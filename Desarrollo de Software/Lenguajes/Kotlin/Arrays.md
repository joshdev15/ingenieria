#development #kotlin

Los arrays y colecciones en Kotlin son seguros y flexibles.

## Arrays

```kotlin
// Array de tipos primitivos
val numeros = arrayOf(1, 2, 3, 4, 5)

// Array tipado
val strings = arrayOf<String>("a", "b", "c")

// IntArray, ByteArray, etc.
val ints = intArrayOf(1, 2, 3)

// Crear con tamaño
val array = Array(5) { it * 2 }  // [0, 2, 4, 6, 8]
```

## Listas

```kotlin
// Inmutable
val lista = listOf(1, 2, 3, 4, 5)
lista[0]  // Error! es inmutable

// Mutable
val listaMut = mutableListOf(1, 2, 3)
listaMut.add(4)
listaMut.removeAt(0)
```

## Sets

```kotlin
// Inmutable
val set = setOf(1, 2, 3, 3, 3)  // [1, 2, 3]

// Mutable
val setMut = mutableSetOf(1, 2, 3)
setMut.add(4)
setMut.remove(1)
```

## Maps

```kotlin
// Inmutable
val mapa = mapOf("a" to 1, "b" to 2)

// Mutable
val mapaMut = mutableMapOf("a" to 1)
mapaMut["b"] = 2
mapaMut.put("c", 3)
```

## Operaciones

```kotlin
val nums = listOf(1, 2, 3, 4, 5)

// Transform
val duplicados = nums.map { it * 2 }

// Filter
val pares = nums.filter { it % 2 == 0 }

// Find
val primerPar = nums.find { it % 2 == 0 }

// Reduce
val suma = nums.reduce { acc, i -> acc + i }

// Any, All, None
nums.any { it > 3 }  // true
nums.all { it > 0 }  // true
nums.none { it < 0 } // true
```

## withIndex

```kotlin
val lista = listOf("a", "b", "c")
for ((index, value) in lista.withIndex()) {
    println("$index: $value")
}
```

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
