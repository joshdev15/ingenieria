#development #kotlin #multiplatform

Crear APIs que funcionen en múltiples plataformas es el objetivo principal de KMP.

## Patrón de Interfaz Común

```kotlin
// commonMain - Definir interfaz
interface HttpClient {
    suspend fun get(url: String): String
    suspend fun post(url: String, body: String): String
}

// androidMain - Implementación Android
class AndroidHttpClient : HttpClient {
    private val client = OkHttpClient()
    
    override suspend fun get(url: String): String {
        return withContext(Dispatchers.IO) {
            client.newCall(Request.Builder().url(url).build()).execute().body?.string() ?: ""
        }
    }
    
    override suspend fun post(url: String, body: String): String {
        return withContext(Dispatchers.IO) {
            client.newCall(Request.Builder()
                .url(url)
                .post(body.toRequestBody("application/json".toMediaTypeOrNull()))
                .build())
                .execute().body?.string() ?: ""
        }
    }
}

// iosMain - Implementación iOS (usando NSURLSession)
class IosHttpClient : HttpClient {
    override suspend fun get(url: String): String = NSURLSession.shared.dataTaskWithURL(NSURL(url)!!).await().toString()
}

// jvmMain - Implementación JVM
class JvmHttpClient : HttpClient {
    private val client = HttpClient.new()
    
    override suspend fun get(url: String): String {
        return client.get(url).bodyAsText()
    }
}
```

## Ktor Client (Multiplataforma)

```kotlin
// commonMain - Usar Ktor
expect val httpClient: HttpClient

// build.gradle.kts common
implementation("io.ktor:ktor-client-core:2.3.7")

// androidMain
implementation("io.ktor:ktor-client-okhttp:2.3.7")

// iosMain
implementation("io.ktor:ktor-client-ios:2.3.7")

// jsMain
implementation("io.ktor:ktor-client-js:2.3.7")
```

## Repository Pattern

```kotlin
// commonMain - Interfaz
interface UserRepository {
    suspend fun getUsers(): List<User>
    suspend fun getUser(id: Int): User?
}

// commonMain - Implementación esperada
class UserRepositoryImpl(
    private val httpClient: HttpClient
) : UserRepository {
    override suspend fun getUsers(): List<User> {
        val json = httpClient.get("https://api.example.com/users")
        return parseUsers(json)
    }
}

// Inyección en Android
val repository = UserRepositoryImpl(AndroidHttpClient())

// Inyección en iOS
val repository = UserRepositoryImpl(IosHttpClient())
```

## Serialización Multiplataforma

```kotlin
// commonMain
@Serializable
data class User(
    val id: Int,
    val name: String,
    val email: String
)

// build.gradle.kts
plugins {
    kotlin("serialization") version "1.9.20"
}

dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.6.2")
}
```

## Storage Multiplataforma

```kotlin
// DataStore / Preferences
// commonMain
interface Storage {
    suspend fun getString(key: String): String?
    suspend fun putString(key: String, value: String)
}

// androidMain - DataStore
class DataStoreStorage(private val context: Context) : Storage {
    private val dataStore = context.dataStore
    
    override suspend fun getString(key: String): String? {
        return dataStore.data.first()[key]
    }
    
    override suspend fun putString(key: String, value: String) {
        dataStore.edit { it[key] = value }
    }
}

// Multiplatform Settings (más simple)
val settings = multiplatformSettings()
settings.putString("token", "xxx")
val token = settings.getString("token")
```

## Logger Multiplataforma

```kotlin
// commonMain
expect fun log(message: String)

// androidMain
actual fun log(message: String) = android.util.Log.d("APP", message)

// iosMain
actual fun log(message: String) = NSLog("%@", message)

// jsMain
@JsExport
@JsName("console")
external val console: dynamic

actual fun log(message: String) { console.log(message) }
```

[[Desarrollo de Software/Plataformas/Kotlin Multiplatform/Kotlin Multiplatform.md]]
