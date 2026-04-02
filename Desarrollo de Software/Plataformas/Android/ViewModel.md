#development #android

ViewModel almacena y gestiona datos de UI de forma lifecycle-aware.

## ViewModel Basic

```kotlin
class MiViewModel : ViewModel() {
    private val _contador = MutableLiveData(0)
    val contador: LiveData<Int> = _contador

    fun incrementar() {
        _contador.value = (_contador.value ?: 0) + 1
    }
}
```

## ViewModel con Repository

```kotlin
class UsuarioViewModel(
    private val repositorio: UsuarioRepositorio
) : ViewModel() {

    private val _usuarios = MutableLiveData<List<Usuario>>()
    val usuarios: LiveData<List<Usuario>> = _usuarios

    private val _cargando = MutableLiveData(false)
    val cargando: LiveData<Boolean> = _cargando

    fun cargarUsuarios() {
        viewModelScope.launch {
            _cargando.value = true
            try {
                _usuarios.value = repositorio.getUsuarios()
            } finally {
                _cargando.value = false
            }
        }
    }
}
```

## Factory para ViewModel con dependencias

```kotlin
class UsuarioViewModelFactory(
    private val repositorio: UsuarioRepositorio
) : ViewModelProvider.Factory {
    override fun <T : ViewModel> create(modelClass: Class<T>): T {
        if (modelClass.isAssignableFrom(UsuarioViewModel::class.java)) {
            @Suppress("UNCHECKED_CAST")
            return UsuarioViewModel(repositorio) as T
        }
        throw IllegalArgumentException("Unknown ViewModel class")
    }
}

// Uso
val viewModel: UsuarioViewModel by viewModels {
    UsuarioViewModelFactory(repositorio)
}
```

## SavedStateHandle

```kotlin
class MiViewModel(
    private val savedStateHandle: SavedStateHandle
) : ViewModel() {

    // Persistir datos a través de process death
    var dato: String?
        get() = savedStateHandle["clave"]
        set(value) { savedStateHandle["clave"] = value }
}
```

## Scopes

```kotlin
// viewModelScope (ViewModel)
class MiViewModel : ViewModel() {
    init {
        viewModelScope.launch {
            // Se cancela cuando ViewModel se destruye
        }
    }
}

// rememberCoroutineScope (Composable)
@Composable
fun MiPantalla() {
    val scope = rememberCoroutineScope()

    Button(onClick = {
        scope.launch {
            // Se cancela cuando Composable se elimina
        }
    }) {}
}
```

## ViewModel vs onSaveInstanceState

| ViewModel | onSaveInstanceState |
|-----------|---------------------|
| Guarda objetos complejos | Solo tipos primitivos |
| Persiste en config change | Solo en onStop |
| Se recrea en process death | Se сохраняет |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
