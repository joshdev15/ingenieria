#architecture #design-patterns #gof #creational #singleton #go #kotlin

# Patrón de Diseño: Singleton (Instancia Única)

El patrón **Singleton** es un patrón de diseño **creacional** del catálogo clásico *Gang of Four (GoF)*. Su objetivo es **garantizar que una clase tenga únicamente una sola instancia en toda la aplicación y proporcionar un punto de acceso global a dicha instancia**.

---

## Índice

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|<- Volver a Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Factory Method.md|Ver Patrón Factory Method]]
- [[Diseño y Arquitectura/Patrones de Diseño/Patrones de Diseño - Catálogo GoF.md|Ver Catálogo de Patrones de Diseño]]

---

## El Problema que Resuelve

En muchas aplicaciones existen recursos del sistema que deben compartirse y coordinarse desde una única fuente para evitar colisiones, corrupción de estado o desperdicio de memoria:
- Un gestor de conexiones a base de datos (*Connection Pool*).
- Un cliente de configuración global (`AppConfig`).
- Un sistema de registro de auditoría o logging (`Logger`).
- Una caché en memoria local.

Si cada componente creara su propia instancia de estos servicios, se agotarían conexiones, se perdería sincronización y se multiplicarían los hilos innecesariamente.

---

## Estructura del Patrón

```
┌──────────────────────────────────────┐
│              Singleton               │
├──────────────────────────────────────┤
│ - instance: Singleton {static}       │
├──────────────────────────────────────┤
│ - Singleton() {private}              │
│ + getInstance(): Singleton {static}  │
│ + operacionNegocio(): void           │
└──────────────────────────────────────┘
```

1. **Constructor Privado**: Impide que otros objetos utilicen el operador `new` o instanciación directa.
2. **Campo Estático Privado**: Almacena la única instancia creada.
3. **Método Estático Público (`getInstance`)**: Sirve como punto de entrada global. Si la instancia no existe, la crea (*Lazy Initialization*); si ya existe, devuelve la existente.

---

## Implementación Segura para Concurrencia (*Thread-Safe*)

En aplicaciones multihilo modernas, el mayor desafío de Singleton es evitar que dos hilos creen dos instancias simultáneas (*Race Condition*).

### Implementación en Go (Uso de `sync.Once`)

En Go, la forma idiomática y atómica de implementar Singleton sin bloqueos lentos es mediante `sync.Once`:

```go
package database

import (
    "sync"
)

type DatabaseConnection struct {
    Host string
}

var (
    instance *DatabaseConnection
    once     sync.Once
)

// ObtenerInstancia garantiza inicialización perezosa y segura en concurrencia
func ObtenerInstancia() *DatabaseConnection {
    once.Do(func() {
        // Este bloque solo se ejecuta exactamente una vez en toda la vida del programa
        instance = &DatabaseConnection{
            Host: "postgres://localhost:5432/estudio",
        }
    })
    return instance
}
```

---

### Implementación en Kotlin

Kotlin provee soporte nativo para Singleton a nivel de lenguaje con la palabra clave `object`:

#### 1. Idiomático con `object` (Eager / Thread-Safe nativo de JVM)
```kotlin
object DatabaseManager {
    val host: String = "localhost:5432"

    fun conectar() {
        println("Conectado a la base de datos única en $host")
    }
}

// Uso directo
DatabaseManager.conectar()
```

#### 2. Lazy con Parámetros (Double-Checked Locking)
```kotlin
class ApiClient private constructor(val apiKey: String) {

    companion object {
        @Volatile
        private var INSTANCIA: ApiClient? = null

        fun obtenerInstancia(apiKey: String): ApiClient {
            return INSTANCIA ?: synchronized(this) {
                INSTANCIA ?: ApiClient(apiKey).also { INSTANCIA = it }
            }
        }
    }
}
```

---

## Ventajas y Desventajas

| Ventajas | Desventajas |
| :--- | :--- |
| **Instancia Única Garantizada**: Control estricto de acceso a recursos compartidos. | **Dificultad para Testing (Mocking)**: Al ser estático, es complejo sustituirlo por dobles de prueba (*mocks*) en tests unitarios. |
| **Inicialización Perezosa (*Lazy*)**: Se crea únicamente cuando se solicita por primera vez, ahorrando recursos. | **Acoplamiento Global Oculto**: Los componentes que lo usan acceden a una variable global encubierta, violando la Inversión de Dependencias (DIP). |
| **Punto de Acceso Centralizado**: Fácil de invocar desde cualquier módulo. | **Violación de Responsabilidad Única (SRP)**: Resuelve su problema de negocio y al mismo tiempo controla su propio ciclo de vida. |

> [!TIP] Singleton vs. Inyección de Dependencias (DI)
> En arquitecturas modernas (Spring, Hilt, Google Wire), la mejor práctica es **definir la clase de forma normal y delegar la unicidad de la instancia al Contenedor de Inyección de Dependencias con alcance `@Singleton`**. Esto mantiene la ventaja de una sola instancia sin perder la capacidad de testear mediante mocks.

---

## Referencias y Enlaces

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|Índice de Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Factory Method.md|Patrón Factory Method]]
- [[Diseño y Arquitectura/Patrones de Diseño/Patrones de Diseño - Catálogo GoF.md|Catálogo General de Patrones de Diseño]]
- GoF (Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides): *Design Patterns: Elements of Reusable Object-Oriented Software (1994).*
