#development #android

Los Fragments son componentes modulares de UI que representan una porción de la interfaz.

## Características

- Modular: Un activity puede contener múltiples fragments
- Reutilizable: Puede usarse en diferentes activities
- Lifecycle propio: Tiene su propio ciclo de vida
- Comunicación: Se comunica con su activity padre

## Ciclo de Vida

```
onAttach() → onCreate() → onCreateView() → onActivityCreated() → onStart() → onResume()
→ onPause() → onStop() → onDestroyView() → onDestroy() → onDetach()
```

## Crear Fragment

```kotlin
class MiFragment : Fragment() {
    override fun onCreateView(
        inflater: LayoutInflater,
        container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        return inflater.inflate(R.layout.fragment_mi, container, false)
    }
}
```

## Comunicación Activity-Fragment

```kotlin
// En el Fragment
interface OnFragmentListener {
    fun onDatoEnviado(dato: String)
}

// En la Activity
class MainActivity : AppCompatActivity(), OnFragmentListener {
    override fun onDatoEnviado(dato: String) {
        // Manejar dato
    }
}
```

## Navigation Component

```xml
<!-- nav_graph.xml -->
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/nav_graph"
    app:startDestination="@id/fragmentA">

    <fragment
        android:id="@+id/fragmentA"
        android:name="com.app.FragmentA">
        <action
            android:id="@+id/action_A_to_B"
            app:destination="@id/fragmentB" />
    </fragment>

    <fragment
        android:id="@+id/fragmentB"
        android:name="com.app.FragmentB" />
</navigation>
```

```kotlin
// Navegar
findNavController().navigate(R.id.action_A_to_B)

// Con argumentos
val bundle = bundleOf("dato" to "valor")
findNavController().navigate(R.id.fragmentB, bundle)
```

## Best Practices

- Usar ViewModel compartido con Activity
- Evitar comunicación directa entre fragments
- Usar Navigation Component

[[Desarrollo de Software/Plataformas/Android/Android.md]]
