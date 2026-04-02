#development #javascript

Las funciones en JavaScript son ciudadanos de primera clase.

## Declaración

```javascript
// Función tradicional
function saludar(nombre) {
    return `Hola, ${nombre}!`
}

// Función expresión
const saludar = function(nombre) {
    return `Hola, ${nombre}!`
}

// Arrow function
const saludar = (nombre) => `Hola, ${nombre}!`

// Arrow function con cuerpo
const saludar = (nombre) => {
    const mensaje = `Hola, ${nombre}!`
    return mensaje
}
```

## Parámetros

```javascript
// Parámetros por defecto
function greet(nombre = "Usuario") {
    return `Hola, ${nombre}`
}

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0)
}

// Destructuring en parámetros
function config({ host, port }) {
    console.log(host, port)
}
```

## Higher-Order Functions

```javascript
// Función que retorna función
const crearMultiplier = (factor) => (x) => x * factor

// Función que recibe función
const nums = [1, 2, 3, 4]
const doubled = nums.map(n => n * 2)
```

## this en Funciones

```javascript
// Regular function - this cambia
function Persona() {
    this.edad = 0
    setInterval(function() {
        this.edad++  // 'this' no es Persona
    }, 1000)
}

// Arrow function - this se mantiene
function Persona() {
    this.edad = 0
    setInterval(() => {
        this.edad++  // 'this' es Persona
    }, 1000)
}
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]