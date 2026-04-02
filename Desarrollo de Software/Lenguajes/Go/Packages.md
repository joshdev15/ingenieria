#development #go

Los paquetes organizan el codigo en Go.

## Paquetes Estandar

| Paquete | Descripcion |
|---------|-------------|
| `fmt` | E/S formateada (como printf) |
| `math` | Operaciones matematicas |
| `http` | Protocolo HTTP |
| `json` | Codificacion/decodificacion JSON |
| `errors` | Manejo de errores |

## Paquetes Personalizados

```go
// Carpeta: action/action.go
package action

func Run() {
    println("Action Run")
}
```

```go
// main.go
package main
import "app/action"

func main() {
    action.Run()
}
```

## Reglas

1. El paquete `main` es el punto de entrada
2. Cada archivo pertenece a un paquete
3. El nombre del paquete debe coincidir con la carpeta

[[Desarrollo de Software/Lenguajes/Go/Go.md]]