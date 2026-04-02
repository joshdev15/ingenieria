#architecture #design-patterns

Los patrones de diseño son soluciones reutilizables a problemas comunes en el diseño de software.

## Categorías

### 1. Patrones Creacionales
解决 la creación de objetos de forma controlada.

| Patrón | Descripción |
|--------|-------------|
| **Singleton** | Una única instancia de una clase |
| **Factory Method** | Interfaz para crear objetos, subclases决定 qué clase instanciar |
| **Abstract Factory** | Interfaz para crear familias de objetos relacionados |
| **Builder** | Construcción paso a paso de objetos complejos |
| **Prototype** | Crear nuevos objetos clonando un prototipo |

### 2. Patrones Estructurales
Definen cómo organizar clases y objetos.

| Patrón | Descripción |
|--------|-------------|
| **Adapter** | Convertir interfaz de una clase en otra interfaz |
| **Decorator** | Añadir funcionalidades dinámicamente |
| **Facade** | Interfaz unificada para subsistemas complejos |
| **Proxy** | Sustituto o placeholder de otro objeto |
| **Composite** | Tratar objetos individuales y compuestos uniformemente |

### 3. Patrones de Comportamiento
Definen la comunicación entre objetos.

| Patrón | Descripción |
|--------|-------------|
| **Observer** | Suscriptor-notificador, uno a muchos |
| **Strategy** | Intercambiar algoritmos dinámicamente |
| **Command** | Encapsular solicitud como objeto |
| **Iterator** | Recorrer colección sin exponer su estructura |
| **State** | Cambiar comportamiento según el estado |
| **Template Method** | Definir esqueleto de algoritmo, subclasses决定 pasos |

## Ejemplo: Singleton (Go)

```go
package main

import "sync"

type DatabaseConnection struct {
    host string
}

var (
    instance *DatabaseConnection
    once     sync.Once
)

func GetDatabaseConnection() *DatabaseConnection {
    once.Do(func() {
        instance = &DatabaseConnection{host: "localhost"}
    })
    return instance
}

func main() {
    db1 := GetDatabaseConnection()
    db2 := GetDatabaseConnection()
    println(db1 == db2) // true
}
```

## Ejemplo: Observer (Kotlin)

```kotlin
interface Observer {
    fun update(data: String)
}

class Subject {
    private val observers = mutableListOf<Observer>()
    
    fun attach(observer: Observer) {
        observers.add(observer)
    }
    
    fun notify(data: String) {
        observers.forEach { it.update(data) }
    }
}

class ConcreteObserver : Observer {
    override fun update(data: String) {
        println("Recibido: $data")
    }
}

fun main() {
    val subject = Subject()
    subject.attach(ConcreteObserver())
    subject.notify("Hola mundo")
}
```

## Cuándo Usar Patrones

- **Sí**: Problemas recurrentes, equipos grandes, código mantenible
- **No**: Sobreingeniería, proyectos pequeños, código complejo innecesario

[[Ingeniería/Arquitectura de Software/Arquitectura de Software.md]]