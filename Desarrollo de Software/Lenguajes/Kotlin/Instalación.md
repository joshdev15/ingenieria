#development #kotlin

Kotlin puede instalarse de varias formas según el entorno de desarrollo.

## Instalación en IntelliJ IDEA

1. Descargar IntelliJ IDEA desde [jetbrains.com](https://www.jetbrains.com/idea/download/)
2. Instalar y abrir el IDE
3. Ir a **File > Settings > Plugins**
4. Buscar "Kotlin" e instalar
5. Restart el IDE

## Instalación en Android Studio

1. Android Studio ya incluye Kotlin por defecto
2. Para verificar: **File > Settings > Plugins** > buscar "Kotlin"

## Instalación独立性

### Via SDKMAN (Linux/Mac)
```bash
sdk install kotlin
```

### Via Homebrew (Mac)
```bash
brew install kotlin
```

### Manual (Windows)
1. Descargar desde [github.com/JetBrains/kotlin/releases](https://github.com/JetBrains/kotlin/releases)
2. Extraer y agregar a PATH

## Compilador Kotlin (kotlinc)

```bash
# Ver instalación
kotlin -version

# Compilar archivo
kotlinc Main.kt -include-runtime -d app.jar

# Ejecutar
kotlin app.jar
```

## Herramientas de Build

| Herramienta | Comando |
|------------|---------|
| Gradle | `./gradlew build` |
| Maven | `mvn compile` |

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
