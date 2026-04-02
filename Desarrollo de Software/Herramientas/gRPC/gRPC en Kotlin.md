#development #grpc #kotlin

Implementar gRPC en Kotlin/JVM.

## Dependencias

```kotlin
// build.gradle.kts
plugins {
    id("com.google.protobuf") version "0.9.4"
    id("io.grpc.kotlin") version "1.4.0"
}

dependencies {
    implementation("io.grpc:grpc-core:1.58.0")
    implementation("io.grpc:grpc-okhttp:1.58.0")
    implementation("io.grpc:grpc-protobuf:1.58.0")
    implementation("io.grpc:grpc-kotlin-stub:1.4.0")
    implementation("com.google.protobuf:protobuf-kotlin:3.24.4")
}
```

## Archivo .proto

```protobuf
syntax = "proto3";

package com.ejemplo;

option java_package = "com.ejemplo.grpc";
option java_multiple_files = true;

service UsuarioService {
    rpc getUsuario(UsuarioRequest) returns (Usuario);
    rpc getUsuarios(UsuarioRequest) returns (stream Usuario);
    rpc crearUsuario(Usuario) returns (Usuario);
    rpc chat(stream Usuario) returns (stream Usuario);
}

message Usuario {
    string id = 1;
    string nombre = 2;
    string email = 3;
    int32 edad = 4;
}

message UsuarioRequest {
    string id = 1;
}
```

## Generar Código

```bash
./gradlew generateProto
```

## Servidor

```kotlin
class UsuarioServiceImpl : UsuarioServiceCoroutineImplBase() {
    
    override suspend fun getUsuario(request: UsuarioRequest): Usuario {
        return Usuario.newBuilder()
            .setId(request.id)
            .setNombre("Juan")
            .setEmail("juan@email.com")
            .setEdad(30)
            .build()
    }
    
    override fun getUsuarios(request: UsuarioRequest, responder: StreamObserver<Usuario>) {
        val usuarios = listOf(
            Usuario.newBuilder().setId("1").setNombre("Juan").build(),
            Usuario.newBuilder().setId("2").setNombre("Maria").build()
        )
        
        usuarios.forEach { responder.onNext(it) }
        responder.onCompleted()
    }
}

fun main() {
    val server = ServerBuilder.forPort(50051)
        .addService(UsuarioServiceImpl())
        .build()
    
    server.start()
    server.awaitTermination()
}
```

## Cliente

```kotlin
class GrpcClient(private val channel: ManagedChannel) {
    
    private val stub: UsuarioServiceCoroutineStub by lazy {
        UsuarioServiceCoroutineStub(channel)
    }
    
    suspend fun getUsuario(id: String): Usuario {
        return stub.getUsuario(UsuarioRequest.newBuilder().setId(id).build())
    }
    
    suspend fun getUsuarios(limite: Int): List<Usuario> {
        val request = UsuarioRequest.newBuilder().setId("$limite").build()
        return stub.getUsuarios(request).toList()
    }
}

suspend fun main() {
    val channel = ManagedChannelBuilder.forAddress("localhost", 50051)
        .usePlaintext()
        .build()
    
    val client = GrpcClient(channel)
    val usuario = client.getUsuario("1")
    println(usuario)
    
    channel.shutdownNow()
}
```

## Android

```kotlin
// build.gradle.kts (Android)
dependencies {
    implementation("io.grpc:grpc-okhttp:1.58.0")
    implementation("io.grpc:grpc-android:1.58.0")
}

// Uso en Android (usar con Dispatchers.IO)
suspend fun getUsuario(id: String): Usuario {
    return withContext(Dispatchers.IO) {
        stub.getUsuario(UsuarioRequest.newBuilder().setId(id).build())
    }
}
```

## Spring gRPC

```kotlin
// build.gradle.kts
implementation("net.devh:grpc-spring-boot-starter:2.15.1")

// Application
@GrpcService
class UsuarioGrpcService : UsuarioServiceImplBase() {
    override fun getUsuario(request: UsuarioRequest, observer: StreamObserver<Usuario>) {
        val usuario = Usuario.newBuilder()
            .setId(request.id)
            .setNombre("Juan")
            .build()
        observer.onNext(usuario)
        observer.onCompleted()
    }
}
```

[[Desarrollo de Software/Herramientas/gRPC/gRPC.md]]
