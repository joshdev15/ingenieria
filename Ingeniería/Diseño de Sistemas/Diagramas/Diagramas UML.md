#engineering #uml #system-design

UML (Unified Modeling Language) es un lenguaje estándar para visualizar, especificar y documentar sistemas orientados a objetos.

## Historia

- **1997**: UML 1.0 publicado por OMG
- **2005**: UML 2.0 disponible
- **2017**: UML 2.5.1 (versión actual)

## Categorías de Diagramas

### Diagramas Estructurales (Estática)
Muestran la estructura estática del sistema.

| Diagrama | Propósito | Archivo |
|----------|-----------|---------|
| **Clases** | Estructura de clases y relaciones | [[Estructurales/Diagrama de Clases|Ver详情]] |
| **Objetos** | Instancias de clases | - |
| **Componentes** | Componentes y dependencias | [[Estructurales/Diagrama de Componentes|Ver详情]] |
| **Despliegue** | Distribución física del sistema | [[Estructurales/Diagrama de Despliegue|Ver详情]] |
| **Paquetes** | Organización de elementos | [[Estructurales/Diagrama de Paquetes|Ver详情]] |
| **Perfil** | Extensiones de UML | - |

### Diagramas de Comportamiento (Dinámica)
Muestran el comportamiento dinámico del sistema.

| Diagrama | Propósito | Archivo |
|----------|-----------|---------|
| **Casos de Uso** | Funcionalidades del sistema | [[Comportamiento/Diagrama de Casos de Uso|Ver详情]] |
| **Actividad** | Flujos de trabajo | [[Comportamiento/Diagrama de Actividad|Ver详情]] |
| **Estado** | Comportamiento de objetos | [[Comportamiento/Diagrama de Estados|Ver详情]] |
| **Secuencia** | Interacciones ordenadas | [[Comportamiento/Diagrama de Secuencia|Ver详情]] |
| **Comunicación** | Interacciones entre objetos | - |
| **Timing** | Restricciones de tiempo | - |

## Elementos Comunes

### Relaciones
```
┌────────────┐     ┌────────────┐
│  Clase A   │───→ │  Clase B   │  → Asociación (navegación)
└────────────┘     └────────────┘
        │
        ◇
        │
   Agregación (parte de)
        │
        ◆
        │
   Composición (parte de, ciclo de vida)
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

[[Diseño de Sistemas]]