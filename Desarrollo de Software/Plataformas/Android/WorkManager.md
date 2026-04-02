#development #android

WorkManager agenda y ejecuta trabajo confiable en background.

## Setup

```kotlin
// build.gradle
dependencies {
    implementation "androidx.work:work-runtime-ktx:2.8.1"
}
```

## Worker Básico

```kotlin
class MiWorker(
    context: Context,
    workerParams: WorkerParameters
) : CoroutineWorker(context, workerParams) {

    override suspend fun doWork(): Result {
        return try {
            // Trabajo
            Result.success()
        } catch (e: Exception) {
            Result.failure()
        }
    }
}

// Usar
val workRequest = OneTimeWorkRequestBuilder<MiWorker>().build()
WorkManager.getInstance(context).enqueue(workRequest)
```

## Tipos de WorkRequest

```kotlin
// OneTime (una vez)
val oneTimeRequest = OneTimeWorkRequestBuilder<MiWorker>().build()

// Periodic (periódico - mínimo 15 min)
val periodicRequest = PeriodicWorkRequestBuilder<MiWorker>(
    15, TimeUnit.MINUTES
).build()
```

## Constraints

```kotlin
val constraints = Constraints.Builder()
    .setRequiredNetworkType(NetworkType.CONNECTED)  // Requiere internet
    .setRequiresBatteryNotLow(true)                  // Batería no baja
    .setRequiresCharging(true)                        // Cargando
    .setRequiresDeviceIdle(true)                       // Device idle (API 23+)
    .build()

val workRequest = OneTimeWorkRequestBuilder<MiWorker>()
    .setConstraints(constraints)
    .build()
```

## Input/Output Data

```kotlin
// Worker con input
class MiWorker(
    context: Context,
    params: WorkerParameters
) : CoroutineWorker(context, params) {

    override suspend fun doWork(): Result {
        val input = inputData.getString("clave") ?: return Result.failure()

        val output = workDataOf("resultado" to "procesado: $input")

        return Result.success(output)
    }
}

// Encolar con input
val inputData = workDataOf("clave" to "valor")
val request = OneTimeWorkRequestBuilder<MiWorker>()
    .setInputData(inputData)
    .build()

// Obtener output
WorkManager.getInstance(context)
    .getWorkInfoByIdLiveData(request.id)
    .observe(this) { workInfo ->
        if (workInfo?.state == WorkInfo.State.SUCCEEDED) {
            val resultado = workInfo.outputData.getString("resultado")
        }
    }
```

## Work Chains (Secuencia)

```kotlin
// A → B → C
val workA = OneTimeWorkRequestBuilder<WorkerA>().build()
val workB = OneTimeWorkRequestBuilder<WorkerB>().build()
val workC = OneTimeWorkRequestBuilder<WorkerC>().build()

WorkManager.getInstance(context)
    .beginWith(workA)
    .then(workB)
    .then(workC)
    .enqueue()
```

## Parallel Work

```kotlin
val workA = OneTimeWorkRequestBuilder<WorkerA>().build()
val workB = OneTimeWorkRequestBuilder<WorkerB>().build()
val workC = OneTimeWorkRequestBuilder<WorkerC>().build()

WorkManager.getInstance(context)
    .enqueue(listOf(workA, workB, workC))
```

## Retry Policy

```kotlin
val request = OneTimeWorkRequestBuilder<MiWorker>()
    .setBackoffCriteria(
        BackoffPolicy.EXPONENTIAL,
        30, TimeUnit.SECONDS
    )
    .build()
```

## Observar Estado

```kotlin
// LiveData
WorkManager.getInstance(context)
    .getWorkInfosForUniqueWorkLiveData("nombre_trabajo")
    .observe(this) { workInfos ->
        workInfos.forEach { info ->
            when (info.state) {
                WorkInfo.State.ENQUEUED -> println("En cola")
                WorkInfo.State.RUNNING -> println("Ejecutando")
                WorkInfo.State.SUCCEEDED -> println("Éxito")
                WorkInfo.State.FAILED -> println("Falló")
                WorkInfo.State.BLOCKED -> println("Bloqueado")
                WorkInfo.State.CANCELLED -> println("Cancelado")
            }
        }
    }

// StateFlow
val workInfos = WorkManager.getInstance(context)
    .getWorkInfosForUniqueWork("nombre_trabajo")
```

## Cancel Work

```kotlin
WorkManager.getInstance(context).cancelUniqueWork("nombre_trabajo")
WorkManager.getInstance(context).cancelAllWork()
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
