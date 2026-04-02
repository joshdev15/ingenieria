#development #android

Jetpack Compose es el toolkit moderno de UI para construir interfaces nativas en Android.

## Conceptos Básicos

```kotlin
@Composable
fun MiPantalla() {
    Text("Hola Mundo")
}
```

## Funciones @Composable

- Todo elemento UI es una función @Composable
- Son funciones que describen la UI
- Se recomputan cuando cambia el estado

## Estado en Compose

```kotlin
@Composable
fun Contador() {
    var contador by remember { mutableStateOf(0) }

    Column {
        Text("Contador: $contador")
        Button(onClick = { contador++ }) {
            Text("Incrementar")
        }
    }
}
```

## Layouts

### Column (vertical)
```kotlin
Column(
    modifier = Modifier.fillMaxSize(),
    verticalArrangement = Arrangement.Center,
    horizontalAlignment = Alignment.CenterHorizontally
) {
    Text("Título")
    Button(onClick = { }) {
        Text("Click")
    }
}
```

### Row (horizontal)
```kotlin
Row(
    modifier = Modifier.fillMaxWidth(),
    horizontalArrangement = Arrangement.SpaceBetween
) {
    Text("Izquierda")
    Text("Derecha")
}
```

### Box (apilar)
```kotlin
Box(
    modifier = Modifier.fillMaxSize(),
    contentAlignment = Alignment.Center
) {
    Text("Centrado")
}
```

## Modifier

```kotlin
Text(
    text = "Estilizado",
    modifier = Modifier
        .padding(16.dp)
        .background(Color.Blue)
        .clickable { }
)
```

## Material Design

```kotlin
import androidx.compose.material3.*

Scaffold(
    topBar = {
        TopAppBar(title = { Text("Mi App") })
    }
) { padding ->
    Column(modifier = Modifier.padding(padding)) {
        Text("Contenido")
    }
}
```

## Preview

```kotlin
@Preview
@Composable
fun PreviewMiPantalla() {
    MiPantalla()
}
```

## Estado con ViewModel

```kotlin
// ViewModel
class MiViewModel : ViewModel() {
    val estado by mutableStateOf(UiState())
}

data class UiState(
    val cargando: Boolean = false,
    val datos: List<String> = emptyList()
)

// Composable
@Composable
fun Pantalla(viewModel: MiViewModel) {
    val estado = viewModel.estado.collectAsState()

    if (estado.cargando) {
        CircularProgressIndicator()
    }
}
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
