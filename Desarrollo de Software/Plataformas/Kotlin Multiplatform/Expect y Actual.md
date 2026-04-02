#development #kotlin #multiplatform

#development #kotlin #multiplatform

expect/actual permite definir declaraciones en código común e implementarlas por plataforma.

## Concepto

- **expect**: Declaración en código compartido
- **actual**: Implementación específica por plataforma

## Ejemplo Básico

```kotlin
// commonMain - expect
expect class Platform {
    val name: String
}

// androidMain - actual
actual class Platform {
    actual val name: String = "Android"
}

// iosMain - actual
actual class Platform {
    actual val name: String = "iOS"
}

// desktopMain - actual  
actual class Platform {
    actual val name: String = "Desktop"
}
```

## expect con funciones

```kotlin
// commonMain
expect fun getPlatformName(): String

// androidMain
actual fun getPlatformName(): String = "Android"

// iosMain
actual fun getPlatformName(): String = "iOS"
```

## expect con clases

```kotlin
// commonMain
expect class DateTime(timestamp: Long) {
    fun toUnix(): Long
    fun format(): String
}

// androidMain
actual class DateTime actual constructor(private val timestamp: Long) {
    actual fun toUnix(): Long = timestamp / 1000
    actual fun format(): String = java.text.SimpleDateFormat().format(Date(timestamp))
}
```

## Múltiples actual en misma plataforma

```kotlin
// En androidMain puedes tener varios archivos con actual
// DateTime.kt
actual class DateTime ...

// Platform.kt  
actual class Platform ...
```

## Errores Comunes

| Error | Solución |
|-------|----------|
| expect sin actual | Crear archivo en carpeta de plataforma |
| firma no coincide | Verificar que parameters y return type coincidan |
| Missing "actual" | Agregar modifier actual a la implementación |

## Good Practices

- Usar para APIs nativas específicas
- Mantener lógica de negocio en common
- Documentar el comportamiento esperado

[[Desarrollo de Software/Plataformas/Kotlin Multiplatform/Kotlin Multiplatform.md]]
