#development #android

Los permisoscontrolan el acceso a funcionalidades y datos sensibles del dispositivo.

## Permisos en Manifest

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.app">

    <!-- Permisos normales (automáticos) -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    <!-- Permisos peligrosos (requieren aprobación) -->
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.READ_CONTACTS" />
    <uses-permission android:name="android.permission.SEND_SMS" />

    <!-- Permisos especiales -->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
    <uses-permission android:name="android.permission.REQUEST_IGNORE_BATTERY_OPTIMIZATIONS" />
</manifest>
```

## Solicitar Permisos (Runtime)

```kotlin
// Verificar permiso
if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA)
    != PackageManager.PERMISSION_GRANTED) {
    // Solicitar
    ActivityCompat.requestPermissions(
        this,
        arrayOf(Manifest.permission.CAMERA),
        REQUEST_CODE_CAMERA
    )
}

// Resultado
override fun onRequestPermissionsResult(
    requestCode: Int,
    permissions: Array<out String>,
    grantResults: IntArray
) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults)
    when (requestCode) {
        REQUEST_CODE_CAMERA -> {
            if (grantResults.isNotEmpty() && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                // Permiso concedido
            } else {
                // Permiso denegado
            }
        }
    }
}
```

## Permisos con rationale

```kotlin
if (ActivityCompat.shouldShowRequestPermissionRationale(this, Manifest.permission.CAMERA)) {
    // Mostrar explicación
    AlertDialog.Builder(this)
        .setMessage("Se necesita cámara para tomar fotos")
        .setPositiveButton("OK") { _, _ ->
            ActivityCompat.requestPermissions(
                this,
                arrayOf(Manifest.permission.CAMERA),
                REQUEST_CODE_CAMERA
            )
        }
        .show()
} else {
    ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.CAMERA), REQUEST_CODE_CAMERA)
}
```

## Permission Launch (Activity Result API)

```kotlin
val permisoLauncher = registerForActivityResult(
    ActivityResultContracts.RequestPermission()
) { concedido ->
    if (concedido) {
        // Usar cámara
    }
}

permisoLauncher.launch(Manifest.permission.CAMERA)

// Múltiples permisos
val permisosLauncher = registerForActivityResult(
    ActivityResultContracts.RequestMultiplePermissions()
) { permisos ->
    val cameraGranted = permisos[Manifest.permission.CAMERA] ?: false
    val locationGranted = permisos[Manifest.permission.ACCESS_FINE_LOCATION] ?: false
}
```

## Permisos en XML (Compose)

```kotlin
// With permission
val permissionLauncher = rememberLauncherForActivityResult(
    ActivityResultContracts.RequestPermission()
) { }

Button(onClick = { permissionLauncher.launch(Manifest.permission.CAMERA) }) {
    Text("Tomar foto")
}
```

## Mejores Prácticas

- Solicitar solo los permisos necesarios
- Explicar por qué se necesita el permiso
- Manejar el caso cuando el permiso es denegado
- Usar permisos de lectura/escritura separados en Android 13+

[[Desarrollo de Software/Plataformas/Android/Android.md]]
