#engineering #uml #system-design

El diagrama de despliegue muestra la distribución física del sistema, representando los nodos (hardware/software) donde se ejecutan los componentes.

## Cuándo Usarlo

- Planificar la infraestructura
- Definir servidores y servicios
- Mostrar comunicación entre servicios
- документировать arquitectura de producción

## Ejemplo: Arquitectura Cloud

```
                                    ┌─────────────────────┐
                                    │   CDN (CloudFront)  │
                                    └──────────┬──────────┘
                                               │
                                    ┌──────────▼──────────┐
                                    │  Load Balancer      │
                                    │  (ALB - AWS)        │
                                    └──────────┬──────────┘
                                               │
              ┌─────────────────────────────────┼─────────────────────────────────┐
              │                                 │                                 │
   ┌──────────▼──────────┐          ┌──────────▼──────────┐          ┌──────────▼──────────┐
   │   EC2 Instance 1      │          │   EC2 Instance 2     │          │   EC2 Instance 3     │
   │   ┌────────────────┐  │          │   ┌────────────────┐  │          │   ┌────────────────┐  │
   │   │ Docker        │  │          │   │ Docker         │  │          │   │ Docker         │  │
   │   │ ┌──────────┐  │  │          │   │ ┌──────────┐   │  │          │   │ ┌──────────┐   │  │
   │   │ │ API      │  │  │          │   │ │ API      │   │  │          │   │ │ API      │   │  │
   │   │ │ Service  │  │  │          │   │ │ Service  │   │  │          │   │ │ Service  │   │  │
   │   │ └──────────┘  │  │          │   │ └──────────┘   │  │          │   │ └──────────┘   │  │
   │   └────────────────┘  │          │   └────────────────┘  │          │   └────────────────┘  │
   └──────────┬───────────┘          └──────────┬───────────┘          └──────────┬───────────┘
              │                                 │                                 │
              └─────────────────────────────────┼─────────────────────────────────┘
                                                │
                                    ┌───────────▼──────────┐
                                    │   RDS PostgreSQL     │
                                    │   (Primary)          │
                                    └───────────┬──────────┘
                                                │
                                    ┌───────────▼──────────┐
                                    │   ElastiCache        │
                                    │   (Redis)            │
                                    └──────────────────────┘
```

## Ejemplo: Diagrama Simplificado

```
┌─────────────────────┐        ┌─────────────────────┐
│   Web Server        │        │   App Server        │
│   ┌─────────────┐   │        │   ┌─────────────┐   │
│   │   Nginx     │───┼────────┼───│   Node.js   │   │
│   └─────────────┘   │        │   └─────────────┘   │
└──────────┬──────────┘        └──────────┬──────────┘
           │                             │
           └──────────────┬──────────────┘
                          │
              ┌───────────▼───────────┐
              │    Database          │
              │   PostgreSQL         │
              └───────────────────────┘
```

## Notación

| Elemento | Símbolo | Descripción |
|----------|---------|-------------|
| Nodo | □ | Servidor o dispositivo |
| Componente | ☐ | Software en ejecución |
| Artifact | ⌘ | Archivo o paquete |
| Comunicación | ───→ | Protocolo de red |

## Relación con Otros Diagramas

- **Diagrama de Componentes**: Muestra qué componentes van en cada nodo
- **Diagrama de Clases**: Define los objetos que se almacenan en BD

[[index|← Volver a Estructurales]]