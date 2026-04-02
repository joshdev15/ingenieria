#development #kotlin

Los paquetes organizan el código en Kotlin.

## Paquetes Estándar

| Paquete | Descripción |
|---------|-------------|
| `kotlin.io` | E/S de archivos |
| `kotlin.math` | Operaciones matemáticas |
| `kotlin.text` | Manipulación de texto |
| `kotlin.collections` | Colecciones |
| `kotlin.coroutines` | Coroutines |

## Declarar Paquete

```kotlin
package com.ejemplo.miproyecto

fun saludar() = "Hola"
```

## Importar

```kotlin
import kotlin.math.PI
import kotlin.random.Random
import com.mipaquete.MiClase
import com.mipaquete.*  // Wildcard
```

## Paquetes por Defecto

| Paquete | Descripción |
|---------|-------------|
| `kotlin` | Funciones básicas |
| `kotlin.io` | Input/Output |
| `kotlin.text` | Strings |
| `kotlin.collections` | Listas, maps, sets |
| `kotlin.coroutines` | Async programming |

## Visibility Modifiers

```kotlin
// público (por defecto)
public class Publico()

// privado al archivo
private class Privado()

// interno al módulo
internal class Interno()
```

## Estructura de Proyecto

```
src/
├── main/
│   └── kotlin/
│       └── com/
│           └── ejemplo/
│               ├── Main.kt
│               └── utils/
│                   └── Utils.kt
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
