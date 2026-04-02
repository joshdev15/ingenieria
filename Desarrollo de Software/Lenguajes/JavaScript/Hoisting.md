#development #javascript

Hoisting es el comportamiento de mover declaraciones al inicio del ámbito antes de ejecutar el código.

## var (Hoisting)

```javascript
console.log(nombre)  // undefined (no error)
var nombre = "Juan"
console.log(nombre) // "Juan"

// Equivalente a:
var nombre           //声明提前
console.log(nombre) // undefined
var nombre = "Juan"
```

## let y const (Temporal Dead Zone)

```javascript
console.log(nombre)  // ReferenceError!
let nombre = "Juan"

// El período entre el inicio del ámbito y la declaración se llama "Temporal Dead Zone"
```

## function (Hoisting completo)

```javascript
saludar()  // "Hola!"

function saludar() {
    return "Hola!"
}

// Las funciones se hoistean completamente
```

## const con funciones

```javascript
const saludar = function() {
    return "Hola!"
}
saludar()  // OK - la variable se hoistea como undefined

// const saludar = function() {...}
// Equivalente a:
var saludar
console.log(saludar)  // undefined
saludar = function() { return "Hola!" }
```

## Ejemplos Prácticos

```javascript
// Problema común
for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100)
}
// Output: 3, 3, 3 (var no tiene ámbito de bloque)

// Solución con let
for (let i = 0; i < 3; i++) {
    setTimeout(() => console.log(i), 100)
}
// Output: 0, 1, 2 (let tiene ámbito de bloque)
```

## Best Practices

```javascript
// ✅ Siempre declarar variables al inicio del ámbito
// ✅ Preferir let/const sobre var
// ✅ Usar funciones flecha para evitar problemas con 'this'
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]
