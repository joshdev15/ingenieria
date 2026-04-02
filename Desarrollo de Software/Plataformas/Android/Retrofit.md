#development #android

Retrofit es el cliente HTTP más usado para Android.

## API Interface

```kotlin
interface ApiService {
    
    @GET("usuarios")
    suspend fun getUsuarios(): List<Usuario>

    @GET("usuarios/{id}")
    suspend fun getUsuario(@Path("id") id: Long): Usuario

    @POST("usuarios")
    suspend fun createUsuario(@Body usuario: Usuario): Usuario

    @PUT("usuarios/{id}")
    suspend fun updateUsuario(
        @Path("id") id: Long,
        @Body usuario: Usuario
    ): Usuario

    @DELETE("usuarios/{id}")
    suspend fun deleteUsuario(@Path("id") id: Long)

    @GET("usuarios")
    suspend fun buscarUsuarios(
        @Query("q") query: String
    ): List<Usuario>

    @Multipart
    @POST("upload")
    suspend fun uploadImage(
        @Part image: MultipartBody.Part
    ): UploadResponse
}
```

## Retrofit Builder

```kotlin
object RetrofitClient {
    private const val BASE_URL = "https://api.ejemplo.com/"

    val api: ApiService by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .client(OkHttpClient.Builder()
                .addInterceptor { chain ->
                    val request = chain.request().newBuilder()
                        .addHeader("Authorization", "Bearer token")
                        .build()
                    chain.proceed(request)
                }
                .build())
            .addConverterFactory(GsonConverterFactory.create())
            .addConverterFactory(Json.asConverterFactory("application/json".toResponseBody()))
            .build()
            .create(ApiService::class.java)
    }
}
```

## Response Wrapper

```kotlin
// Para manejar estados
sealed class Resource<T> {
    data class Success<T>(val data: T) : Resource<T>()
    data class Error<T>(val message: String, val data: T? = null) : Resource<T>()
    class Loading<T> : Resource<T>()
}

suspend fun <T> safeApiCall(apiCall: suspend () -> T): Resource<T> {
    return try {
        Resource.Success(apiCall())
    } catch (e: Exception) {
        Resource.Error(e.message ?: "Error desconocido")
    }
}

// Uso
val result = safeApiCall { api.getUsuarios() }
when (result) {
    is Resource.Success -> mostrarDatos(result.data)
    is Resource.Error -> mostrarError(result.message)
    is Resource.Loading -> mostrarCarga()
}
```

## Con Flow

```kotlin
@GET("usuarios")
fun getUsuariosFlow(): Flow<List<Usuario>> = flow {
    val response = api.getUsuarios()
    emit(response)
}.flowOn(Dispatchers.IO).catch { e ->
    emit(emptyList())
}
```

## Interceptors

```kotlin
// Logging
val logging = HttpLoggingInterceptor().apply {
    level = HttpLoggingInterceptor.Level.BODY
}

// Auth
val authInterceptor = Interceptor { chain ->
    val request = chain.request().newBuilder()
        .addHeader("Authorization", "Bearer ${getToken()}")
        .build()
    chain.proceed(request)
}
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
