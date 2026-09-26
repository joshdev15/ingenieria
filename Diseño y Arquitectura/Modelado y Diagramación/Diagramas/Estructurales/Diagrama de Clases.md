#engineering #uml #system-design

El diagrama de clases es el más utilizado en UML, muestra la estructura estática del sistema representando clases, sus atributos, métodos y las relaciones entre ellas.

## Cuándo Usarlo

- Diseñar la estructura de objetos del sistema
- Definir el modelo de dominio
- Comunicar la arquitectura de clases
- Identificar relaciones entre entidades

## Ejemplo: Sistema de E-commerce

### Modelo de Dominio

```
┌─────────────────────┐         ┌─────────────────────┐
│       Usuario       │         │       Producto      │
├─────────────────────┤         ├─────────────────────┤
│ - id: int           │         │ - id: int           │
│ - nombre: string    │         │ - nombre: string    │
│ - email: string     │ 0..*    │ - precio: decimal   │
│ - password: string  │─────────│ - stock: int        │
├─────────────────────┤    1   ├─────────────────────┤
│ + login()           │         │ + actualizarStock()  │
│ + registrar()       │         └──────────┬──────────┘
└──────────┬──────────┘                  │
           │                              │
           │ 1..*                        │
           ▼                              │
┌─────────────────────┐         ┌────────▼──────────┐
│      Pedido          │         │   Categoría       │
├─────────────────────┤         ├───────────────────┤
│ - id: int           │         │ - id: int         │
│ - fecha: datetime   │         │ - nombre: string  │
│ - total: decimal    │         ├───────────────────┤
│ - estado: string    │         │ + agregar()       │
├─────────────────────┤         └───────────────────┘
│ + calcularTotal()   │
│ + confirmar()        │
└─────────────────────┘
```

### Relaciones en el Ejemplo

| Relación | Descripción |
|----------|-------------|
| Usuario 1 ──→ 0..* Pedido | Un usuario puede tener muchos pedidos |
| Pedido * ──→ 1 Producto | Cada pedido tiene varios productos |
| Producto 0..* ──→ 1 Categoría | Un producto pertenece a una categoría |

## Notación de Clases

```go
// Equivalente en código Go
type Usuario struct {
    ID       int    `json:"id"`
    Nombre   string `json:"nombre"`
    Email    string `json:"email"`
}

type UsuarioRepository interface {
    Save(u Usuario) error
    FindByID(id int) (Usuario, error)
}
```

## Relaciones Detalladas

### Herencia (Generalización)
```
    ┌───────────┐
    │  Persona  │
    └─────┬─────┘
          △
    ┌─────┴─────┐
    │           │
┌───▼───┐   ┌───▼───┐
│Cliente │   │Admin  │
└───────┘   └───────┘
```

### Agregación (tiene un, parte separable)
```
   ◇────────
  /           \
┌─┐          ┌─┐
│A│          │B│
└─┘          └─┘
```

### Composición (parte inseparable)
```
   ◆────────
  /           \
┌─┐          ┌─┐
│A│          │B│
└─┘          └─┘
```

## Multiplicidad

| Notación | Significado |
|----------|-------------|
| 1 | Exactamente uno |
| 0..1 | Cero o uno |
| * | Cero o muchos |
| 1..* | Uno o muchos |
| 2..5 | Rango específico |

[[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/index.md|<- Volver a Diagramas de Estructurales]]