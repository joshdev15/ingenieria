#engineering #uml #system-design

UML (Unified Modeling Language) es un lenguaje estándar para visualizar, especificar y documentar sistemas orientados a objetos.

## Historia

- **1997**: UML 1.0 publicado por OMG
- **2005**: UML 2.0 disponible
- **2017**: UML 2.5.1 (version actual)

## Índice

.
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Diagramas UML.md|Diagramas UML.md]]
├── Comportamiento
│   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/index.md|index.md]]
│   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Actividad.md|Diagrama de Actividad.md]]
│   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Diagrama de Casos de Uso.md]]
│   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Estados.md|Diagrama de Estados.md]]
│   └── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Secuencia.md|Diagrama de Secuencia.md]]
└── Estructurales
    ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/index.md|index.md]]
    ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Clases.md|Diagrama de Clases.md]]
    ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Componentes.md|Diagrama de Componentes.md]]
    ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Despliegue.md|Diagrama de Despliegue.md]]
    └── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Paquetes.md|Diagrama de Paquetes.md]]

## Categorias de Diagramas

### Diagramas Estructurales (Estatica)
Muestran la estructura estatica del sistema.

| Diagrama | Proposito | Archivo |
|----------|-----------|---------|
| **Clases** | Estructura de clases y relaciones | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Clases.md|Ver]] |
| **Objetos** | Instancias de clases | - |
| **Componentes** | Componentes y dependencias | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Componentes.md|Ver]] |
| **Despliegue** | Distribucion fisica del sistema | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Despliegue.md|Ver]] |
| **Paquetes** | Organizacion de elementos | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Paquetes.md|Ver]] |
| **Perfil** | Extensiones de UML | - |

### Diagramas de Comportamiento (Dinámica)
Muestran el comportamiento dinámico del sistema.

| Diagrama | Proposito | Archivo |
|----------|-----------|---------|
| **Casos de Uso** | Funcionalidades del sistema | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Ver]] |
| **Actividad** | Flujos de trabajo | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Actividad.md|Ver]] |
| **Estado** | Comportamiento de objetos | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Estados.md|Ver]] |
| **Secuencia** | Interacciones ordenadas | [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Secuencia.md|Ver]] |
| **Comunicacion** | Interacciones entre objetos | - |
| **Timing** | Restricciones de tiempo | - |

## Elementos Comunes

### Relaciones
```
┌────────────┐     ┌────────────┐
│  Clase A   │───→ │  Clase B   │  → Asociacion (navegacion)
└────────────┘     └────────────┘
        │
        ◇
        │
   Agregacion (parte de)
        │
        ◆
        │
   Composicion (parte de, ciclo de vida)
        │
        ──────
        │
    Herencia
```

### Visibilidad
- `+` Public
- `-` Private
- `#` Protected
- `~` Package

[[Diseño y Arquitectura/Modelado y Diagramación/Modelado y Diagramación.md|<- Volver a Diseño de Sistemas]]