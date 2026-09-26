---
isFirst: true
---
#architecture #system-design #distributed-systems #design-patterns

El módulo **Diseño y Arquitectura** centraliza todo el conocimiento estructural de software del repositorio: desde modelos de arquitectura macro y sistemas distribuidos, hasta patrones de diseño a nivel de clases y técnicas de modelado y diagramación UML.

---

## Diferencia Fundamental: Arquitectura vs. Diseño

> [!NOTE] Metáfora de la Construcción
> - **Patrones de Arquitectura (*Nivel Macro / Sistema*)**: Definen la estructura global, los subsistemas, las fronteras entre servicios y cómo fluye la información a gran escala (ej. MVC, MVVM, Microservicios, Saga, Circuit Breaker).
> - **Patrones de Diseño (*Nivel Micro / Código y Clases*)**: Son los planos de los muebles y las habitaciones: cómo se crean los objetos en memoria y cómo colaboran las clases concretas (ej. Singleton, Factory Method, Observer, Builder).

---

## Índice Maestro

.
├── [[Diseño y Arquitectura/Diseño y Arquitectura.md|Diseño y Arquitectura.md]]
├── APIs y Comunicación
│   └── [[Diseño y Arquitectura/APIs y Comunicación/Diseño de APIs.md|Diseño de APIs.md]]
├── Modelado y Diagramación
│   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Modelado y Diagramación.md|Modelado y Diagramación.md]]
│   ├── Diagramas
│   │   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Diagramas UML.md|Diagramas UML.md]]
│   │   ├── Comportamiento
│   │   │   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Actividad.md|Diagrama de Actividad.md]]
│   │   │   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Diagrama de Casos de Uso.md]]
│   │   │   ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Estados.md|Diagrama de Estados.md]]
│   │   │   └── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Secuencia.md|Diagrama de Secuencia.md]]
│   │   └── Estructurales
│   │       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Clases.md|Diagrama de Clases.md]]
│   │       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Componentes.md|Diagrama de Componentes.md]]
│   │       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Despliegue.md|Diagrama de Despliegue.md]]
│   │       └── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Estructurales/Diagrama de Paquetes.md|Diagrama de Paquetes.md]]
│   └── Herramientas
│       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Herramientas de Diagramación.md|Herramientas de Diagramación.md]]
│       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Draw.io.md|Draw.io.md]]
│       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Lucidchart.md|Lucidchart.md]]
│       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Mermaid.md|Mermaid.md]]
│       ├── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Miro.md|Miro.md]]
│       └── [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/PlantUML.md|PlantUML.md]]
├── Patrones de Arquitectura
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - BFF.md|Patrón Arquitectónico - BFF.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Circuit Breaker.md|Patrón Arquitectónico - Circuit Breaker.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Clean Architecture.md|Patrón Arquitectónico - Clean Architecture.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - CQRS.md|Patrón Arquitectónico - CQRS.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Event Sourcing.md|Patrón Arquitectónico - Event Sourcing.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Event-Driven.md|Patrón Arquitectónico - Event-Driven.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Hexagonal.md|Patrón Arquitectónico - Hexagonal.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Microservicios.md|Patrón Arquitectónico - Microservicios.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVC.md|Patrón Arquitectónico - MVC.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVI.md|Patrón Arquitectónico - MVI.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVVM.md|Patrón Arquitectónico - MVVM.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Por Capas.md|Patrón Arquitectónico - Por Capas.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Saga.md|Patrón Arquitectónico - Saga.md]]
│   ├── [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Signals.md|Patrón Arquitectónico - Signals.md]]
│   └── [[Diseño y Arquitectura/Patrones de Arquitectura/Metodologías Limpias - Criterios de Aplicación.md|Metodologías Limpias - Criterios de Aplicación.md]]
├── Patrones de Diseño
│   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrones de Diseño - Catálogo GoF.md|Patrones de Diseño - Catálogo GoF.md]]
│   ├── Creacionales
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Abstract Factory.md|Patrón de Diseño - Abstract Factory.md]]
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Builder.md|Patrón de Diseño - Builder.md]]
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Factory Method.md|Patrón de Diseño - Factory Method.md]]
│   │   └── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Singleton.md|Patrón de Diseño - Singleton.md]]
│   ├── Estructurales
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Adapter.md|Patrón de Diseño - Adapter.md]]
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Decorator.md|Patrón de Diseño - Decorator.md]]
│   │   ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Facade.md|Patrón de Diseño - Facade.md]]
│   │   └── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Proxy.md|Patrón de Diseño - Proxy.md]]
│   └── Comportamiento
│       ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Command.md|Patrón de Diseño - Command.md]]
│       ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Observer.md|Patrón de Diseño - Observer.md]]
│       ├── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - State.md|Patrón de Diseño - State.md]]
│       └── [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Strategy.md|Patrón de Diseño - Strategy.md]]
├── Principios de Diseño
│   ├── [[Diseño y Arquitectura/Principios de Diseño/Principios de Diseño.md|Principios de Diseño.md]]
│   ├── [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - SOLID.md|Principio de Diseño - SOLID.md]]
│   ├── [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - DRY.md|Principio de Diseño - DRY.md]]
│   ├── [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - KISS.md|Principio de Diseño - KISS.md]]
│   └── [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - YAGNI.md|Principio de Diseño - YAGNI.md]]
├── Seguridad
│   └── [[Diseño y Arquitectura/Seguridad/Seguridad en Arquitectura.md|Seguridad en Arquitectura.md]]
└── Sistemas Distribuidos
    ├── [[Diseño y Arquitectura/Sistemas Distribuidos/Rate Limit.md|Rate Limit.md]]
    ├── [[Diseño y Arquitectura/Sistemas Distribuidos/Teorema CAP.md|Teorema CAP.md]]
    └── [[Diseño y Arquitectura/Sistemas Distribuidos/Teorema PACELC.md|Teorema PACELC.md]]

