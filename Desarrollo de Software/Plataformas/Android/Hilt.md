#development #android

Hilt es el estándar de inyección de dependencias para Android.

## Setup

```kotlin
// build.gradle (app)
plugins {
    id 'com.google.dagger.hilt.android'
}
dependencies {
    implementation 'com.google.dagger:hilt-android:2.48'
    kapt 'com.google.dagger:hilt-android-compiler:2.48'
}
```

## Application

```kotlin
@HiltAndroidApp
class MiApp : Application()
```

## Module

```kotlin
@Module
@InstallIn(SingletonComponent::class)
object AppModule {

    @Provides
    @Singleton
    fun provideRetrofit(): Retrofit {
        return Retrofit.Builder()
            .baseUrl("https://api.ejemplo.com/")
            .build()
    }

    @Provides
    @Singleton
    fun provideApiService(retrofit: Retrofit): ApiService {
        return retrofit.create(ApiService::class.java)
    }

    @Provides
    fun provideUsuarioRepository(
        api: ApiService,
        dao: UsuarioDao
    ): UsuarioRepository {
        return UsuarioRepository(api, dao)
    }
}
```

## Inject en Classes

```kotlin
// Activity
@AndroidEntryPoint
class MainActivity : AppCompatActivity() {
    @Inject
    lateinit var repository: UsuarioRepository

    @Inject
    lateinit var analytics: Analytics
}

// ViewModel
@HiltViewModel
class UsuarioViewModel @Inject constructor(
    private val repository: UsuarioRepository
) : ViewModel() {

}

// Fragment
@AndroidEntryPoint
class MiFragment : Fragment() {
    @Inject
    lateinit var viewModelFactory: UsuarioViewModelFactory
}
```

## Constructor Injection

```kotlin
class UsuarioRepository @Inject constructor(
    private val api: ApiService,
    private val dao: UsuarioDao
) {
    // ...
}
```

## Named Qualifiers

```kotlin
@Provides
@Named("debug")
fun provideOkHttpDebug(): OkHttpClient { ... }

@Provides
@Named("release")
fun provideOkHttpRelease(): OkHttpClient { ... }

@Inject
@Named("debug")
lateinit var client: OkHttpClient
```

## Scopes

| Scope | Descripción |
|-------|-------------|
| `@Singleton` | Una instancia para toda la app |
| `@ActivityScoped` | Una instancia por activity |
| `@FragmentScoped` | Una instancia por fragment |
| `@ViewModelScoped` | Una instancia por ViewModel |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
