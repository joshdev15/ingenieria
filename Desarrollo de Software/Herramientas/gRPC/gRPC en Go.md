#development #grpc #go

Implementar gRPC en Go.

## Instalación

```bash
# Instalar protoc
brew install protobuf

# Instalar generadores
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.31.0
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.3.0

# Dependencias
go get google.golang.org/grpc
go get google.golang.org/protobuf
```

## Archivo .proto

```protobuf
syntax = "proto3";

package pb;

option go_package = "github.com/usuario/proyecto/pb";

import "google/protobuf/timestamp.proto";

service UsuarioService {
    rpc GetUsuario(GetUsuarioRequest) returns (Usuario);
    rpc GetUsuarios(GetUsuariosRequest) returns (stream Usuario);
    rpc CrearUsuario(Usuario) returns (Usuario);
    rpc Chat(stream Usuario) returns (stream Usuario);
}

message Usuario {
    string id = 1;
    string nombre = 2;
    string email = 3;
    int32 edad = 4;
    google.protobuf.Timestamp creado_en = 5;
}

message GetUsuarioRequest {
    string id = 1;
}

message GetUsuariosRequest {
    int32 limite = 1;
}
```

## Generar Código

```bash
protoc --go_out=. --go_opt=paths=source_relative \
    --go-grpc_out=. --go-grpc_opt=paths=source_relative \
    proto/usuario.proto
```

## Servidor

```go
package main

import (
    "context"
    "net"
    
    "google.golang.org/grpc"
    "google.golang.org/protobuf/types/known/timestamppb"
    
    pb "github.com/usuario/proyecto/pb"
)

type server struct {
    pb.UnimplementedUsuarioServiceServer
}

func (s *server) GetUsuario(ctx context.Context, req *pb.GetUsuarioRequest) (*pb.Usuario, error) {
    return &pb.Usuario{
        Id:        req.Id,
        Nombre:    "Juan",
        Email:     "juan@email.com",
        Edad:      30,
        CreadoEn:  timestamppb.Now(),
    }, nil
}

func (s *server) GetUsuarios(req *pb.GetUsuariosRequest, stream pb.UsuarioService_GetUsuariosServer) error {
    usuarios := []*pb.Usuario{
        {Id: "1", Nombre: "Juan", Email: "juan@email.com"},
        {Id: "2", Nombre: "Maria", Email: "maria@email.com"},
    }
    
    for _, u := range usuarios {
        if err := stream.Send(u); err != nil {
            return err
        }
    }
    return nil
}

func main() {
    lis, _ := net.Listen("tcp", ":50051")
    s := grpc.NewServer()
    pb.RegisterUsuarioServiceServer(s, &server{})
    s.Serve(lis)
}
```

## Cliente

```go
package main

import (
    "context"
    "fmt"
    
    "google.golang.org/grpc"
    "google.golang.org/grpc/credentials/insecure"
    
    pb "github.com/usuario/proyecto/pb"
)

func main() {
    conn, _ := grpc.Dial("localhost:50051", grpc.WithTransportCredentials(insecure.NewCredentials()))
    defer conn.Close()
    
    client := pb.NewUsuarioServiceClient(conn)
    
    // Unary
    resp, _ := client.GetUsuario(context.Background(), &pb.GetUsuarioRequest{Id: "1"})
    fmt.Println(resp)
    
    // Server Streaming
    stream, _ := client.GetUsuarios(context.Background(), &pb.GetUsuariosRequest{Limite: 10})
    for {
        u, err := stream.Recv()
        if err != nil {
            break
        }
        fmt.Println(u)
    }
}
```

## Interceptors

```go
// Server interceptor
func loggingInterceptor(srv interface{}, ss grpc.ServerStream, info *grpc.StreamServerInfo, handler grpc.StreamHandler) error {
    fmt.Println("Llamada:", info.FullMethodName)
    return handler(srv, ss)
}

// Client interceptor
func authInterceptor(ctx context.Context, method string, req, reply interface{}, cc *grpc.ClientConn, invoker grpc.UnaryInvoker, opts ...grpc.CallOption) error {
    ctx = metadata.NewOutgoingContext(ctx, metadata.Pairs("authorization", "Bearer token"))
    return invoker(ctx, method, req, reply, cc, opts...)
}
```

[[Desarrollo de Software/Herramientas/gRPC/gRPC.md]]
