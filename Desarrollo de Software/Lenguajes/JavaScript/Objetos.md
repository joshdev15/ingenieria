#development #javascript

Los objetos son colecciones de propiedades clave-valor.

## Crear Objetos

```javascript
// Literales
const persona = {
    nombre: "Juan",
    edad: 30,
    saludar() {
        return `Hola, soy ${this.nombre}`
    }
}

// Constructor
function Persona(nombre, edad) {
    this.nombre = nombre
    this.edad = edad
}
Persona.prototype.saludar = function() {
    return `Hola, soy ${this.nombre}`
}

// Object.create
const persona = Object.create(null)
```

## Acceso a Propiedades

```javascript
const persona = { nombre: "Juan", edad: 30 }

// Notación punto
persona.nombre

// Notación corchetes
persona["nombre"]

// Destructuring
const { nombre, edad } = persona
```

## Métodos Útiles

```javascript
const persona = { nombre: "Juan", edad: 30 }

// Keys, values, entries
Object.keys(persona)    // ["nombre", "edad"]
Object.values(persona)  // ["Juan", 30]
Object.entries(persona) // [[<- Volver a "nombre", "Juan"], ["edad", 30]]

// Merge
const merged = { ...persona, ciudad: "Madrid" }

// Freeze (inmutable)
Object.freeze(persona)
```

## this

```javascript
const persona = {
    nombre: "Juan",
    saludar() {
        // 'this' referencia al objeto
        return `Hola, soy ${this.nombre}`
    }
}

// Call, Apply, Bind
const saludar = function() {
    return `Hola, soy ${this.nombre}`
}
saludar.call({ nombre: "Pedro" })
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]