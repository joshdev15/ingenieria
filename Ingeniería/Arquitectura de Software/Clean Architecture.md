#architecture #clean

Clean Architecture es un conjunto de principios para estructurar software con separación de preocupaciones.

## Capas

```
┌─────────────────────────────────────────────┐
│           Presentation / API                │  ← Controllers, DTOs
├─────────────────────────────────────────────┤
│              Application                    │  ← Use Cases, DTOs
├─────────────────────────────────────────────┤
│                 Domain                       │  ← Entities, Interfaces
├─────────────────────────────────────────────┤
│              Infrastructure                 │  ← Repositories, Services
└─────────────────────────────────────────────┘
```

## Reglas de Dependencia

- Las dependencias apuntan hacia adentro
- El dominio no conoce nada de otras capas
- Las capas externas dependen de las internas

## Domain Layer (Núcleo) - Go

```go
// Entity
type User struct {
    ID    string
    Email string
    Name  string
}

// Interface (Puerto)
type UserRepository interface {
    Save(user User) error
    FindByID(id string) (User, error)
}
```

## Application Layer (Casos de Uso) - Go

```go
type CreateUserUseCase struct {
    repository UserRepository
}

func (c *CreateUserUseCase) Execute(email, name string) (User, error) {
    user := User{
        ID:    generateID(),
        Email: email,
        Name:  name,
    }
    return user, c.repository.Save(user)
}
```

## Infrastructure Layer (Adaptadores) - Go

```go
type UserRepositoryImpl struct {
    db *sql.DB
}

func (r *UserRepositoryImpl) Save(user User) error {
    _, err := r.db.Exec(
        "INSERT INTO users (id, email, name) VALUES (?, ?, ?)",
        user.ID, user.Email, user.Name,
    )
    return err
}
```

## Presentation Layer - Kotlin

```kotlin
@RestController
class UserController(
    private val createUserUseCase: CreateUserUseCase
) {
    @PostMapping("/users")
    fun create(@RequestBody request: CreateUserRequest): User {
        return createUserUseCase.execute(request.email, request.name)
    }
}
```

## Beneficios

- **Testabilidad**: Cada capa se puede probar independientemente
- **Independencia de frameworks**: El dominio no depende de bibliotecas
- **Independencia de UI**: La lógica es agnóstica a cómo se presenta
- **Independencia de DB**: Se puede cambiar la base de datos sin afectar la lógica

## Principios SOLID Aplicados

- **SRP**: Cada clase tiene una responsabilidad
- **OCP**: Abierto para extender, cerrado para modificar
- **LSP**: Las subclases son sustituibles
- **ISP**: Interfaces pequeñas y específicas
- **DIP**: Depender de abstracciones, no de concreciones

[[Ingeniería/Arquitectura de Software/Arquitectura de Software.md]]
[[Ingeniería/Arquitectura de Software/Patrones Arquitectónicos.md]]