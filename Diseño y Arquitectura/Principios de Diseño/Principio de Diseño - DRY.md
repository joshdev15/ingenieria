#architecture #design-principles #dry #clean-code #refactoring #pragmatic-programmer #interview-prep #go #kotlin

# Principio de Diseño: DRY (Don't Repeat Yourself)

El principio **DRY (Don't Repeat Yourself)** fue formalizado por **Andy Hunt y Dave Thomas** en su célebre libro *The Pragmatic Programmer* (1999). 

Su definición original es:
> *"Every piece of knowledge must have a single, unambiguous, authoritative representation within a system."*  
> *(Cada pieza de conocimiento debe tener una representación única, inequívoca y autoritativa dentro de un sistema).*

Aunque popularmente se reduce a *"no copies y pegues código"*, el principio DRY va mucho más allá de la sintaxis: se enfoca en **evitar la duplicación de conocimiento de negocio y lógica de decisión**.

---

## Índice

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|<- Volver a Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Principios de Diseño/Principios de Diseño.md|<- Hub de Principios de Diseño]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - SOLID.md|Ver SOLID]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - KISS.md|Ver KISS]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - YAGNI.md|Ver YAGNI]]

---

## El Núcleo de DRY: Duplicación de Conocimiento vs. Duplicación Accidental

Uno de los errores más comunes de ingenieros junior es asumir que si dos bloques de código tienen las mismas 4 líneas, deben extraerse inmediatamente en una función común. Esto suele provocar **abstracciones prematuras dañinas**.

| Tipo de Duplicación | Definición | Acción Recomendada |
| :--- | :--- | :--- |
| **Duplicación Esencial (De Conocimiento)** | Dos partes del sistema calculan la misma regla fiscal o validan el mismo formato legal de documento. Si la ley cambia, ambos deben cambiar al unísono. | **Aplicar DRY**: Centralizar en una única función, servicio o *Value Object*. |
| **Duplicación Accidental (Incidental)** | Dos flujos distintos (ej. registro de clientes y alta de proveedores) tienen casualmente los mismos 3 campos y validaciones similares hoy, pero pertenecen a dominios distintos y cambiarán por razones diferentes. | **No aplicar DRY**: Mantenerlos separados para evitar acoplar dos contextos de negocio independientes. |

> [!WARNING] Cita Célebre de Sandi Metz
> *"Duplication is far cheaper than the wrong abstraction."*  
> *(La duplicación es mucho más barata que la abstracción equivocada).*

---

## El Antipatrón del "Exceso de DRY" y Alternativas

Cuando se fuerza DRY ciegamente sobre código que no comparte el mismo ciclo de vida, se generan monstruos acoplados llenos de parámetros booleanos: `calcular(datos, esCliente = true, esProveedor = false, aplicarDescuentoEspecial = false)`.

Para combatir esto surgieron principios complementarios:
1. **WET (Write Everything Twice / Waste Everyone's Time)**: Permítete duplicar una vez. Si lo escribes por segunda vez, toléralo; solo a la tercera vez (*Rule of Three*) abstrae.
2. **AHA (Avoid Hasty Abstractions)** de Kent C. Dodds: Prefiere duplicar antes de apresurarte a crear una abstracción rígida que luego sea una pesadilla de mantener.
3. **Rule of Three (Regla de Tres)** de Martin Fowler:
   - La primera vez que haces algo, simplemente escríbelo.
   - La segunda vez que haces algo similar, traga saliva y duplícalo.
   - La tercera vez que haces algo idéntico, es momento de refactorizar y abstraer.

---

## Ejemplo Práctico: Buen DRY vs. Mal DRY

### 1. Buen DRY: Centralizar Reglas de Negocio en Go
Imagina el cálculo de impuestos y redondeo contable:

```go
package main

import (
    "fmt"
    "math"
)

// BUEN DRY: Centralizamos la regla impositiva en una sola fuente de verdad (SSOT)
type CalculadoraFiscal struct {
    tasaIVA float64
}

func NuevaCalculadoraFiscal(tasa float64) *CalculadoraFiscal {
    return &CalculadoraFiscal{tasaIVA: tasa}
}

func (c *CalculadoraFiscal) CalcularTotalConIVA(subtotal float64) float64 {
    // Regla de redondeo financiero estricta a 2 decimales
    totalBruto := subtotal * (1.0 + c.tasaIVA)
    return math.Round(totalBruto*100) / 100
}

func main() {
    fiscal := NuevaCalculadoraFiscal(0.19) // 19% IVA
    fmt.Printf("Total Factura A: $%.2f\n", fiscal.CalcularTotalConIVA(100.555))
    fmt.Printf("Total Factura B: $%.2f\n", fiscal.CalcularTotalConIVA(250.00))
}
```
*Si la tasa o la regla de redondeo cambia por disposición gubernamental, se edita en un único punto del sistema.*

---

### 2. Mal DRY: Abstracción Prematura Acoplada en Kotlin

```kotlin
// ANTIPATRÓN: Unificar DTOs de dominios distintos solo porque se parecen hoy
// Esto acopla el módulo de Facturación con el de Envíos
data class PersonaGenericaDTO(
    val id: String,
    val nombre: String,
    val direccion: String,
    val esCliente: Boolean,      // bandera para el módulo de billing
    val codigoRutaEnvio: String? // bandera para el módulo de logística
)

// MEJOR DISEÑO (Respetando límites de dominio de DDD):
// Cada contexto tiene su propio modelo, aunque compartan campos sintácticos:
data class ClienteFacturacion(
    val id: String,
    val razonSocial: String,
    val direccionFiscal: String
)

data class DestinatarioLogistica(
    val id: String,
    val nombreReceptor: String,
    val direccionEntrega: String,
    val codigoPostalRuta: String
)
```

---

## Preguntas Frecuentes en Entrevistas Técnicas

### 1. ¿Toda duplicación de código viola el principio DRY?
**No**. La duplicación sintáctica (dos bloques de código que se ven iguales) no necesariamente viola DRY si representan conceptos de dominio diferentes con motivos de cambio independientes. DRY solo se viola cuando hay duplicación de **conocimiento**, es decir, cuando un cambio en un único requisito de negocio obliga a modificar el código en múltiples archivos dispersos.

### 2. ¿Cómo se relaciona DRY con el principio de Fuente Única de Verdad (SSOT)?
DRY es la aplicación a nivel de código y diseño del concepto de **Single Source of Truth (SSOT)**. En bases de datos, la normalización relacional busca DRY para evitar anomalías de actualización. En arquitecturas modernas, esquemas OpenAPI o contratos protobuf actúan como la SSOT que genera clientes y servidores sin duplicar definiciones de datos.

### 3. ¿Qué peligro conlleva ser dogmático con DRY en arquitecturas de Microservicios?
El exceso de celo con DRY en microservicios suele llevar a la creación de una librería compartida (*shared library* o paquete `commons.jar` / `common-go`) con modelos de datos compartidos. Esto introduce un **acoplamiento distribuido**: cuando un servicio necesita cambiar un modelo, rompe o fuerza el despliegue sincronizado de todos los demás servicios, destruyendo la autonomía de los microservicios. En microservicios, **la duplicación controlada es preferible al acoplamiento de librerías**.

---

## Referencias y Enlaces

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|Índice de Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Principios de Diseño/Principios de Diseño.md|Hub de Principios de Diseño]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - SOLID.md|Principio SOLID]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - KISS.md|Principio KISS]]
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - YAGNI.md|Principio YAGNI]]
- Hunt, Andrew, and David Thomas. *The Pragmatic Programmer: From Journeyman to Master.* Addison-Wesley, 1999.
