#development #android

LiveData es un observable lifecycle-aware para Android.

## Conceptos

- **Observable**: Notifica cambios a observers
- **Lifecycle-aware**: Solo actualiza cuando el lifecycle está activo
- **LiveData vs Flow**: LiveData es más simple pero menos flexible

## LiveData Básico

```kotlin
class MiViewModel : ViewModel() {
    val mensaje = MutableLiveData<String>()

    fun actualizarMensaje() {
        mensaje.value = "Nuevo mensaje"
    }
}
```

## Observar en Activity/Fragment

```kotlin
// Con observe (lifecycle owner)
viewModel.mensaje.observe(this) { mensaje ->
    textView.text = mensaje
}

// Con observeForever (sin lifecycle)
viewModel.mensaje.observeForever { mensaje ->
    // Se ejecuta siempre
}
```

## LiveData con Transformations

```kotlin
// map
val nombreMayus = Transformations.map(usuarioLiveData) { usuario ->
    usuario.nombre.uppercase()
}

// switchMap
val detalleLiveData = Transformations.switchMap(seleccionLiveData) { id ->
    repositorio.getDetalle(id)
}

// MediatorLiveData
val liveDataCombinado = MediatorLiveData<String>()
liveDataCombinado.addSource(fuente1) { actualizar() }
liveDataCombinado.addSource(fuete2) { actualizar() }
```

## LiveData en Compose

```kotlin
@Composable
fun Pantalla(viewModel: MiViewModel) {
    val mensaje by viewModel.mensaje.observeAsState("默认值")

    Text(mensaje)
}
```

## Best Practices

- Usar LiveData para UI state en arquitecturas MVVM
- Preferir StateFlow en nuevo código Kotlin
- Usar observe() con lifecycle owner correcto

## Comparación

| Característica | LiveData | StateFlow |
|----------------|----------|-----------|
| Android only | ✅ | ❌ |
| Lifecycle aware | ✅ | ✅ (con lifecycleRuntime) |
| Cancelable | ❌ | ✅ |
| Kotlin only | ❌ | ✅ |
| operators | Limitados | Completo |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
