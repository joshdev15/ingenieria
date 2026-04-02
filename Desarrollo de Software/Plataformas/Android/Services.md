#development #android

Los Services son componentes que ejecutan tareas en background sin UI.

## Foreground Service

```kotlin
class MiServicio : Service() {
    companion object {
        const val CHANNEL_ID = "mi_canal"
        const val NOTIFICATION_ID = 1
    }

    override fun onCreate() {
        super.onCreate()
        createNotificationChannel()
    }

    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        val notification = NotificationCompat.Builder(this, CHANNEL_ID)
            .setContentTitle("Servicio activo")
            .setContentText("Trabajando en background...")
            .setSmallIcon(R.drawable.ic_icon)
            .build()

        startForeground(NOTIFICATION_ID, notification)

        // Trabajo
        return START_STICKY
    }

    override fun onBind(intent: Intent?): IBinder? = null

    private fun createNotificationChannel() {
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            val channel = NotificationChannel(
                CHANNEL_ID,
                "Mi Canal",
                NotificationManager.IMPORTANCE_LOW
            ).apply {
                description = "Notificaciones del servicio"
            }
            val manager = getSystemService(NotificationManager::class.java)
            manager.createNotificationChannel(channel)
        }
    }
}
```

## Iniciar/Detener Service

```kotlin
// En Activity
val intent = Intent(this, MiServicio::class.java)
ContextCompat.startForegroundService(this, intent)

// Detener
val intent = Intent(this, MiServicio::class.java)
stopService(intent)
```

## IntentService (Deprecated → usar WorkManager)

```kotlin
@Deprecated("Usar WorkManager")
class MiIntentService : IntentService("MiIntentService") {
    override fun onHandleIntent(intent: Intent?) {
        // Trabajo en background
    }
}
```

## JobIntentService (para API >= O)

```kotlin
class MiJobIntentService : JobIntentService() {
    companion object {
        const val JOB_ID = 1001

        fun enqueueWork(context: Context, intent: Intent) {
            enqueueWork(context, MiJobIntentService::class.java, JOB_ID, intent)
        }
    }

    override fun onHandleWork(intent: Intent) {
        // Trabajo
    }
}

// Encolar trabajo
MiJobIntentService.enqueueWork(context, intent)
```

## Background vs Foreground

| Tipo | Descripción | Ejemplo |
|------|-------------|---------|
| **Foreground** | Visible al usuario, no puede ser matado | Música, navegación |
| **Background** | invisible, puede ser limitado | Sincronización |
| **IntentService** | Tarea corta, se autodestruye | Procesar imagen |
| **JobIntentService** | Similar pero con queue | Cargas pequeñas |

## Restricciones Background (Android 8+)

```kotlin
// Antes (Android 7)
startService(intent)

// Android 8+
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    startForegroundService(intent)
} else {
    startService(intent)
}
```

## Bound Service (Comunicación Activity-Service)

```kotlin
class MiBoundService : Service() {
    private val binder = MiBinder()

    inner class MiBinder : Binder() {
        fun getService(): MiBoundService = this@MiBoundService
    }

    override fun onBind(intent: Intent?): IBinder = binder

    fun miMetodo(): String = "Hola del servicio"
}

// En Activity
var servicio: MiBoundService? = null
val connection = object : ServiceConnection {
    override fun onServiceConnected(name: ComponentName?, service: IBinder?) {
        val binder = service as MiBoundService.MiBinder
        servicio = binder.getService()
    }
    override fun onServiceDisconnected(name: ComponentName?) {
        servicio = null
    }
}

bindService(Intent(this, MiBoundService::class.java), connection, Context.BIND_AUTO_CREATE)
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
