#architecture #pattern

Los patrones arquitectónicos son soluciones de alto nivel a problemas recurrentes en el diseño de sistemas software.

> Para principios de diseño (SOLID, DRY, KISS), ver [[Ingeniería/Diseño de Sistemas/Principios de Diseño.md]]

## Patrones Fundamentales

### Layered Architecture (Arquitectura por Capas)

Separación del sistema en capas con responsabilidades específicas.

```
┌─────────────────────────────────────┐
│         Presentation Layer          │  ← UI, Controllers
├─────────────────────────────────────┤
│         Application Layer           │  ← Casos de uso, Servicios
├─────────────────────────────────────┤
│           Domain Layer              │  ← Entidades, Lógica de negocio
├─────────────────────────────────────┤
│        Infrastructure Layer         │  ← DB, APIs externas
└─────────────────────────────────────┘
```

**Ventajas**: Separación clara, fácil de entender
**Desventajas**: Acoplamiento entre capas, puede ser excesivamente rígido

### Hexagonal Architecture (Puertos y Adaptadores)

El dominio está en el centro, rodeado de puertos y adaptadores.

```
         ┌─────────────┐
         │   ADAPTER   │  ← UI, API, DB
         └──────┬──────┘
                ↓
         ┌─────────────┐
         │    PORT     │  ← Interfaz
         └──────┬──────┘
                ↓
         ┌─────────────┐
         │    DOMAIN   │  ← Lógica de negocio pura
         └─────────────┘
```

**Ventajas**: Alta testabilidad, dominio independiente
**Desventajas**: Más complejo inicialmente

### Event-Driven Architecture (EDA)

Comunicación mediante eventos asíncronos.

```
[Producer] → [Event Channel] → [Consumer]
                ↓
         [Event Broker]
```

**Ventajas**: Escalabilidad, desacoplamiento
**Complejidad**: Mayor dificultad para rastrear el flujo

### microservices

Descomposición en servicios pequeños e independientes.

**Características**:
- Cada servicio tiene su propia base de datos
- Comunicación via API REST o mensajes
- Despliegue independiente

**Ventajas**: Escalabilidad, autonomía de equipos
**Desventajas**: Complejidad operacional, distribución

### CQRS (Command Query Responsibility Segregation)

Separación de operaciones de lectura y escritura.

```
┌──────────────┐    ┌──────────────┐
│   Commands   │    │    Queries   │
│   (Escritura)│    │   (Lectura)  │
└──────┬───────┘    └──────┬───────┘
       ↓                   ↓
┌──────────────┐    ┌──────────────┐
│ Write Model  │    │ Read Model   │
│ (Dominio)    │    │ (Vista)      │
└──────────────┘    └──────────────┘
```

**Ventajas**: Optimización de lectura/escritura por separado
**Desventajas**: Sincronización entre modelos

## Selección de Patrón

| Requerimiento | Patrón Recomendado |
|---------------|-------------------|
| Proyecto simple | Layered |
| Alta testabilidad | Hexagonal |
| Alta concurrencia | Event-Driven |
| Sistema grande con equipos | Microservicios |
| Consultas complejas | CQRS |

[[Ingeniería/Arquitectura de Software/Arquitectura de Software.md]]
[[Ingeniería/Arquitectura de Software/Clean Architecture.md]]