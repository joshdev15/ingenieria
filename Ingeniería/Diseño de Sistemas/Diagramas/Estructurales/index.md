#engineering #uml #system-design

Los diagramas estructurales muestran la estructura estática del sistema.

## Índice

- [[Diagrama de Clases]] - Estructura de clases y relaciones
- [[Diagrama de Componentes]] - Componentes y dependencias
- [[Diagrama de Despliegue]] - Distribución física
- [[Diagrama de Paquetes]] - Organización de módulos

## Diagrama de Clases

El más usado, muestra clases, atributos, métodos y relaciones.

```
┌─────────────────────────┐
│       Usuario           │
├─────────────────────────┤
│ - id: int               │
│ - nombre: string        │
│ - email: string         │
├─────────────────────────┤
│ + getNombre(): string  │
│ + setEmail(email)       │
└─────────────────────────┘
        △
        │
   Herencia
        │
┌─────────────────────────┐
│      Administrador     │
├─────────────────────────┤
│ - permisos: list         │
├─────────────────────────┤
│ + eliminarUsuario()     │
└─────────────────────────┘
```

### Tipos de Relaciones

| Relación | Símbolo | Descripción |
|----------|---------|-------------|
| **Asociación** | ───→ | Conexión simple |
| **Agregación** | ◇──→ | "Tiene un" (parte separable) |
| **Composición** | ◆──→ | "Tiene un" (parte inseparable) |
| **Herencia** | △──→ | Generalización |
| **Dependencia** | - - → | Usa temporalmente |

### Multiplicidad

| Notación | Significado |
|----------|-------------|
| 1 | Exactly one |
| 0..1 | Zero or one |
| * | Zero or more |
| 1..* | One or more |

---

## Diagrama de Componentes

Muestra los componentes del sistema y sus dependencias. Para APIs, ver [[Arquitectura de Software/Diseño de APIs|Diseño de APIs]].

```
┌──────────────┐      ┌──────────────┐
│   Frontend   │──────│    API       │
│  (React)     │      │   (REST)     │
└──────────────┘      └──────┬───────┘
                             │
                    ┌────────▼────────┐
                    │   Database     │
                    │  (PostgreSQL)  │
                    └────────────────┘
```

---

## Diagrama de Despliegue

Muestra la distribución física del sistema.

```
┌─────────────────┐        ┌─────────────────┐
│   Servidor Web  │        │ Servidor BD     │
│   ┌───────────┐ │        │ ┌─────────────┐ │
│   │ Nginx     │ │        │ │ PostgreSQL  │ │
│   └───────────┘ │        │ └─────────────┘ │
└─────────────────┘        └─────────────────┘
        │
        └───────→ (JDBC)
```

---

## Diagrama de Paquetes

Organiza elementos en grupos.

```
┌─────────────────────────────────────┐
│         Sistema                     │
│  ┌─────────────┐  ┌─────────────┐   │
│  │   domínio   │  │   infra     │   │
│  │ ┌─────────┐ │  │ ┌─────────┐ │   │
│  │ │ Entity  │ │  │ │  Repo   │ │   │
│  │ └─────────┘ │  │ └─────────┘ │   │
│  └─────────────┘  └─────────────┘   │
└─────────────────────────────────────┘
```

[[Diagramas UML]]