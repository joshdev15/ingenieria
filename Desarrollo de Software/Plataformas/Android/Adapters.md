#development #android

#development #android

Los Adapters conectan datos con vistas en Android, principalmente para RecyclerView y ListView.

## RecyclerView Adapter

```kotlin
class UsuarioAdapter(
    private val usuarios: List<Usuario>
) : RecyclerView.Adapter<UsuarioAdapter.ViewHolder>() {

    class ViewHolder(view: View) : RecyclerView.ViewHolder(view)

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context)
            .inflate(R.layout.item_usuario, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val usuario = usuarios[position]
        holder.itemView.findViewById<TextView>(R.id.tvNombre).text = usuario.nombre
        holder.itemView.findViewById<TextView>(R.id.tvEmail).text = usuario.email
    }

    override fun getItemCount(): Int = usuarios.size
}
```

## Con ViewBinding

```kotlin
class UsuarioAdapter(
    private val usuarios: MutableList<Usuario>
) : RecyclerView.Adapter<UsuarioAdapter.ViewHolder>() {

    class ViewHolder(val binding: ItemUsuarioBinding) : RecyclerView.ViewHolder(binding.root)

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val binding = ItemUsuarioBinding.inflate(
            LayoutInflater.from(parent.context), parent, false
        )
        return ViewHolder(binding)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        holder.binding.tvNombre.text = usuarios[position].nombre
        holder.binding.tvEmail.text = usuarios[position].email
    }

    override fun getItemCount(): Int = usuarios.size

    fun addUsuario(usuario: Usuario) {
        usuarios.add(usuario)
        notifyItemInserted(usuarios.size - 1)
    }
}
```

## ListView Adapter

```kotlin
class UsuarioListAdapter(
    context: Context,
    private val usuarios: List<Usuario>
) : ArrayAdapter<Usuario>(context, R.layout.item_usuario, usuarios) {

    override fun getView(position: Int, convertView: View?, parent: ViewGroup): View {
        val view = convertView ?: LayoutInflater.from(context)
            .inflate(R.layout.item_usuario, parent, false)

        val usuario = usuarios[position]
        view.findViewById<TextView>(R.id.tvNombre).text = usuario.nombre
        view.findViewById<TextView>(R.id.tvEmail).text = usuario.email

        return view
    }
}

// Uso
val adapter = UsuarioListAdapter(this, listaUsuarios)
listView.adapter = adapter
```

## ViewHolder Pattern

```kotlin
class ViewHolder(view: View) : RecyclerView.ViewHolder(view) {
    val tvNombre: TextView = view.findViewById(R.id.tvNombre)
    val tvEmail: TextView = view.findViewById(R.id.tvEmail)
}

// En onBindViewHolder
override fun onBindViewHolder(holder: ViewHolder, position: Int) {
    holder.tvNombre.text = usuarios[position].nombre
    holder.tvEmail.text = usuarios[position].email
}
```

## DiffUtil (Actualizaciones eficientes)

```kotlin
class UsuarioDiffCallback(
    private val oldList: List<Usuario>,
    private val newList: List<Usuario>
) : DiffUtil.Callback() {

    override fun getOldListSize(): Int = oldList.size
    override fun getNewListSize(): Int = newList.size

    override fun areItemsTheSame(oldPos: Int, newPos: Int): Boolean {
        return oldList[oldPos].id == newList[newPos].id
    }

    override fun areContentsTheSame(oldPos: Int, newPos: Int): Boolean {
        return oldList[oldPos] == newList[newPos]
    }
}

// Uso
val diffResult = DiffUtil.calculateDiff(UsuarioDiffCallback(oldList, newList))
diffResult.dispatchUpdatesTo(this)
```

## ListAdapter (Automático con DiffUtil)

```kotlin
class UsuarioListAdapter : ListAdapter<Usuario, UsuarioViewHolder>(UsuarioDiffCallback()) {
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): UsuarioViewHolder {
        // ...
    }

    override fun onBindViewHolder(holder: UsuarioViewHolder, position: Int) {
        holder.bind(getItem(position))
    }
}

// Uso - automáticamente notifica cambios
adapter.submitList(nuevaLista)
```

[[Desarrollo de Software/Plataformas/Android/Android.md]]
