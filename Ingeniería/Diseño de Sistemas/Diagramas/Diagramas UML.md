#engineering #uml #system-design

UML (Unified Modeling Language) es un lenguaje estandar para visualizar, especificar y documentar sistemas orientados a objetos.

## Historia

- **1997**: UML 1.0 publicado por OMG
- **2005**: UML 2.0 disponible
- **2017**: UML 2.5.1 (version actual)

## Indice

.
├── [[Ingeniería/Diseño de Sistemas/Diagramas/Diagramas UML.md|Diagramas UML.md]]
├── Comportamiento
│   ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/index.md|index.md]]
│   ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Actividad.md|Diagrama de Actividad.md]]
│   ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Diagrama de Casos de Uso.md]]
│   ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Estados.md|Diagrama de Estados.md]]
│   └── [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Secuencia.md|Diagrama de Secuencia.md]]
└── Estructurales
    ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/index.md|index.md]]
    ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Clases.md|Diagrama de Clases.md]]
    ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Componentes.md|Diagrama de Componentes.md]]
    ├── [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Despliegue.md|Diagrama de Despliegue.md]]
    └── [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Paquetes.md|Diagrama de Paquetes.md]]

## Categorias de Diagramas

### Diagramas Estructurales (Estatica)
Muestran la estructura estatica del sistema.

| Diagrama | Proposito | Archivo |
|----------|-----------|---------|
| **Clases** | Estructura de clases y relaciones | [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Clases.md|Ver]] |
| **Objetos** | Instancias de clases | - |
| **Componentes** | Componentes y dependencias | [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Componentes.md|Ver]] |
| **Despliegue** | Distribucion fisica del sistema | [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Despliegue.md|Ver]] |
| **Paquetes** | Organizacion de elementos | [[Ingeniería/Diseño de Sistemas/Diagramas/Estructurales/Diagrama de Paquetes.md|Ver]] |
| **Perfil** | Extensiones de UML | - |

### Diagramas de Comportamiento (Dinamica)
Muestran el comportamiento dinamico del sistema.

| Diagrama | Proposito | Archivo |
|----------|-----------|---------|
| **Casos de Uso** | Funcionalidades del sistema | [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Ver]] |
| **Actividad** | Flujos de trabajo | [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Actividad.md|Ver]] |
| **Estado** | Comportamiento de objetos | [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Estados.md|Ver]] |
| **Secuencia** | Interacciones ordenadas | [[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/Diagrama de Secuencia.md|Ver]] |
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

[[Ingeniería/Diseño de Sistemas/Diseño de Sistemas.md|<- Volver a Diseño de Sistemas]]