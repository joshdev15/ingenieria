#development #android

Las Activities son el componente fundamental de Android que representa una pantalla.

## Ciclo de Vida

```
onCreate() → onStart() → onResume() → [Running] → onPause() → onStop() → onDestroy()
```

| Método | Descripción |
|--------|-------------|
| `onCreate()` | Se llama cuando se crea la activity |
| `onStart()` | Visible para el usuario |
| `onResume()` | En foreground, interactiva |
| `onPause()` | Pierde focus |
| `onStop()` | Ya no visible |
| `onDestroy()` | Se destruye |

## Crear Activity

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

## Intents (Navegación)

```kotlin
// Navegar a otra Activity
val intent = Intent(this, SegundaActivity::class.java)
startActivity(intent)

// Con datos
val intent = Intent(this, DetalleActivity::class.java)
intent.putExtra("usuario", usuario)
startActivity(intent)

// Recibir resultado
startActivityForResult(intent, REQUEST_CODE)
```

## Lifecycle Aware Components

```kotlin
class MiObserver : LifecycleObserver {
    @OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
    fun onResume() {
        // Activity resumed
    }
}
```

## Best Practices

- Usar ViewModel para datos survive rotation
- No guardar estado en variables de instancia
- Usar Navigation Component para navegación compleja

[[Desarrollo de Software/Plataformas/Android/Android.md]]
