---
isFirst: true
---
#architecture

La arquitectura de software es la estructura fundamental de un sistema, definiendo como se organizan los componentes y como interactuan entre si.

## Indice

.
├── [[Ingeniería/Arquitectura de Software/Arquitectura de Software.md|Arquitectura de Software.md]]
├── [[Ingeniería/Arquitectura de Software/Clean Architecture.md|Clean Architecture.md]]
├── [[Ingeniería/Arquitectura de Software/Diseño de APIs.md|Diseño de APIs.md]]
├── [[Ingeniería/Arquitectura de Software/Metodologías Limpias.md|Metodologías Limpias.md]]
├── [[Ingeniería/Arquitectura de Software/Patrones Arquitectónicos.md|Patrones Arquitectónicos.md]]
├── [[Ingeniería/Arquitectura de Software/Patrones de Diseño.md|Patrones de Diseño.md]]
├── [[Ingeniería/Arquitectura de Software/Seguridad.md|Seguridad.md]]
└── [[Ingeniería/Arquitectura de Software/Tecnologías Ágiles.md|Tecnologías Ágiles.md]]

## Importancia

- Define la estructura global del sistema
- Facilita la comunicacion entre equipos
- Permite la evolucion y mantenimiento del software
- Reduce la complejidad tecnica
- Define tecnologias y herramientas a utilizar
- Soporta las cualidades no funcionales (escalabilidad, rendimiento, seguridad)

## Principios de Diseno

### Modularidad
Dividir el sistema en modulos independientes con responsabilidades claras.

### Cohesion
Cada modulo debe tener una unica responsabilidad bien definida. Alta cohesion = mejor mantenibilidad.

### Acoplamiento
Minimizar las dependencias entre modulos para facilitar cambios. Bajo acoplamiento = mayor flexibilidad.

### Abstraccion
Ocultar detalles de implementacion detras de interfaces definidas.

### Responsabilidad Unica (SRP)
Cada clase debe tener una unica razon para cambiar.

### Inversion de Dependencias (DIP)
Depender de abstracciones, no de implementaciones concretas.

## Estilos Arquitectonicos

| Estilo | Descripcion | Cuando usarlo |
|--------|-------------|---------------|
| **Monolitica** | Todo el codigo en una sola aplicacion | Proyectos pequenos/medianos, equipos reducidos |
| **Microservicios** | Servicios pequenos e independientes | Sistemas grandes, equipos multidisciplinarios |
| **Capas** | Separacion en presentacion, negocio y datos | Aplicaciones empresariales tradicionales |
| **Eventos** | Comunicacion mediante eventos | Sistemas reactivos, procesamiento async |
| **Hexagonal** | Puertos y adaptadores | Alta testabilidad, dominio separado |
| **Clean Architecture** | Capas independientes del framework | Proyectos con larga vida util |

## Patrones Arquitectonicos Comunes

### MVC (Model-View-Controller)
Separacion en modelo, vista y controlador.

### MVVM (Model-View-ViewModel)
Enlace de datos bidireccional, popular en frontend.

### Repository
Abstraccion de la capa de datos.

### Service Layer
Logica de negocio encapsulada en servicios.

### CQRS (Command Query Responsibility Segregation)
Separacion de operaciones de lectura y escritura.

## Calidad de Software

### Atributos de Calidad
- **Rendimiento**: Tiempo de respuesta, throughput
- **Escalabilidad**: Capacidad de crecer horizontal/verticalmente
- **Seguridad**: Proteccion contra amenazas
- **Disponibilidad**: Uptime, tolerancia a fallos
- **Mantenibilidad**: Facilidad de cambios y evolucion
- **Testabilidad**: Facilidad de pruebas unitarias

## Documentacion Arquitectonica

La arquitectura debe documentarse con:
- Diagramas de componentes
- Diagramas de despliegue
- Especificacion de interfaces
- ADRs (Architecture Decision Records)