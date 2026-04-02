#development #android

Flow es un flujo de datos asíncrono que puede收集 múltiples valores.

## Flows vs LiveData

| Flow | LiveData |
|------|----------|
| cold (por defecto) | hot |
| Cancelable | No cancelable |
| Más flexible | Más simple |
| Kotlin only | Android lifecycle aware |

## Crear Flow

```kotlin
// Flow básico
fun obtenerNumeros(): Flow<Int> = flow {
    for (i in 1..5) {
        delay(100)
        emit(i)
    }
}

// Flow desde suspend function
fun getUsuarios(): Flow<List<Usuario>> = flow {
    emit(api.getUsuarios())
}.flowOn(Dispatchers.IO)
```

## Recoger Flow

```kotlin
// collect en ViewModel
viewModelScope.launch {
    obtenerNumeros().collect { numero ->
        println("Número: $numero")
    }
}

// collectAsState (para Compose)
val numeros by obtenerNumeros().collectAsState(initial = 0)
```

## Flow Operators

```kotlin
// map
val duplicados = flujo.map { it * 2 }

// filter
val pares = flujo.filter { it % 2 == 0 }

// take
val tresPrimeros = flujo.take(3)

// transform
val transformados = flujo.transform { valor ->
    emit("Valor: $valor")
}

// combine
val combinado = flujo1.combine(flujo2) { a, b -> "$a - $b" }
```

## StateFlow

```kotlin
class MiViewModel : ViewModel() {
    private val _estado = MutableStateFlow(UiState())
    val estado: StateFlow<UiState> = _estado

    fun actualizar() {
        _estado.value = UiState(cargando = true)
    }
}

// En Compose
val estado by viewModel.estado.collectAsState()
```

## SharedFlow

```kotlin
class MiViewModel : ViewModel() {
    private val _eventos = MutableSharedFlow<Evento>()
    val eventos: SharedFlow<Evento> = _eventos

    fun enviarEvento() {
        _eventos.emit(Evento("mensaje"))
    }
}
```

## cold vs hot

```kotlin
// cold: no genera valores hasta que se collecting
val coldFlow = flow {
    println("Generando...")
    emit(1)
}

// hot: genera valores aunque nadie escuche
val stateFlow = MutableStateFlow(1)
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
