---
isFirst: true
---
#architecture

La arquitectura de software es la estructura fundamental de un sistema, definiendo cómo se organizan los componentes y cómo interactúan entre sí.

## Índice

### Fundamentos
- [[Arquitectura de Software]] - Este archivo
- Principios de Diseño (Modularidad, Cohesión, Acoplamiento)
- Estilos Arquitectónicos (Monolítica, Microservicios, Capas, Hexagonal)

### Patrones y Diseño
- [[Patrones de Diseño]] - Patrones GoF (Creacionales, Estructurales, Comportamiento)
- [[Patrones Arquitectónicos]] - Layered, Hexagonal, Event-Driven, CQRS
- [[Clean Architecture]] - Arquitectura limpia por capas

### Tecnologías
- [[Diseño de APIs]] - REST, GraphQL, gRPC
- [[Seguridad]] - OWASP, autenticación, validación
- [[Tecnologías Ágiles]] - Scrum, Kanban, XP
- [[Metodologías Limpias]] - Clean Code, cuándo aplicar

## Importancia

- Define la estructura global del sistema
- Facilita la comunicación entre equipos
- Permite la evolución y mantenimiento del software
- Reduce la complejidad técnica
- Define tecnologías y herramientas a utilizar
- Soporta las cualidades no funcionales (escalabilidad, rendimiento, seguridad)

## Principios de Diseño

### Modularidad
Dividir el sistema en módulos independientes con responsabilidades claras.

### Cohesión
Cada módulo debe tener una única responsabilidad bien definida. Alta cohesión = mejor mantenibilidad.

### Acoplamiento
Minimizar las dependencias entre módulos para facilitar cambios. Bajo acoplamiento = mayor flexibilidad.

### Abstracción
Ocultar detalles de implementación detrás de interfaces definidas.

### Responsabilidad Única (SRP)
Cada clase debe tener una única razón para cambiar.

### Inversión de Dependencias (DIP)
Depender de abstracciones, no de implementaciones concretas.

## Estilos Arquitectónicos

| Estilo | Descripción | Cuándo usarlo |
|--------|-------------|---------------|
| **Monolítica** | Todo el código en una sola aplicación | Proyectos pequeños/medianos, equipos reducidos |
| **Microservicios** | Servicios pequeños e independientes | Sistemas grandes, equipos multidisciplinarios |
| **Capas** | Separación en presentación, negocio y datos | Aplicaciones empresariales tradicionales |
| **Eventos** | Comunicación mediante eventos | Sistemas reactivos, procesamiento async |
| **Hexagonal** | Puertos y adaptadores | Alta testabilidad, dominio separado |
| **Clean Architecture** | Capas independientes del framework | Proyectos con larga vida útil |

## Patrones Arquitectónicos Comunes

### MVC (Model-View-Controller)
Separación en modelo, vista y controlador.

### MVVM (Model-View-ViewModel)
Enlace de datos bidireccional, popular en frontend.

### Repository
Abstracción de la capa de datos.

### Service Layer
Lógica de negocio encapsulada en servicios.

### CQRS (Command Query Responsibility Segregation)
Separación de operaciones de lectura y escritura.

## Calidad de Software

### Atributos de Calidad
- **Rendimiento**: Tiempo de respuesta, throughput
- **Escalabilidad**: Capacidad de crecer horizontal/verticalmente
- **Seguridad**: Protección contra amenazas
- **Disponibilidad**: Uptime, tolerancia a fallos
- **Mantenibilidad**: Facilidad de cambios y evolución
- **Testabilidad**: Facilidad de pruebas unitarias

## Documentación Arquitectónica

La arquitectura debe documentarse con:
- Diagramas de componentes
- Diagramas de despliegue
- Especificación de interfaces
- ADRs (Architecture Decision Records)
