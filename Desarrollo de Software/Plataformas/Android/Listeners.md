#development #android

#development #android

Los Listeners (Listeners) son interfaces que permiten responder a eventos del usuario o del sistema.

## OnClickListener

```kotlin
// XML
<Button
    android:id="@+id/btnClick"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />

// Kotlin - forma 1
btnClick.setOnClickListener {
    Toast.makeText(this, "Click!", Toast.LENGTH_SHORT).show()
}

// Kotlin - forma 2 (con View.OnClickListener)
btnClick.setOnClickListener(object : View.OnClickListener {
    override fun onClick(v: View?) {
        println("Click en: ${v?.id}")
    }
})
```

## OnLongClickListener

```kotlin
btnClick.setOnLongClickListener {
    println("Click largo!")
    true  // consume el evento
}
```

## OnItemClickListener (RecyclerView/ListView)

```kotlin
// RecyclerView
recyclerView.adapter = object : RecyclerView.Adapter<ViewHolder>() {
    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder.itemView.setOnClickListener {
            println("Click en posición: $position")
        }
    }
}

// ListView
listView.setOnItemClickListener { parent, view, position, id ->
    println("Item: ${parent.getItemAtPosition(position)}")
}
```

## TextWatcher

```kotlin
editText.addTextChangedListener(object : TextWatcher {
    override fun beforeTextChanged(s: CharSequence?, start: Int, count: Int, after: Int) {}
    override fun onTextChanged(s: CharSequence?, start: Int, before: Int, count: Int) {}
    override fun afterTextChanged(s: Editable?) {
        println("Texto: ${s.toString()}")
    }
})
```

## OnScrollListener

```kotlin
recyclerView.addOnScrollListener(object : RecyclerView.OnScrollListener() {
    override fun onScrolled(recyclerView: RecyclerView, dx: Int, dy: Int) {
        super.onScrolled(recyclerView, dx, dy)
        val layoutManager = recyclerView.layoutManager as LinearLayoutManager
        val totalItemCount = layoutManager.itemCount
        val lastVisibleItem = layoutManager.findLastVisibleItemPosition()
    }
})
```

## Custom Listener (Interfaz)

```kotlin
// Definir interfaz
interface OnItemSeleccionadoListener {
    fun onItemSeleccionado(item: Item)
}

// En adapter
class MiAdapter(
    private val listener: OnItemSeleccionadoListener
) : RecyclerView.Adapter<ViewHolder>() {

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder.itemView.setOnClickListener {
            listener.onItemSeleccionado(items[position])
        }
    }
}

// En Activity/Fragment
adapter = MiAdapter { item ->
    println("Seleccionado: ${item.nombre}")
}
```

## Kotlin Lambdas (Simplificado)

```kotlin
// Todos los listeners pueden usar lambdas
view.setOnClickListener { view -> /* código */ }

// Si solo se usa el click
view.setOnClickListener { /* código */ }
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
