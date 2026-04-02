#development #android

#development #android

Thread representa un hilo de ejecución en Android.

## Thread Básico

```kotlin
// Crear y ejecutar Thread
Thread {
    // Este código se ejecuta en un hilo separado
    println("Hilo secundario")
}.start()

// Con Runnable
val runnable = Runnable {
    for (i in 1..5) {
        println("Contador: $i")
        Thread.sleep(1000)
    }
}
Thread(runnable).start()
```

## Thread en Activity (CUIDADO)

```kotlin
class MiActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        Thread {
            // ⚠️ NO hacer esto - puede causar memory leak
            runOnUiThread {
                textView.text = "Actualizado desde thread"
            }
        }.start()
    }
}
```

## Interrupted

```kotlin
val thread = Thread {
    try {
        while (!Thread.interrupted()) {
            // Trabajo
            Thread.sleep(1000)
        }
    } catch (e: InterruptedException) {
        // El hilo fue interrumpido
    }
}
thread.start()
thread.interrupt()  // Detener
```

## ExecutorService (Mejor alternativa)

```kotlin
val executor = Executors.newSingleThreadExecutor()

// Ejecutar tarea
executor.execute {
    // Trabajo en background
}

// Tarea con resultado
executor.submit(Callable<String> {
    "Resultado"
})

// Shutdown
executor.shutdown()     // Espera tareas pendientes
executor.shutdownNow() // Intenta detener inmediatamente
```

## Executors utilitarios

```kotlin
// Pool de un hilo
Executors.newSingleThreadExecutor()

// Pool fijo
Executors.newFixedThreadPool(4)

// Pool dinámico
Executors.newCachedThreadPool()

// Scheduler
Executors.newScheduledThreadPool(2).scheduleAtFixedRate({
    println("Ejecuta cada segundo")
}, 1, 1, TimeUnit.SECONDS)
```

## Best Practices

- ❌ No usar Thread directamente para UI
- ✅ Usar Coroutines (más moderno)
- ✅ Usar ExecutorService para operaciones cortas
- ✅ Handler/Looper para comunicación con UI thread

[[Desarrollo de Software/Plataformas/Android/Android.md]]
