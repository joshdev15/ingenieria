#development #kotlin

Declaración y uso de variables en Kotlin.

## Formas de Declaración

```kotlin
// 1. Solo declaración (no recomendado)
var nombre: String

// 2. Declaración e inicialización
var nombre: String = "Kotlin"

// 3. Inferencia de tipo
var nombre = "Kotlin"

// 4. Inmutable (recomendado)
val nombre = "Kotlin"
```

## Tipos Compuestos

### Arrays
```kotlin
val arr = arrayOf("a", "b", "c")
val arrInt = IntArray(50)
```

### Listas
```kotlin
val lista = listOf(1, 2, 3)        // Inmutable
val listaMut = mutableListOf(1, 2, 3)  // Mutable
```

### Maps
```kotlin
val mapa = mapOf("a" to 1, "b" to 2)
val mapaMut = mutableMapOf("a" to 1)
```

## Data Classes

```kotlin
data class Persona(
    val nombre: String,
    val edad: Int
)

val persona = Persona("Juan", 25)
```

## Interfaces

```kotlin
interface Runner {
    fun run()
}

fun startRunning(r: Runner) {
    r.run()
}
```

## Null Safety

```kotlin
// Nullable (puede ser null)
var nombre: String? = null

// Safe call
println(nombre?.length)

// Elvis operator
val len = nombre?.length ?: 0

// Not null assertion (cuidado!)
val len = nombre!!.length
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