---

## Secciones Temáticas

### 1. 🏛️ Patrones de Arquitectura
- **UI y Presentación**:
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVC.md|MVC]]: Separación para aplicaciones web renderizadas en servidor (*SSR*).
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVVM.md|MVVM]]: Enlace reactivo con `StateFlow`, estándar en Android e iOS.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - MVI.md|MVI]]: Flujo Unidireccional (*UDF*) con Estado Inmutable para Compose/React/Flutter.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Signals.md|Signals]]: Reactividad de grano fino (*Fine-Grained*), grafo DAG y estándar moderno en Angular, Solid y propuesta TC39.
- **Estructura y Dominio**:
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Por Capas.md|Por Capas (Layered)]]: Organización técnica N-Capas tradicional.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Hexagonal.md|Hexagonal (Puertos y Adaptadores)]]: Dominio puro aislado de la tecnología.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Clean Architecture.md|Clean Architecture]]: Regla de dependencias hacia adentro y alta testabilidad.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Metodologías Limpias - Criterios de Aplicación.md|Metodologías Limpias]]: Criterios de Joshua y Johandry sobre cuándo implementar Clean Architecture.
- **Sistemas Distribuidos y Microservicios**:
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Microservicios.md|Microservicios]]: Servicios autónomos con *Database-per-Service*.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - BFF.md|BFF (Backend for Frontend)]]: Capas de API intermedias por tipo de cliente.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Saga.md|Patrón Saga]]: Transacciones distribuidas con compensaciones.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Circuit Breaker.md|Circuit Breaker]]: Cortacircuitos ante fallos en cascada.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - CQRS.md|CQRS]]: Segregación de caminos de lectura y escritura.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Event Sourcing.md|Event Sourcing]]: Persistencia como secuencia histórica inmutable.
  - [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Event-Driven.md|Event-Driven]]: Arquitectura asíncrona desacoplada por brokers.

---

### 2. 🧩 Patrones de Diseño (GoF)
- [[Diseño y Arquitectura/Patrones de Diseño/Patrones de Diseño - Catálogo GoF.md|Catálogo General de Patrones GoF]]: Visión global estructurada de los 23 patrones de diseño clásicos.

#### Patrones Creacionales (Creational)
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Singleton.md|Singleton]]: Instancia única thread-safe (Go `sync.Once`, Kotlin `object`).
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Factory Method.md|Factory Method]]: Creación desacoplada del operador `new`, delegando en subclases/funciones factoría (OCP).
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Abstract Factory.md|Abstract Factory]]: Creación de familias completas de productos relacionados e interoperables.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Builder.md|Builder]]: Construcción por pasos de objetos complejos y parámetros opcionales (Fluent API y Go Functional Options).

#### Patrones Estructurales (Structural)
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Adapter.md|Adapter]]: Convierte interfaces incompatibles para permitir que clases dispares colaboren.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Decorator.md|Decorator]]: Añade responsabilidades dinámicamente mediante envoltorios (*wrappers*) sucesivos.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Facade.md|Facade]]: Ofrece una interfaz unificada, simple y de alto nivel a un subsistema complejo.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Proxy.md|Proxy]]: Objeto sustituto o intermediario para control de acceso, lazy loading, caché o auditoría.

