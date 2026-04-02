#architecture #api

El diseño de APIs es fundamental para la comunicación entre sistemas.

## REST (Representational State Transfer)

### Principios
- Recursos identificados por URLs
- Uso de métodos HTTP (GET, POST, PUT, DELETE)
- Estado representado en JSON o XML
- Sin estado (cada solicitud es independiente)

### Mejores Prácticas

| Práctica | Descripción |
|----------|-------------|
| **Nombres resource** | Usar sustantivos, plural: `/users`, `/orders` |
| **Verbos HTTP** | GET=leer, POST=crear, PUT=actualizar, DELETE=eliminar |
| **Códigos de estado** | 200=OK, 201=Creado, 400=Bad Request, 404=No encontrado, 500=Error |
| **Versionado** | `/api/v1/users` |
| **Pagination** | `?page=1&limit=10` |

### Ejemplo REST (Go)

```go
// GET /api/v1/users/123
// Response:
type UserResponse struct {
    ID        string    `json:"id"`
    Name      string    `json:"name"`
    Email     string    `json:"email"`
    CreatedAt time.Time `json:"created_at"`
}

// Handler en Go con Gin
func GetUser(c *gin.Context) {
    id := c.Param("id")
    user, err := userService.FindByID(id)
    if err != nil {
        c.JSON(404, gin.H{"error": "User not found"})
        return
    }
    c.JSON(200, user)
}

func CreateUser(c *gin.Context) {
    var req CreateUserRequest
    if err := c.ShouldBindJSON(&req); err != nil {
        c.JSON(400, gin.H{"error": err.Error()})
        return
    }
    user, err := userService.Create(req.Name, req.Email)
    if err != nil {
        c.JSON(500, gin.H{"error": "Internal error"})
        return
    }
    c.JSON(201, user)
}
```

### Ejemplo REST (Kotlin con Spring)

```kotlin
@RestController
@RequestMapping("/api/v1/users")
class UserController(
    private val userService: UserService
) {
    @GetMapping("/{id}")
    fun getUser(@PathVariable id: String): ResponseEntity<UserResponse> {
        return userService.findById(id)
            ?.let { ResponseEntity.ok(it) }
            ?: ResponseEntity.notFound().build()
    }
    
    @PostMapping
    fun createUser(@RequestBody request: CreateUserRequest): ResponseEntity<UserResponse> {
        val user = userService.create(request.name, request.email)
        return ResponseEntity.status(201).body(user)
    }
}
```

## GraphQL

Lenguaje de consulta para APIs.

### Características
- Un solo endpoint
- El cliente especifica exactamente qué datos necesita
- Typed schema

```graphql
type User {
  id: ID!
  name: String!
  email: String!
}

type Query {
  user(id: ID!): User
  users: [User!]!
}

type Mutation {
  createUser(name: String!, email: String!): User!
}
```

## gRPC

Remote Procedure Call con Protocol Buffers.

### Ventajas
- Rápido y eficiente
- Tipado fuerte
- Streaming bidireccional

```protobuf
message User {
  string id = 1;
  string name = 2;
  string email = 3;
}

service UserService {
  rpc GetUser (UserRequest) returns (User);
  rpc CreateUser (User) returns (User);
}
```

## GraphQL vs REST vs gRPC

| Característica | REST | GraphQL | gRPC |
|----------------|------|---------|------|
| Flexibilidad | Baja | Alta | Alta |
| Performance | Regular | Buena | Excelente |
| Curva aprendizaje | Baja | Media | Alta |
| Typed schema | No | Opcional | Sí |

## Documentación

- OpenAPI/Swagger para REST
- GraphQL Schema para GraphQL
- Protocol Buffers para gRPC

[[Arquitectura de Software]]