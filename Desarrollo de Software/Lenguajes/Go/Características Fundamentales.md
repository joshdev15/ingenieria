#development #go

Go es un lenguaje de proposito general con las siguientes caracteristicas:

## Características Generales

| Característica | Descripcion |
|----------------|-------------|
| **Simplicidad** | Sintaxis clara similar a C, facil de aprender |
| **Eficiencia** | Compilado a codigo maquina, muy rapido |
| **Concurrencia** | Soporte nativo para multiples tareas |
| **Escalabilidad** | Ideal para aplicaciones empresariales |
| **Robustez** | Biblioteca estandar completa y comunidad activa |

## Características Tecnicas

- **Tipos Estaticos**: Lenguaje fuertemente tipado
- **Recoleccion de Basura**: Gestion automatica de memoria
- **Seguridad**: Comprobacion de tipos en tiempo de ejecucion

## Características Modernas (Go 1.18+)

### alias `any` para `interface{}`

A partir de Go 1.18, `any` es un alias para el tipo vacio `interface{}`, que representa cualquier tipo.

```go
// Antes (valido pero anticuado)
var valor interface{} = "hola"

// Moderno (Go 1.18+)
var valor any = "hola"

// Uso en funciones
func procesar(dato any) {
    // ...
}
```

### Genericos (Generics)

Los genericos permiten escribir codigo reusable con diferentes tipos sin perder type safety.

```go
// Funcion generica con type parameters
func Sum[T int | float64](nums []T) T {
    var total T
    for _, n := range nums {
        total += n
    }
    return total
}

// Uso
resultado := Sum([]int{1, 2, 3})           // resultado: 6
resultadoFloat := Sum([]float64{1.5, 2.5}) // resultado: 4.0
```

#### Constraints

```go
// Define un constraint personalizado
type Number interface {
    int | int32 | float64 | float32
}

// Generic con constraint
func Double[T Number](value T) T {
    return value + value
}
```

#### Generic Types

```go
// Define un tipo generico
type Stack[T any] struct {
    items []T
}

func (s *Stack[T]) Push(item T) {
    s.items = append(s.items, item)
}

func (s *Stack[T]) Pop() T {
    last := s.items[len(s.items)-1]
    s.items = s.items[:len(s.items)-1]
    return last
}
```

[[Desarrollo de Software/Lenguajes/Go/Go.md]]