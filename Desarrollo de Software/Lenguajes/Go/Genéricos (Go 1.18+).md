#development #go

Los genericos fueron introducidos en Go 1.18 (2022), permitiendo escribir codigo reutilizable con tipos genericos.

## Type Parameters

```go
func GenericFunc[T any](param T) T {
    return param
}
```

## Constraints

Los constraints limitan los tipos que pueden usarse con un parametro generico.

### Union Types

```go
func Sum[T int | float64](nums []T) T { ... }
```

### Interface como Constraint

```go
type Number interface {
    ~int | ~float64 | ~int32
}

func Double[T Number](n T) T {
    return n + n
}
```

## Generic Types

```go
type Pair[K any, V any] struct {
    Key K
    Value V
}
```

## Maps y Slices Genericos

```go
keys := []string{"a", "b", "c"}
values := []int{1, 2, 3}

// zip con genericos
func Zip[K any, V any](keys []K, values []V) map[K]V {
    result := make(map[K]V)
    for i := range keys {
        result[keys[i]] = values[i]
    }
    return result
}
```

## Ejemplo: funcion PrintSlice

```go
func PrintSlice[T any](items []T) {
    for i, item := range items {
        fmt.Printf("%d: %v\n", i, item)
    }
}
```

[[Desarrollo de Software/Lenguajes/Go/Go.md]]