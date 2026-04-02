#development #kotlin

Las funciones en Kotlin son ciudadano de primera clase.

## Declaración

```kotlin
// Función básica
fun saludar(nombre: String): String {
    return "Hola, $nombre!"
}

// Función de expresión única
fun saludar(nombre: String) = "Hola, $nombre!"

// Función con cuerpo de bloque
fun saludar(nombre: String): String {
    return "Hola, $nombre!"
}
```

## Parámetros

```kotlin
// Parámetros por defecto
fun greet(nombre: String = "Usuario") = "Hola, $nombre"

// Named parameters
fun crearUsuario(nombre: String, edad: Int, activo: Boolean = true) {}
crearUsuario(nombre = "Juan", edad = 25)

// Vararg
fun sum(vararg numbers: Int): Int {
    return numbers.sum()
}
```

## Lambdas

```kotlin
// Lambda básica
val duplicar = { x: Int -> x * 2 }

// Lambda en funciones de orden superior
val nums = listOf(1, 2, 3, 4)
val doubled = nums.map { it * 2 }

// Filter
val pares = nums.filter { it % 2 == 0 }

// Reduce
val suma = nums.reduce { acc, i -> acc + i }
```

## Extension Functions

```kotlin
fun String.saludar(): String {
    return "Hola, $this!"
}

"Juan".saludar()  // "Hola, Juan!"
```

## Funciones de Orden Superior

```kotlin
// Función como parámetro
fun operar(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}

val suma = operar(5, 3) { a, b -> a + b }

// Función que retorna función
fun crearMultiplier(factor: Int): (Int) -> Int {
    return { x -> x * factor }
}
```

## Coroutines (async)

```kotlin
import kotlinx.coroutines.*

suspend fun fetchData(): String {
    delay(1000)
    return "Datos"
}

fun main() = runBlocking {
    val result = async { fetchData() }.await()
    println(result)
}
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
