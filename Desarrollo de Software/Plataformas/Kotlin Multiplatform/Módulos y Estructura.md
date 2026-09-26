#development #kotlin #multiplatform

La estructura de módulos en KMP organiza el código compartido y específico por plataforma.

## Estructura de Carpetas

```
mi-proyecto/
├── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
├── src/
│   ├── commonMain/
│   │   └── kotlin/
│   │       └── com/
│   │           └── ejemplo/
│   │               └── App.kt
│   ├── commonTest/
│   ├── androidMain/
│   │   └── kotlin/
│   │       └── com/
│   │           └── ejemplo/
│   │               └── Platform.kt
│   ├── iosMain/
│   │   └── kotlin/
│   │       └── com/
│   │           └── ejemplo/
│   │               └── Platform.kt
│   ├── jvmMain/
│   ├── jsMain/
│   └── desktopMain/
├── androidApp/
│   └── src/
├── iosApp/
└── webApp/
```

## Módulo Compartido (shared)

```
shared/
├── build.gradle.kts
├── src/
│   ├── commonMain/kotlin/
│   │   └── com/app/shared/
│   │       ├── Greeting.kt
│   │       ├── api/
│   │       │   └── HttpClient.kt
│   │       └── model/
│   │           └── User.kt
│   ├── androidMain/kotlin/
│   │   └── com/app/shared/
│   │       └── Platform.kt
│   ├── iosMain/kotlin/
│   │   └── com/app/shared/
│   │       └── Platform.kt
│   └── iosArm64Main/
│       └── kotlin/
│           └── Platform.kt
```

## Módulos de Aplicación

```kotlin
// androidApp/build.gradle.kts
plugins {
    kotlin("android")
}

android {
    defaultConfig {
        applicationId = "com.ejemplo.android"
        minSdk = 24
    }
}

dependencies {
    implementation(project(":shared"))
}

// iosApp/build.gradle.kts
plugins {
    kotlin("native.cocoapods")
}

ios {
    deploymentTarget = "13.0"
}

dependencies {
    implementation(project(":shared"))
}
```

## Organizar por característica

```
shared/
└── src/
    └── commonMain/kotlin/
        └── com/
            ejemplo/
                └── app/
                    ├── domain/
                    │   ├── model/
                    │   ├── repository/
                    │   └── usecase/
                    ├── data/
                    │   ├── repository/
                    │   └── api/
                    └── presentation/
                        └── viewmodel/
```

## Conexión entre Módulos

```kotlin
// androidApp - usar el módulo compartido
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        val greeting = Greeting().greeting()
        // "Hello, iOS/Android/JVM/etc"
    }
}
```

## Gradle Properties

```properties
# gradle.properties
kotlin.mpp.enabled=true
kotlin.native.ignoreDisabledTargets=true
org.gradle.jvmargs=-Xmx4096m
```

[[Desarrollo de Software/Plataformas/Kotlin Multiplatform/Kotlin Multiplatform.md|<- Volver a Kotlin Multiplatform]]
