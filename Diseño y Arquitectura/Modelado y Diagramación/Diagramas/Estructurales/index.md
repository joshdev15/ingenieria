#engineering #uml #system-design

Los diagramas estructurales muestran la estructura estatica del sistema.

## Índice

.
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/index.md|index.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Clases.md|Diagrama de Clases.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Componentes.md|Diagrama de Componentes.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Despliegue.md|Diagrama de Despliegue.md]]
└── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Paquetes.md|Diagrama de Paquetes.md]]

## Diagrama de Clases

El mas usado, muestra clases, atributos, metodos y relaciones.

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

| Relacion | Simbolo | Descripción |
|----------|---------|-------------|
| **Asociacion** | ───→ | Conexion simple |
| **Agregacion** | ◇──→ | "Tiene un" (parte separable) |
| **Composicion** | ◆──→ | "Tiene un" (parte inseparable) |
| **Herencia** | △──→ | Generalizacion |
| **Dependencia** | - - → | Usa temporalmente |

### Multiplicidad

| Notacion | Significado |
|----------|-------------|
| 1 | Exactly one |
| 0..1 | Zero or one |
| * | Zero or more |
| 1..* | One or more |

---

## Diagrama de Componentes

Muestra los componentes del sistema y sus dependencias. Para APIs, ver [[Diseño y Arquitectura/APIs y Comunicación/Diseño de APIs.md|Diseño de APIs]].

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

Muestra la distribucion fisica del sistema.

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
│  │   dominio   │  │   infra     │   │
│  │ ┌─────────┐ │  │ ┌─────────┐ │   │
│  │ │ Entity  │ │  │ │  Repo   │ │   │
│  │ └─────────┘ │  │ └─────────┘ │   │
│  └─────────────┘  └─────────────┘   │
└─────────────────────────────────────┘
```

[[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Diagramas UML.md|<- Volver a Diagramas UML]]