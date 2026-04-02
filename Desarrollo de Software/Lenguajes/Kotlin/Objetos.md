#development #kotlin

Los objetos en Kotlin son más concisos que en otros lenguajes.

## Crear Objetos

```kotlin
// Literal
val persona = mapOf(
    "nombre" to "Juan",
    "edad" to 30
)

// Data class (recomendado)
data class Persona(val nombre: String, val edad: Int)
val persona = Persona("Juan", 30)

// Clase manual
class Persona {
    var nombre: String = ""
    var edad: Int = 0
}
val persona = Persona().apply {
    nombre = "Juan"
    edad = 30
}
```

## Acceso a Propiedades

```kotlin
data class Persona(val nombre: String, val edad: Int)
val persona = Persona("Juan", 30)

// Acceso directo
println(persona.nombre)

// Destructuring
val (nombre, edad) = persona
```

## mapOf y mutableMapOf

```kotlin
// Inmutable
val mapa = mapOf("a" to 1, "b" to 2)
println(mapa["a"])  // 1
println(mapa.keys)  // [a, b]

// Mutable
val mapaMut = mutableMapOf("a" to 1)
mapaMut["b"] = 2
mapaMut.remove("a")
```

## apply y also

```kotlin
val persona = Persona().apply {
    nombre = "Juan"
    edad = 30
}

val numero = 10.also {
    println("El número es $it")
}
```

## Object Expressions

```kotlin
// Anonymous object
val objeto = object {
    var x = 10
    fun saludar() = "Hola"
}
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
