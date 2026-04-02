#engineering #uml #system-design

El diagrama de componentes muestra la estructura del sistema en términos de sus componentes y las dependencias entre ellos.

## Cuándo Usarlo

- Visualizar la organización de componentes
- Definir la arquitectura de módulos
- Mostrar dependencias entre componentes
- Planificar la distribución del código

## Ejemplo: Arquitectura de Aplicación Web

```
┌─────────────────────────────────────────────────────────────┐
│                    FRONTEND (Client)                       │
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │   React App    │  │   Vue App       │                  │
│  └────────┬────────┘  └────────┬────────┘                  │
└───────────┼────────────────────┼──────────────────────────┘
            │                    │
            │ HTTP/REST         │ HTTP/REST
            ▼                    ▼
┌─────────────────────────────────────────────────────────────┐
│                    API GATEWAY                             │
│  ┌─────────────────────────────────────────────┐           │
│  │         Kong / AWS API Gateway              │           │
│  └─────────────────────────────────────────────┘           │
└──────────────────────┬──────────────────────────────────────┘
                       │
         ┌─────────────┼─────────────┐
         ▼             ▼             ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   Auth      │ │   Users     │ │  Products   │
│  Service    │ │  Service    │ │  Service    │
│  (Go)       │ │  (Go)       │ │   (Go)      │
└──────┬──────┘ └──────┬──────┘ └──────┬──────┘
       │              │              │
       └──────────────┼──────────────┘
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                    DATABASE LAYER                          │
│  ┌─────────────────┐  ┌─────────────────┐                  │
│  │   PostgreSQL    │  │     Redis      │                  │
│  │  (Users/Orders) │  │    (Cache)     │                  │
│  └─────────────────┘  └─────────────────┘                  │
└─────────────────────────────────────────────────────────────┘
```

## Ejemplo: Diagrama de Componentes (Simplificado)

```
┌──────────────────┐      ┌──────────────────┐      ┌──────────────────┐
│   Component A    │──────│   Component B    │──────│   Component C    │
│                  │ uses │                  │ uses │                  │
│ - state          │      │ - config         │      │ - data           │
│ - behavior()     │      │ - process()     │      │ - render()       │
└──────────────────┘      └──────────────────┘      └──────────────────┘
```

## Símbolos

| Símbolo | Significado |
|---------|-------------|
| ┌───┐ | Componente |
| ───→ | Dependencia |
| ◇─── | Realización |
| ○─── | Interfaz provista |
| ───○ | Interfaz requerida |

## Relación con Otros Diagramas

- **Diagrama de Despliegue**: Muestra dónde se ejecutan los componentes
- **Diagrama de Clases**: Define la estructura de cada componente

[[index|← Volver a Estructurales]]