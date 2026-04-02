#development #kotlin

Kotlin ofrece una sintaxis concisa para clases y POO.

## Definir Clase

```kotlin
// Clase básica
class Persona(val nombre: String, var edad: Int) {
    fun saludar(): String = "Hola, soy $nombre"
}

// Con constructor secundario
class Persona {
    var nombre: String = ""
    var edad: Int = 0

    constructor(nombre: String, edad: Int) {
        this.nombre = nombre
        this.edad = edad
    }
}
```

## Data Classes

```kotlin
// Data class (auto-genera equals, hashCode, toString, copy)
data class Usuario(val nombre: String, val email: String)

val usuario =Usuario("Juan", "juan@email.com")
val copia = usuario.copy(nombre = "Pedro")
```

## Herencia

```kotlin
open class Persona(val nombre: String) {
    open fun saludar(): String = "Hola, soy $nombre"
}

class Desarrollador(nombre: String, val lenguaje: String) : Persona(nombre) {
    override fun saludar(): String = "${super.saludar()} y programo en $lenguaje"
}

val dev = Desarrollador("Juan", "Kotlin")
```

## Object (Singleton)

```kotlin
object Configuracion {
    val apiUrl = "https://api.ejemplo.com"
    val timeout = 30
}
Configuracion.apiUrl
```

## Interfaces

```kotlin
interface Saludador {
    fun saludar(): String
}

class PersonaSaludable(val nombre: String) : Saludador {
    override fun saludar(): String = "Hola, soy $nombre"
}
```

## Sealed Classes

```kotlin
sealed class Resultado {
    data class Success(val data: String) : Resultado()
    data class Error(val mensaje: String) : Resultado()
    object Loading : Resultado()
}

fun handle(result: Resultado) = when (result) {
    is Resultado.Success -> println(result.data)
    is Resultado.Error -> println(result.mensaje)
    is Resultado.Loading -> println("Cargando...")
}
```

## Propiedades

```kotlin
class Circulo {
    var radio: Double = 0.0
    
    val diametro: Double
        get() = radio * 2
    
    var area: Double
        get() = Math.PI * radio * radio
        set(value) {
            radio = Math.sqrt(value / Math.PI)
        }
}
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
