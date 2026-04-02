#development #grpc

gRPC (Google Remote Procedure Call) es un framework de comunicación entre servicios.

## Arquitectura

```
Cliente → gRPC → Red (HTTP/2) → gRPC → Servidor
```

## Tipos de Comunicación

### Unary (request-response)
```protobuf
rpc GetUsuario(UsuarioRequest) returns (Usuario);
```

### Server Streaming
```protobuf
rpc GetUsuarios(UsuarioRequest) returns (stream Usuario);
```

### Client Streaming
```protobuf
rpc SubirArchivos(stream Archivo) returns (UploadResponse);
```

### Bidirectional Streaming
```protobuf
rpc Chat(stream Mensaje) returns (stream Mensaje);
```

## HTTP/2

| Característica | Descripción |
|----------------|-------------|
| Multiplexing | Múltiples requests en una conexión |
| Header Compression | HPACK |
| Binary Framing | Binario en lugar de texto |
| Server Push | Enviar múltiples recursos |

## Comparación REST vs gRPC

| Aspecto | REST | gRPC |
|---------|------|------|
| Formato | JSON | Protobuf |
| Tamaño | Grande | Pequeño |
| Velocidad | Más lento | Más rápido |
| Typing | Dinámico | Fuertes |
| Streaming | Limited | Nativo |
| browser support | ✅ | ❌ (solo grpc-web) |

## Metadata

```protobuf
service MiServicio {
    rpc GetData(Request) returns (Response) {
        option (google.api.http) = {
            get: "/v1/data"
        };
    };
}
```

## Errores

| Código | Descripción |
|--------|-------------|
| OK | Éxito |
| NOT_FOUND | No encontrado |
| INVALID_ARGUMENT | Argumento inválido |
| UNAUTHENTICATED | Sin autenticación |
| UNAUTHORIZED | No autorizado |
| INTERNAL | Error interno |
| UNAVAILABLE | Servicio no disponible |

[[Desarrollo de Software/Herramientas/gRPC/gRPC.md]]
