#development #grpc #protobuf

Protocol Buffers (protobuf) es el formato de serialización de datos de Google.

## Sintaxis

```protobuf
syntax = "proto3";

package ejemplo;

option go_package = "github.com/usuario/proyecto/pb";

message Usuario {
    string id = 1;
    string nombre = 2;
    string email = 3;
    int32 edad = 4;
    bool activo = 5;
    repeated string telefonos = 6;
    map<string, string> direcciones = 7;
}

message Request {
    string query = 1;
}
```

## Tipos de Datos

| Proto | Go | Kotlin | Descripción |
|-------|-----|---------|-------------|
| `int32` | `int32` | `Int` | Entero |
| `int64` | `int64` | `Long` | Entero 64 bits |
| `float` | `float32` | `Float` | Punto flotante |
| `double` | `float64` | `Double` | Punto flotante 64 |
| `string` | `string` | `String` | Texto |
| `bytes` | `[]byte` | `ByteString` | Datos binarios |
| `bool` | `bool` | `Boolean` | Booleano |

## Tipos Avanzados

### Enum
```protobuf
enum Estado {
    ACTIVO = 0;
    INACTIVO = 1;
    PENDIENTE = 2;
}

message Cuenta {
    Estado estado = 1;
}
```

### Nested Messages
```protobuf
message Persona {
    message Direccion {
        string calle = 1;
        string ciudad = 2;
    }
    
    Direccion direccion = 1;
}
```

### Oneof
```protobuf
message Respuesta {
    oneof contenido {
        string texto = 1;
        bytes binario = 2;
    }
}
```

## Imports

```protobuf
import "google/protobuf/timestamp.proto";
import "google/protobuf/empty.proto";

message Evento {
    google.protobuf.Timestamp fecha = 1;
}
```

## Well-Known Types

```protobuf
import "google/protobuf/any.proto";
import "google/protobuf/duration.proto";

message Mensaje {
    google.protobuf.Any contenido = 1;
    google.protobuf.Duration duracion = 2;
}
```

## Compilar

```bash
# Instalar compiler
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.31.0
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.3.0

# Compilar (Go)
protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    proto/usuario.proto

# Compilar (Kotlin)
protoc --kotlin_out=. --kotlingrpc_out=. proto/usuario.proto
```

## JSON vs Protobuf

```json
// JSON (52 bytes)
{
    "id": "1",
    "nombre": "Juan",
    "email": "juan@email.com",
    "edad": 30
}

// Protobuf (~15 bytes)
[08 01 12 04 4a 75 61 6e 1a 10 6a 75 61 6e 40 3e]
```

[[Desarrollo de Software/Herramientas/gRPC/gRPC.md]]