#### Patrones de Comportamiento (Behavioral)
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Observer.md|Observer]]: Mecanismo reactivo de suscripción y notificación (1-a-N).
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Strategy.md|Strategy]]: Familia de algoritmos intercambiables en tiempo de ejecución, eliminando condicionales masivos.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Command.md|Command]]: Encapsula solicitudes como objetos independientes, facilitando Undo/Redo, colas y CQRS.
- [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - State.md|State]]: Modela máquinas de estados finitas (*FSM*) alterando el comportamiento cuando cambia el estado interno.

#### Claves Rápidas para Entrevistas Técnicas
- **Factory Method vs. Abstract Factory**: Factory Method crea un único producto usando herencia o polimorfismo; Abstract Factory crea familias completas de productos relacionados usando composición.
- **Adapter vs. Facade vs. Decorator vs. Proxy**:
  - *Adapter*: Cambia o traduce la interfaz.
  - *Facade*: Simplifica la interfaz de un subsistema complejo.
  - *Decorator*: Mantiene la misma interfaz y añade nuevas responsabilidades funcionales.
  - *Proxy*: Mantiene la misma interfaz y controla el acceso o ciclo de vida (seguridad, caché, lazy loading).
- **Strategy vs. State**: Ambos usan una composición polimórfica idéntica. Pero en *Strategy*, los algoritmos son independientes y los configura el cliente; en *State*, el objeto cambia de estado de forma interna y las clases de estado orquestan las transiciones.

---

### 3. 📐 Principios de Diseño
- [[Diseño y Arquitectura/Principios de Diseño/Principios de Diseño.md|Visión General de Principios de Diseño]]: Fundamentos, leyes de diseño y sinergia entre principios.
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - SOLID.md|SOLID]]: Los 5 pilares de diseño modular (SRP, OCP, LSP, ISP, DIP) con explicaciones individuales, ejemplos en Go y Kotlin, diagramas y preguntas de entrevista.
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - DRY.md|DRY (Don't Repeat Yourself)]]: Centralización del conocimiento de negocio, duplicación accidental vs. esencial, la regla de 3 y AHA (*Avoid Hasty Abstractions*).
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - KISS.md|KISS (Keep It Simple, Stupid)]]: Reducción radical de la complejidad accidental frente a la complejidad esencial, combate a la sobreingeniería y *patternitis*.
- [[Diseño y Arquitectura/Principios de Diseño/Principio de Diseño - YAGNI.md|YAGNI (You Aren't Gonna Need It)]]: Erradicación de la generalización especulativa y del código muerto preventivo (Extreme Programming).

---

### 4. 🌐 Sistemas Distribuidos y Resiliencia
- [[Diseño y Arquitectura/Sistemas Distribuidos/Teorema CAP.md|Teorema CAP]]: Consistencia ($C$), Disponibilidad ($A$) y Tolerancia a Particiones ($P$).
- [[Diseño y Arquitectura/Sistemas Distribuidos/Teorema PACELC.md|Teorema PACELC]]: Compromiso entre Latencia ($L$) y Consistencia ($C$) en operación normal.
- [[Diseño y Arquitectura/Sistemas Distribuidos/Rate Limit.md|Rate Limiting]]: Algoritmos Token Bucket, Leaky Bucket y Sliding Window.

---

### 5. 🔌 APIs y Comunicación
- [[Diseño y Arquitectura/APIs y Comunicación/Diseño de APIs.md|Diseño de APIs]]: REST, GraphQL y gRPC con ejemplos en Go y Kotlin.

---

### 6. 🛡️ Seguridad
- [[Diseño y Arquitectura/Seguridad/Seguridad en Arquitectura.md|Seguridad en Arquitectura]]: OWASP Top 10, Autenticación (JWT/OAuth), Autorización (RBAC/ABAC) y HTTPS/TLS.

---

### 7. 📊 Modelado y Diagramación
- [[Diseño y Arquitectura/Modelado y Diagramación/Modelado y Diagramación.md|Modelado y Diagramación de Sistemas]]: Visión general del proceso de análisis y especificación.
- [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Diagramas UML.md|Diagramas UML]]: Diagramas estructurales (Clases, Componentes, Despliegue, Paquetes) y de comportamiento (Secuencia, Actividad, Estados, Casos de Uso).
- [[Diseño y Arquitectura/Modelado y Diagramación/Herramientas/Herramientas de Diagramación.md|Herramientas de Diagramación]]: Mermaid, PlantUML, Draw.io, Lucidchart y Miro.

---

[[README.md|<- Volver al Inicio]]
