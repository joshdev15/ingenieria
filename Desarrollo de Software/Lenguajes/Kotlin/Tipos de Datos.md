#development #kotlin

Kotlin es un lenguaje fuertemente tipado con sintaxis amigable.

## Tipos de Datos

### Primitivos
```kotlin
val entero: Int = 0
val largo: Long = 7_000_000_000
val pi: Double = 3.141592653589793
val gravedad: Float = 9.8f
val byte: Byte = 1
val short: Short = 2024
val letra: Char = 'a'
val palabra: String = "hola"
val booleano: Boolean = true
```

### Colecciones
```kotlin
// Arrays
val array: Array<Int> = arrayOf(1, 2, 3, 4, 5)

// Listas
val lista: List<Int> = listOf(1, 2, 3, 4, 5)

// Sets
val vocales: Set<Char> = setOf('a', 'e', 'i', 'o', 'u')

// Maps
val mapa: Map<Int, String> = mapOf(
    1 to "uno",
    2 to "dos",
    3 to "tres"
)
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]