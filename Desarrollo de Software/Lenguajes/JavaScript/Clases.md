#development #javascript

ES6 introduced sintaxis de clases para herencia prototípica.

## Definir Clase

```javascript
class Persona {
    // Constructor
    constructor(nombre, edad) {
        this.nombre = nombre
        this.edad = edad
    }

    // Método
    saludar() {
        return `Hola, soy ${this.nombre}`
    }

    // Getter
    get mayorDeEdad() {
        return this.edad >= 18
    }

    // Setter
    set edad(value) {
        if (value > 0) this._edad = value
    }
}
```

## Herencia

```javascript
class Desarrollador extends Persona {
    constructor(nombre, edad, lenguaje) {
        super(nombre, edad)
        this.lenguaje = lenguaje
    }

    saludar() {
        return `${super.saludar()} y programo en ${this.lenguaje}`
    }
}

const dev = new Desarrollador("Juan", 25, "JavaScript")
```

## Métodos Estáticos

```javascript
class Util {
    static saludar(nombre) {
        return `Hola, ${nombre}`
    }
}
Util.saludar("Juan")  // sin instanciar
```

## Private Fields (ES2022)

```javascript
class Cuenta {
    #saldo = 0

    #mostrarSaldo() {
        return this.#saldo
    }

    get saldo() {
        return this.#mostrarSaldo()
    }
}
```

[[Desarrollo de Software/Lenguajes/JavaScript/JavaScript.md]]