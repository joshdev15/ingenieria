#development #kotlin

Ejemplo básico de "Hola Mundo" en Kotlin.

## Función Main

```kotlin
// Forma más simple
fun main() {
    println("Hola mundo!")
}

// Con argumentos
fun main(args: Array<String>) {
    println("Hola mundo!")
}

// Expression body
fun main() = println("Hola mundo!")
```

## Análisis del Código

| Línea | Descripción |
|-------|-------------|
| `fun main()` | Función principal punto de entrada |
| `println()` | Imprime texto con salto de línea |
| `print()` | Imprime sin salto de línea |

## En IntelliJ IDEA

1. File > New > Project
2. Seleccionar Kotlin/JVM
3. New Kotlin File
4. Escribir el código y ejecutar

## En Android Studio

```kotlin
// MainActivity.kt
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        println("Hola mundo!")
    }
}
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
