#development #kotlin

Palabras reservadas en Kotlin (no pueden usarse como identificadores).

## Modificadores

| Keyword | Descripción |
|---------|-------------|
| `public` | Accesible desde cualquier lugar |
| `private` | Accesible solo en la clase |
| `protected` | Accesible en clase y subclases |
| `internal` | Accesible en el mismo módulo |
| `open` | Permite herencia |
| `final` | No permite herencia |
| `abstract` | Clase sin implementación |
| `sealed` | Clase con herencia restringida |
| `data` | Genera métodos automáticos |
| `lateinit` | Inicialización diferida |
| `override` | Sobreescribe miembro |
| `companion` | Objeto compañero estático |
| `init` | Bloque de inicialización |
| `by` | Delegación de propiedad |
| `inline` | Función en línea |
| `noinline` | Evita inline de lambda |
| `crossinline` | Lambda sin return no-local |
| `reified` | Tipo genérico en tiempo de ejecución |
| `suspend` | Función coroutine |

## Declaraciones

| Keyword | Descripción |
|---------|-------------|
| `class` | Define una clase |
| `interface` | Define una interfaz |
| `object` | Define un singleton |
| `data class` | Clase con métodos automáticos |
| `sealed class` | Clase restringida |
| `enum class` | Enumeración |
| `annotation class` | Definición de anotación |
| `fun` | Define una función |
| `val` | Variable inmutable |
| `var` | Variable mutable |
| `typealias` | Alias de tipo |
| `typedef` | Alias de tipo |

## Control de Flujo

| Keyword | Descripción |
|---------|-------------|
| `if` | Condicional |
| `else` | Alternativa |
| `when` | Selección múltiple (como switch) |
| `for` | Bucle |
| `while` | Bucle condicion |
| `do-while` | Bucle post-condición |
| `return` | Devuelve valor |
| `break` | Sale de bucle |
| `continue` | siguiente iteración |

## Nulidad

| Keyword | Descripción |
|---------|-------------|
| `?` | Tipo nullable |
| `?.` | Safe call |
| `?:` | Elvis operator |
| `!!` | Not null assertion |
| `as?` | Safe cast |

## Otros

| Keyword | Descripción |
|---------|-------------|
| `import` | Importa paquetes |
| `package` | Define paquete |
| `is` | Verifica tipo |
| `in` | Pertenece a rango/colección |
| `out` | Covarianza genérica |
| `where` | Restricciones genéricas |
| `try` | Manejo de excepciones |
| `catch` | Captura excepción |
| `finally` | Bloque siempre ejecutado |
| `throw` | Lanza excepción |

[[Desarrollo de Software/Lenguajes/Kotlin/Kotlin.md]]
