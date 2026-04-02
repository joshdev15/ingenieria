#engineering #uml #system-design

El diagrama de estados muestra el comportamiento de un objeto respondiendo a eventos, representando los estados posibles y las transiciones entre ellos.

## Cuándo Usarlo

- Modelar el ciclo de vida de objetos
- Representar comportamiento con múltiples estados
- Definir máquinas de estados finitas
- Documentar flujos de proceso complejos

## Ejemplo: Estado de un Pedido

```
┌─────────────────────────────────────────────────────────────────────┐
│                         PEDIDO                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────┐                                                  │
│  │  Pendiente  │                                                  │
│  └──────┬──────┘                                                  │
│         │ confirmar()                                             │
│         ▼                                                         │
│  ┌─────────────┐    cancelar()       ┌─────────────┐            │
│  │ Confirmado  │──────────────────────│ Cancelado   │            │
│  └──────┬──────┘                     └─────────────┘            │
│         │ aprobarPago()                                         │
│         ▼                                                         │
│  ┌─────────────┐    rechazarPago()   ┌─────────────┐            │
│  │ Pagado      │──────────────────────│ Cancelado   │            │
│  └──────┬──────┘                     └─────────────┘            │
│         │ preparar()                                           │
│         ▼                                                         │
│  ┌─────────────┐    enviar()          ┌─────────────┐            │
│  │ Preparando  │──────────────────────│ Cancelado   │            │
│  └──────┬──────┘                     └─────────────┘            │
│         │                                                         │
│         ▼                                                         │
│  ┌─────────────┐    entregar()        ┌─────────────┐            │
│  │ Enviado     │──────────────────────│  Entregado  │            │
│  └──────┬──────┘                     └─────────────┘            │
│         │                                                         │
└─────────┼─────────────────────────────────────────────────────────┘
```

## Ejemplo: Login de Usuario

```
                              ┌─────────────┐
                              │  LoggedOut  │
                              └──────┬──────┘
                                     │ login()
                                     ▼
                              ┌─────────────┐
                     ┌────────│ Authenticat │
                     │        └──────┬──────┘
                     │               │ verify()
                     │               ▼
          ┌──────────┴────┐   ┌─────────────┐
          │ Auth Failed   │   │  LoggedIn   │
          └───────┬───────┘   └──────┬──────┘
                  │                   │ logout()
                  ▼                   ▼
            ┌─────────────┐   ┌─────────────┐
            │  LoggedOut  │   │  LoggedOut  │
            └─────────────┘   └─────────────┘
```

## Notación

| Elemento | Descripción |
|----------|-------------|
| ○ | Estado inicial |
| ● | Estado final |
| rectángulo | Estado |
| → | Transición (evento) |
| [ ] | Condición de guarda |
| / | Acción |
| * | Estado histórico |

## Transiciones con Acciones

```
┌─────────┐    evento[condición] / acción    ┌─────────┐
│ Estado A │ ───────────────────────────────→ │ Estado B │
└─────────┘                                   └─────────┘

Ejemplo:
┌─────────┐    order() [stock > 0] / createOrder() ┌─────────┐
│  idle   │ ─────────────────────────────────────→ │ active  │
└─────────┘                                        └─────────┘
```

## Subestados (Historial)

```
┌─────────────────────────────────────┐
│        Estado Contenedor            │
│                                     │
│  ┌───────────┐   ┌───────────┐     │
│  │   Sub1    │   │   Sub2    │     │
│  └───────────┘   └───────────┘     │
│         │               │          │
│         └───────┬───────┘          │
│                 │                  │
│                 * H                │
└─────────────────────────────────────┘
```

El `H` (historial) vuelve al último subestado activo.

[[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/index.md]]