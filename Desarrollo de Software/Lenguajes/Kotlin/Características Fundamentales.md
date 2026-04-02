#development #kotlin

Kotlin es un lenguaje moderno con características avanzadas.

## Características Generales

| Característica | Descripción |
|----------------|-------------|
| **Conciso** | Reduce boilerplate significativamente |
| **Interoperable** | 100% compatible con Java |
| **Nulidad segura** | Elimina NullPointerException |
| **Funcional** | Lambda expressions, extension functions |
| **Multiplataforma** | JVM, JS, Native, Android |

## Características Técnicas

- **Tipos Estáticos**: Lenguaje fuertemente tipado
- **Inferencia de tipos**: El compilador infiere el tipo
- **Coroutines**: Asincronía ligera integrada
- **Smart casts**: Conversiones automáticas

## Comparación con Java

```kotlin
// Java - requiere ;
// public class Main {
//     public static void main(String[] args) {
//         System.out.println("Hola");
//     }
// }

// Kotlin - conciso
fun main() = println("Hola")

// Data class vs Java POJO
data class Usuario(val nombre: String, val email: String)
// Equivalente a: constructor, equals, hashCode, toString, copy
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
