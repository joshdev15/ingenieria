#development #go

Declaracion y uso de variables en Go.

## Formas de Declaracion

```go
// 1. Solo declaracion
var nombre string

// 2. Declaracion e inicializacion
var nombre string = "Go"

// 3. Inferencia de tipo (shortcut)
nombre := "Go"
```

## Tipos Compuestos

### Arrays (tamano fijo)
```go
var arr [50]string
arr2 := [25]byte{}
```

### Slices (tamano dinamico)
```go
var slice []string
slice2 := make([]int, 10)
```

### Maps (diccionario)
```go
var mapa map[string]string
mapa2 := make(map[string]int)
```

## Structs

```go
type Persona struct {
    Nombre string
    Edad   int
}

p := Persona{Nombre: "Juan", Edad: 25}
```

## Interfaces

```go
type Runner interface {
    Run()
}

func startRunning(r Runner) {
    r.Run()
}
```

## Canales

```go
ch := make(chan int)
ch <- 10      // Enviar
valor := <-ch // Recibir
```

[[Desarrollo de Software/Lenguajes/Go/Go.md]]