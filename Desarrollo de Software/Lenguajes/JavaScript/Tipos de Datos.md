#development #javascript

JavaScript tiene tipos de datos primitivos y objetos.

## Primitivos

| Tipo | Ejemplo |
|------|---------|
| `string` | `"Hola"` |
| `number` | `42`, `3.14` |
| `boolean` | `true`, `false` |
| `undefined` | `undefined` |
| `null` | `null` |
| `symbol` | `Symbol("id")` |
| `bigint` | `9007199254740991n` |

## Objetos

```javascript
// Arrays
const arr = [1, 2, 3]

// Objetos
const persona = {
    nombre: "Juan",
    edad: 30
}

// Funciones
function saludar() {}
```

## Verificar Tipos

```javascript
typeof "Hola"       // "string"
typeof 42           // "number"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" (bug histórico)
typeof {}           // "object"
typeof []           // "object"
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]