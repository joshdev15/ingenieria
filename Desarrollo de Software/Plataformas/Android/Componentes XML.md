#development #android

Los componentes XML son los elementos visuales que construyen las interfaces.

## Texto

### TextView
```xml
<TextView
    android:id="@+id/tvMensaje"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hola Mundo"
    android:textSize="16sp"
    android:textColor="@color/black"
    android:textStyle="bold" />
```

### EditText
```xml
<EditText
    android:id="@+id/etNombre"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Ingresa tu nombre"
    android:inputType="textPersonName"
    android:maxLines="1" />
```

## Botones

### Button
```xml
<Button
    android:id="@+id/btnAceptar"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Aceptar"
    android:backgroundTint="@color/primary" />
```

### ImageButton
```xml
<ImageButton
    android:id="@+id/btnImagen"
    android:layout_width="48dp"
    android:layout_height="48dp"
    android:src="@drawable/ic_buscar"
    android:contentDescription="Buscar" />
```

### MaterialButton
```xml
<com.google.android.material.button.MaterialButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Continuar"
    app:icon="@drawable/ic_arrow" />
```

## Imágenes

### ImageView
```xml
<ImageView
    android:id="@+id/ivFoto"
    android:layout_width="200dp"
    android:layout_height="200dp"
    android:src="@drawable/foto_perfil"
    android:scaleType="centerCrop" />
```

## Listas

### RecyclerView
```xml
<androidx.recyclerview.widget.RecyclerView
    android:id="@+id/rvLista"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layoutManager="androidx.recyclerview.widget.LinearLayoutManager" />
```

### ListView
```xml
<ListView
    android:id="@+id/lvOpciones"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

## Contenedores

### CardView
```xml
<com.google.android.material.card.MaterialCardView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:cardElevation="4dp"
    app:cardCornerRadius="8dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Contenido" />
</com.google.android.material.card.MaterialCardView>
```

### SwipeRefreshLayout
```xml
<androidx.swiperefreshlayout.widget.SwipeRefreshLayout
    android:id="@+id/swipeRefresh"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <RecyclerView
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</androidx.swiperefreshlayout.widget.SwipeRefreshLayout>
```

## Atributos Comunes

| Atributo | Descripción |
|----------|-------------|
| `android:id` | Identificador único |
| `android:layout_width` | Ancho |
| `android:layout_height` | Alto |
| `android:layout_margin` | Margen exterior |
| `android:padding` | Relleno interior |
| `android:visibility` | visible/invisible/gone |
| `android:background` | Fondo |

[[Desarrollo de Software/Plataformas/Android/Android.md]]
