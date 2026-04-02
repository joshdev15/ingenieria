#development #javascript

Declaración de variables y constantes en JavaScript.

## var (legacy)

```javascript
var nombre = "Juan"       // Variables con alcance de función
var edad = 25
```

**Problemas:**
- No tiene alcance de bloque
- Se puede redeclarar
- Hoisting automático

## let (ES6)

```javascript
let nombre = "Juan"        // Variables con alcance de bloque
let edad = 25

edad = 30                  // Redeclaración no permitida
```

## const (ES6)

```javascript
const PI = 3.14159
const persona = { nombre: "Juan" }

persona.edad = 30         // Mutación permitida
// persona = {}           // Error: asignación no permitida
```

## Diferencias

| Característica | var | let | const |
|----------------|-----|-----|--------|
| Alcance función | ✅ | ❌ | ❌ |
| Alcance bloque | ❌ | ✅ | ✅ |
| Redeclarar | ✅ | ❌ | ❌ |
| Hoisting | ✅ | ❌ | ❌ |

## Best Practices

```javascript
// ✅ Usar const por defecto
// ✅ Usar let si necesita reasignar
// ❌ Evitar var
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]