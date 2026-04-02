#development #android

Las coroutines son la forma recomendada de manejar operaciones asíncronas en Android.

## Conceptos Básicos

- **Ligeras**: Miles de coroutines en un hilo
- **Integradas con Kotlin**: Sintaxis nativa
- **Cancelables**: Soporte para cancelar operaciones

## Funciones Suspend

```kotlin
suspend fun obtenerDatos(): String {
    delay(1000)  // Simula operación larga
    return "Datos obtenidos"
}
```

## Scope

```kotlin
// ViewModelScope (recomendado en ViewModel)
class MiViewModel : ViewModel() {
    fun cargarDatos() {
        viewModelScope.launch {
            val datos = obtenerDatos()
        }
    }
}

// LifecycleScope
class MiActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        lifecycleScope.launch {
            // Código async
        }
    }
}
```

## launch vs async

```kotlin
viewModelScope.launch {
    // fire and forget
    operacion1()
    operacion2()
}

viewModelScope.launch {
    // retorna resultado
    val resultado = async { obtenerDatos() }.await()
}
```

## Dispatchers

```kotlin
viewModelScope.launch(Dispatchers.Main) {
    // UI thread
}

viewModelScope.launch(Dispatchers.IO) {
    // Para operaciones I/O (red, BD)
}

viewModelScope.launch(Dispatchers.Default) {
    // CPU intensivo
}

viewModelScope.launch(Dispatchers.Unconfined) {
    // Continúa en el hilo que llamó
}
```

## withContext

```kotlin
suspend fun getData(): Data {
    return withContext(Dispatchers.IO) {
        // Se ejecuta en IO
        api.getData()
    }
}
```

## Cancelación

```kotlin
val job = viewModelScope.launch {
    try {
        while (isActive) {
            // Trabajo
            delay(100)
        }
    } catch (e: CancellationException) {
        // Limpieza
    }
}

// Cancelar
job.cancel()
```

## Coroutine Builders

| Builder | Descripción |
|---------|-------------|
| `launch` | Crea coroutine sin retorno |
| `async` | Crea coroutine con retorno |
| `runBlocking` | Bloquea el hilo actual |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
