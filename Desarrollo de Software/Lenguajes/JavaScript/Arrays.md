#development #javascript

Los arrays son listas ordenadas de valores.

## Crear Arrays

```javascript
// Literales
const numeros = [1, 2, 3, 4, 5]

// Constructor
const numeros = new Array(1, 2, 3)

// Array vacío con tamaño
const arr = new Array(10)
```

## Métodos de Iteración

```javascript
const nums = [1, 2, 3, 4, 5]

// map - transformar
const doubled = nums.map(n => n * 2)

// filter - filtrar
const even = nums.filter(n => n % 2 === 0)

// reduce - acumular
const sum = nums.reduce((acc, n) => acc + n, 0)

// forEach - iterar
nums.forEach(n => console.log(n))

// find - buscar primero
const found = nums.find(n => n > 3)

// some - al menos uno
const hasEven = nums.some(n => n % 2 === 0)

// every - todos
const allPositive = nums.every(n => n > 0)
```

## Métodos de Modificación

```javascript
const arr = [1, 2, 3]

// Añadir
arr.push(4)        // al final
arr.unshift(0)     // al inicio

// Eliminar
arr.pop()           // último
arr.shift()         // primero

// Buscar y modificar
arr.splice(1, 1, 99)  // remove 1 at index 1, add 99

// Ordenar
arr.sort((a, b) => a - b)
arr.reverse()

// flatten
[[1,2], [3,4]].flat()  // [1,2,3,4]
```

## Destructuring

```javascript
const [a, b, ...rest] = [1, 2, 3, 4, 5]
// a=1, b=2, rest=[3,4,5]
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]