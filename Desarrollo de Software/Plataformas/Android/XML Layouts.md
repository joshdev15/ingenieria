#development #android

Los XML Layouts definen la estructura visual de las interfaces en Android.

## Tipos de Layout

### LinearLayout
```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hola" />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Click" />
</LinearLayout>
```

### ConstraintLayout
```xml
<androidx.constraintlayout.widget.ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/tvTitulo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:text="Título" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

### RelativeLayout
```xml
<RelativeLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/tv1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Centrado" />
</RelativeLayout>
```

### FrameLayout
```xml
<FrameLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Overlay" />
</FrameLayout>
```

## Dimensiones

| Valor | Descripción |
|-------|-------------|
| `match_parent` | Ocupa todo el espacio disponible |
| `wrap_content` | Ocupa solo lo necesario |
| `0dp` | Usado con weight en LinearLayout |

## Weight en LinearLayout
```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal">

    <TextView
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="50%" />

    <TextView
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:text="50%" />
</LinearLayout>
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
