#development #android

Room es la biblioteca de base de datos para Android con SQLite.

## Entity

```kotlin
@Entity(tableName = "usuarios")
data class Usuario(
    @PrimaryKey(autoGenerate = true)
    val id: Long = 0,
    val nombre: String,
    val email: String,
    val edad: Int? = null
)
```

## DAO (Data Access Object)

```kotlin
@Dao
interface UsuarioDao {
    
    @Query("SELECT * FROM usuarios")
    fun getAll(): LiveData<List<Usuario>>

    @Query("SELECT * FROM usuarios")
    suspend fun getAllSync(): List<Usuario>

    @Query("SELECT * FROM usuarios WHERE id = :id")
    suspend fun getById(id: Long): Usuario?

    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insert(usuario: Usuario): Long

    @Update
    suspend fun update(usuario: Usuario)

    @Delete
    suspend fun delete(usuario: Usuario)

    @Query("DELETE FROM usuarios")
    suspend fun deleteAll()

    @Query("SELECT * FROM usuarios WHERE nombre LIKE '%' || :query || '%'")
    fun buscar(query: String): LiveData<List<Usuario>>
}
```

## Database

```kotlin
@Database(entities = [Usuario::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun usuarioDao(): UsuarioDao

    companion object {
        @Volatile
        private var INSTANCE: AppDatabase? = null

        fun getDatabase(context: Context): AppDatabase {
            return INSTANCE ?: synchronized(this) {
                val instance = Room.databaseBuilder(
                    context.applicationContext,
                    AppDatabase::class.java,
                    "app_database"
                )
                .fallbackToDestructiveMigration()
                .build()
                INSTANCE = instance
                instance
            }
        }
    }
}
```

## Repository

```kotlin
class UsuarioRepository(private val usuarioDao: UsuarioDao) {
    val allUsuarios: LiveData<List<Usuario>> = usuarioDao.getAll()

    suspend fun insert(usuario: Usuario): Long {
        return usuarioDao.insert(usuario)
    }

    suspend fun update(usuario: Usuario) {
        usuarioDao.update(usuario)
    }

    suspend fun delete(usuario: Usuario) {
        usuarioDao.delete(usuario)
    }
}
```

## TypeConverters

```kotlin
class Converters {
    @TypeConverter
    fun fromTimestamp(value: Long?): Date? {
        return value?.let { Date(it) }
    }

    @TypeConverter
    fun dateToTimestamp(date: Date?): Long? {
        return date?.time
    }
}

// En database
@Database(entities = [Usuario::class], version = 1)
@TypeConverters(Converters::class)
abstract class AppDatabase : RoomDatabase()
```

## Relationships

```kotlin
// One-to-Many
@Entity
class Carrito {
    @PrimaryKey val id: Long = 1
    val usuarioId: Long
}

@Entity
class ItemCarrito {
    @PrimaryKey(autoGenerate = true) val id: Long = 0
    val carritoId: Long
    val producto: String
}

data class CarritoConItems(
    @Embedded val carrito: Carrito,
    @Relation(
        parentColumn = "id",
        entityColumn = "carritoId"
    )
    val items: List<ItemCarrito>
)
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
