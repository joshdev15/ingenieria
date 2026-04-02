#development #android

#development #android

Handler permite enviar y procesar mensajes Runnable entre hilos, principalmente para comunicar con el hilo UI.

## Conceptos

- **Looper**: Mantiene el mensaje queue de un thread
- **Handler**: Envía mensajes al Looper
- **Message**: Unidad de comunicación
- **Runnable**: Tarea ejecutable

## Handler Básico

```kotlin
// Crear Handler en UI thread ( automaticamente asociado a Looper del hilo actual)
val handler = Handler(Looper.getMainLooper())

// Enviar Runnable al UI thread
handler.post {
    textView.text = "Actualizado desde background"
}

// Con delay
handler.postDelayed({
    textView.text = "Actualizado después de 2 segundos"
}, 2000)

// Remover pendientes
handler.removeCallbacksAndMessages(null)
```

## Handler con nuevo Thread

```kotlin
val backgroundHandler = Handler(Looper.getMainLooper())

Thread {
    // Trabajo en background...
    backgroundHandler.post {
        // Actualizar UI
        progressBar.visibility = View.GONE
    }
}.start()
```

## Messages

```kotlin
// Crear Message
val msg = handler.obtainMessage()
msg.what = 1
msg.obj = "dato"
handler.sendMessage(msg)

// Enviar con datos
val bundle = Bundle()
bundle.putString("key", "value")
val msg = handler.obtainMessage(1, bundle)
handler.sendMessage(msg)

// Recibir
val handler = object : Handler(Looper.getMainLooper()) {
    override fun handleMessage(msg: Message) {
        when (msg.what) {
            1 -> println("Recibido: ${msg.obj}")
        }
    }
}
```

## runOnUiThread

```kotlin
// En Activity
Thread {
    // Trabajo background
    runOnUiThread {
        // Actualizar UI
        textView.text = "Listo"
    }
}.start()
```

## Comparación

| Método | Uso |
|--------|-----|
| `handler.post()` | Ejecutar en hilo del Handler |
| `runOnUiThread()` | Ejecutar en UI thread desde cualquier hilo |
| `view.post()` | Ejecutar cuando la view esté lista |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
