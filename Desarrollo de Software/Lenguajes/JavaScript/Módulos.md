#development #javascript

Los módulos organizan el código en unidades reutilizables.

## CommonJS (Node.js)

```javascript
// math.js
module.exports = {
    suma: (a, b) => a + b,
    resta: (a, b) => a - b
}

// main.js
const math = require('./math')
console.log(math.suma(2, 3))
```

## ES6 Modules (moderno)

```javascript
// math.js
export const suma = (a, b) => a + b
export const resta = (a, b) => a - b
export default class Calculadora {}

// main.js
import Calculadora, { suma, resta } from './math'
console.log(suma(2, 3))
```

## Dynamic Imports

```javascript
// Carga bajo demanda
const modulo = await import('./modulo.js')
modulo.default()
```

## Namespace Pattern

```javascript
const App = {}
App.utils = {
    suma: (a, b) => a + b
}
App.config = { apiUrl: '...' }
```

## Export Variations

```javascript
// Named exports
export const PI = 3.14159
export function saludar() {}

// Default export
export default class Config {}

// Aggregate exports
export * from './math'
export { suma, resta } from './math'
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]
