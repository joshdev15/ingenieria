#development #kotlin #multiplatform

#development #kotlin #multiplatform

La configuración de Gradle en KMP define los módulos y plataformas objetivo.

## Estructura de build.gradle.kts

```kotlin
// build.gradle.kts (root)
plugins {
    kotlin("multiplatform") version "1.9.20" apply false
}

// settings.gradle.kts
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}

dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
    }
}

include(":androidApp", ":shared", ":iosApp", ":webApp")
```

## build.gradle.kts del módulo compartido

```kotlin
plugins {
    kotlin("multiplatform")
}

kotlin {
    jvm {
        withJava()
    }
    
    androidTarget()
    
    iosX64()
    iosArm64()
    iosSimulatorArm64()
    
    js {
        browser {}
        nodejs {}
    }
    
    linuxX64()
    macosX64()
    macosArm64()
    windowsX64()
    
    mingwX64()

    sourceSets {
        val commonMain by getting
        val commonTest by getting {
            dependencies {
                implementation(kotlin("test"))
            }
        }
        
        val jvmMain by getting
        val jvmTest by getting
        
        val androidMain by getting
        val androidTest by getting
        
        val iosMain by getting
        val iosTest by getting
        
        val jsMain by getting
        val jsTest by getting
    }
}
```

## Configuración por Plataforma

```kotlin
kotlin {
    androidTarget {
        compilations.all {
            kotlinOptions {
                jvmTarget = "17"
            }
        }
    }
    
    jvm {
        compilations.all {
            kotlinOptions {
                jvmTarget = "17"
            }
        }
    }
    
    iosX64 {
        // Configuración específica para iOS simulator 64-bit
    }
    
    js {
        browser {
            testTask {
                useKarma {
                    useChromeHeadless()
                }
            }
        }
    }
}
```

## Dependencias por Plataforma

```kotlin
sourceSets {
    commonMain {
        dependencies {
            implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.3")
        }
    }
    
    androidMain {
        dependencies {
            implementation("androidx.core:core-ktx:1.12.0")
        }
    }
    
    iosMain {
        dependencies {
            // Solo dependencias compatibles con iOS
        }
    }
}
```

## Version Catalog (libs.versions.toml)

```toml
[versions]
kotlin = "1.9.20"
coroutines = "1.7.3"

[libraries]
kotlinx-coroutines-core = { group = "org.jetbrains.kotlinx", name = "kotlinx-coroutines-core", version.ref = "coroutines" }

[plugins]
kotlin-multiplatform = { id = "org.jetbrains.kotlin.multiplatform", version.ref = "kotlin" }
```

## Targets Mínimos

| Plataforma | Mínima |
|------------|--------|
| Android | API 21 (Android 5.0) |
| iOS | iOS 13 |
| JVM | Java 8 |
| JS | ES5 |

[[Desarrollo de Software/Plataformas/Kotlin Multiplatform/Kotlin Multiplatform.md]]
