#engineering #uml #system-design

El diagrama de paquetes organiza los elementos del modelo en grupos (paquetes) para gestionar la complejidad del sistema.

## Cuándo Usarlo

- Organizar grandes sistemas en módulos
- Mostrar la estructura de namespaces/packages
- Definir dependencias entre módulos
- Facilitar la división del trabajo en equipo

## Ejemplo: Estructura de Proyecto Go

```
┌─────────────────────────────────────────────────────────────────┐
│                        myapp (Root Package)                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌───────────────────┐  ┌───────────────────┐  ┌────────────────┐ │
│  │     cmd/          │  │     internal/    │  │    vendor/     │ │
│  │  ┌─────────────┐  │  │  ┌─────────────┐  │  │  (deps)       │ │
│  │  │   api       │  │  │  │  domain/    │  │  │              │ │
│  │  │   server   │  │  │  │  ─── user   │  │  │              │ │
│  │  └─────────────┘  │  │  │  ─── order  │  │  │              │ │
│  │  ┌─────────────┐  │  │  ├─────────────┤  │  │              │ │
│  │  │   cli      │  │  │  │   infra/    │  │  │              │ │
│  │  └─────────────┘  │  │  │  ─── repo   │  │  │              │ │
│  └───────────────────┘  │  │  ─── cache  │  │  │              │ │
│                         │  ├─────────────┤  │  │              │ │
│                         │  │   api/      │  │  │              │ │
│                         │  │  ─── handler│  │  │              │ │
│                         │  │  ─── dto    │  │  │              │ │
│                         │  └─────────────┘  │  │              │ │
│                         └───────────────────┘  └────────────────┘ │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

## Ejemplo: Paquetes Kotlin/Spring

```
┌─────────────────────────────────────────────────────┐
│                    com.myapp                         │
├─────────────────────────────────────────────────────┤
│                                                      │
│  ┌────────────────────┐    ┌────────────────────┐   │
│  │    config/         │    │    controller/     │   │
│  │  - AppConfig       │    │  - UserController │   │
│  │  - DatabaseConfig  │    │  - OrderController│   │
│  └────────────────────┘    └─────────┬──────────┘   │
│                                       │              │
│  ┌────────────────────┐               │              │
│  │    service/       │◄──────────────┘              │
│  │  - UserService    │                             │
│  │  - OrderService   │                             │
│  └─────────┬──────────┘                             │
│            │                                        │
│  ┌─────────▼──────────┐    ┌────────────────────┐   │
│  │    repository/    │    │    model/          │   │
│  │  - UserRepo       │    │  - User            │   │
│  │  - OrderRepo      │    │  - Order           │   │
│  └───────────────────┘    └────────────────────┘   │
│                                                      │
└──────────────────────────────────────────────────────┘
```

## Dependencias entre Paquetes

```
┌─────────────┐       ┌─────────────┐
│  package A  │       │  package B  │
│             │───────│             │
│  (domain)   │       │ (infraest.) │
└─────────────┘       └─────────────┘
        │                     ▲
        │                     │
        └─────────┬───────────┘
                  ▼
          ┌─────────────┐
          │  package C  │
          │ (application)│
          └─────────────┘
```

## Notación

| Elemento | Descripción |
|----------|-------------|
| Carpeta grande | Paquete |
| Flecha | Dependencia |
| ++ | Elemento público |
| - | Elemento privado |

[[index|← Volver a Estructurales]]