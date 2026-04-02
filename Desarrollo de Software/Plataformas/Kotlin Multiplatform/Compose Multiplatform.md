#development #kotlin #multiplatform

Compose Multiplatform permite crear interfaces de usuario que funcionan en Android, iOS, Web y Desktop.

## Setup

```kotlin
// build.gradle.kts (root)
plugins {
    kotlin("multiplatform") version "1.9.20"
    kotlin("plugin.compose") version "1.9.20"
}

// build.gradle.kts del módulo
kotlin {
    sourceSets {
        val commonMain by getting {
            dependencies {
                implementation(compose.runtime)
                implementation(compose.foundation)
                implementation(compose.material3)
                @OptIn(ExperimentalComposeUiApi::class)
                implementation(compose.ui)
                implementation(compose.components.resources)
            }
        }
    }
}

compose {
    // enabled = false para web si hay problemas
    // compilerExtensionVersion = "1.5.4"
}
```

## UI Común

```kotlin
import androidx.compose.material3.*
import androidx.compose.runtime.*

@Composable
fun App() {
    var texto by mutableStateOf("")

    MaterialTheme {
        Column(
            modifier = Modifier.fillMaxSize(),
            verticalArrangement = Arrangement.Center,
            horizontalAlignment = Alignment.CenterHorizontally
        ) {
            Text(
                text = "Hola Kotlin Multiplatform",
                style = MaterialTheme.typography.headlineMedium
            )
            
            OutlinedTextField(
                value = texto,
                onValueChange = { texto = it },
                label = { Text("Ingresa texto") }
            )
            
            Button(onClick = { /* acción */ }) {
                Text("Click")
            }
        }
    }
}
```

## Componentes por Plataforma

```kotlin
@Composable
expect fun MostrarDialogo()

// androidMain
@Composable
actual fun MostrarDialogo() {
    AlertDialog(
        onDismissRequest = { },
        title = { Text("Android Dialog") },
        text = { Text("Contenido específico de Android") },
        confirmButton = { }
    )
}

// desktopMain
@Composable
actual fun MostrarDialogo() {
    // Diálogo nativo de Desktop o Compose for Desktop
    androidx.compose.ui.window.Dialog(onCloseRequest = { }) {
        Text("Desktop Dialog")
    }
}
```

## Navigation

```kotlin
// Common Navigation
@Composable
fun AppNavigation() {
    val navController = rememberNavController()

    NavHost(navController, startDestination = "home") {
        composable("home") {
            HomeScreen(navController)
        }
        composable("detail/{id}") { backStackEntry ->
            val id = backStackEntry.arguments?.getString("id")
            DetailScreen(id)
        }
    }
}
```

## Recursos

```kotlin
// commonMain/resources
// Los recursos se comparten automáticamente
// drawable, values, strings, etc.

// Uso
Image(
    painter = painterResource("drawable/logo.png"),
    contentDescription = "Logo"
)

// Strings
Text(stringResource(R.string.app_name))
```

## Diferencias por Plataforma

| Componente | Android | iOS | Desktop | Web |
|------------|---------|-----|---------|-----|
| Dialog | AlertDialog | AlertDialog | Dialog | alert() |
| Image | Image | Image | Image | img |
| Scroll | ScrollableColumn | ScrollView | ScrollableColumn | overflow |
| Window | Activity | UIViewController | Window | Canvas/HTML |

## Ejemplo Completo

```kotlin
// Main.kt (common)
@Composable
fun MainView() {
    MaterialTheme {
        Surface(
            modifier = Modifier.fillMaxSize(),
            color = MaterialTheme.colorScheme.background
        ) {
            Column(
                modifier = Modifier.padding(16.dp)
            ) {
                Text("Mi App Multiplataforma")
                
                Spacer(modifier = Modifier.height(8.dp))
                
                Button(onClick = { }) {
                    Text("Presionar")
                }
            }
        }
    }
}
```

## Estado y ViewModel

```kotlin
class MyViewModel : ViewModel() {
    private val _state = MutableStateFlow(State())
    val state: StateFlow<State> = _state
}

@Composable
fun Screen(viewModel: MyViewModel) {
    val state by viewModel.state.collectAsState()
    
    if (state.isLoading) {
        CircularProgressIndicator()
    }
}
```

[[Desarrollo de Software/Plataformas/Kotlin Multiplatform/Kotlin Multiplatform.md]]
