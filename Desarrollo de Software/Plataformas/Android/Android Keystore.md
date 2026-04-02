#development #android

Android Keystore almacena claves criptográficas de forma segura en hardware o software.

## Keystore Básico

```kotlin
// Obtener keystore
val keyStore = KeyStore.getInstance("AndroidKeyStore")
keyStore.load(null)

// Generar clave
val keyGenerator = KeyGenerator.getInstance(
    KeyProperties.KEY_ALGORITHM_AES,
    "AndroidKeyStore"
)

val keyGenSpec = KeyGenParameterSpec.Builder(
    "mi_clave",
    KeyProperties.PURPOSE_ENCRYPT or KeyProperties.PURPOSE_DECRYPT
)
    .setBlockModes(KeyProperties.BLOCK_MODE_GCM)
    .setEncryptionPaddings(KeyProperties.ENCRYPTION_PADDING_NONE)
    .setKeySize(256)
    .build()

keyGenerator.init(keyGenSpec)
keyGenerator.generateKey()
```

## Encriptar/Desencriptar

```kotlin
fun encriptar(datos: ByteArray): ByteArray {
    val keyStore = KeyStore.getInstance("AndroidKeyStore")
    keyStore.load(null)
    
    val key = keyStore.getKey("mi_clave", null) as SecretKey
    
    val cipher = Cipher.getInstance("AES/GCM/NoPadding")
    cipher.init(Cipher.ENCRYPT_MODE, key)
    
    val iv = cipher.iv
    val datosEncriptados = cipher.doFinal(datos)
    
    // Combinar IV + datos
    return iv + datosEncriptados
}

fun desencriptar(datosEncriptados: ByteArray): ByteArray {
    val keyStore = KeyStore.getInstance("AndroidKeyStore")
    keyStore.load(null)
    
    val key = keyStore.getKey("mi_clave", null) as SecretKey
    
    // Extraer IV (12 bytes para GCM)
    val iv = datosEncriptados.copyOfRange(0, 12)
    val datos = datosEncriptados.copyOfRange(12, datosEncriptados.size)
    
    val cipher = Cipher.getInstance("AES/GCM/NoPadding")
    val spec = GCMParameterSpec(128, iv)
    cipher.init(Cipher.DECRYPT_MODE, key, spec)
    
    return cipher.doFinal(datos)
}
```

## AndroidKeyStore Characteristics

| Característica | Descripción |
|----------------|-------------|
| **Hardware-backed** | Las claves pueden almacenarse en TEE/SE |
| **Secure** | Las claves nunca salen del keystore |
| **App-specific** | Solo la app que crea la clave puede usarla |
| **User-bound** | Puede requerir autenticación del usuario |

## Con Autenticación Biométrica

```kotlin
val keyGenSpec = KeyGenParameterSpec.Builder(
    "mi_clave_segura",
    KeyProperties.PURPOSE_ENCRYPT or KeyProperties.PURPOSE_DECRYPT
)
    .setUserAuthenticationRequired(true)
    .setUserAuthenticationParameters(
        0,  // Timeout (0 = cada vez)
        KeyProperties.AUTH_BIOMETRIC_STRONG
    )
    .build()
```

## SharedPreferences Encriptado

```kotlin
// Usando EncryptedSharedPreferences
val masterKey = MasterKey.Builder(context)
    .setKeyScheme(MasterKey.KeyScheme.AES256_GCM)
    .build()

val sharedPreferences = EncryptedSharedPreferences.create(
    context,
    "secure_prefs",
    masterKey,
    EncryptedSharedPreferences.PrefKeyEncryptionScheme.AES256_SIV,
    EncryptedSharedPreferences.PrefValueEncryptionScheme.AES256_GCM
)

sharedPreferences.edit().putString("token", "valor_secreto").apply()
```

## Librerías Recomendadas

```kotlin
// AndroidX Security
implementation "androidx.security:security-crypto:1.1.0-alpha06"

// Para más control
implementation "com.google.crypto.tink:tink-android:1.7.0"
```

## Tink (Google's Crypto Library)

```kotlin
// Inicializar
val tink = AndroidTinkGcmAead()

// Encriptar
val aead = tink.getPrimitive(Aead::class.java)
val plaintext = "mensaje secreto".toByteArray()
val associatedData = "app_data".toByteArray()

val ciphertext = aead.encrypt(plaintext, associatedData)

// Desencriptar
val decrypted = aead.decrypt(ciphertext, associatedData)
```

## Best Practices

- Usar Android Keystore para datos sensibles
- No almacenar claves en SharedPreferences plain
- Usar EncryptedSharedPreferences para preferencias
- Habilitar biometric authentication para mayor seguridad

[[Desarrollo de Software/Plataformas/Android/Android.md]]
