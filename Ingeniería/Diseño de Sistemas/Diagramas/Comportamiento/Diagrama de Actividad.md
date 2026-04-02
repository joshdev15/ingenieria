#engineering #uml #system-design

El diagrama de actividades modela el flujo de trabajo de un proceso, mostrando las actividades y las decisiones de forma similar a un flowchart.

## Cuándo Usarlo

- Modelar procesos de negocio
- Definir flujos de trabajo
- Representar algoritmos
- Documentar procedimientos

## Ejemplo: Proceso de Checkout

```
                                    ┌─────────────────┐
                                    │   INICIO        │
                                    └────────┬────────┘
                                             ▼
                              ┌─────────────────────────┐
                              │ 1. Revisar Carrito      │
                              └───────────┬─────────────┘
                                          ▼
                         ┌────────────────────────────────┐
                         │ 2. ¿Carrito tiene productos?  │
                         └────────────┬───────────────────┘
                                      │
                    ┌─────────────────┴─────────────────┐
                    ▼                                     ▼
          ┌─────────────────────┐              ┌─────────────────┐
          │         SÍ          │              │       NO        │
          └──────────┬──────────┘              └────────┬────────┘
                     ▼                                 ▼
          ┌─────────────────────┐              ┌─────────────────┐
          │ 3. Calcular Total   │              │ 4. Mostrar msgs  │
          └──────────┬──────────┘              │    "Carrito      │
                     ▼                         │     vacío"       │
          ┌─────────────────────┐              └────────┬────────┘
          │ 5. Seleccionar      │                       ▼
          │    Método de Pago   │              ┌─────────────────┐
          └──────────┬──────────┘              │      FIN        │
                     ▼                         └──────────────────┘
          ┌─────────────────────┐
          │ 6. Procesar Pago     │
          └──────────┬──────────┘
                     ▼
          ┌─────────────────────────────────┐
          │ 7. ¿Pago exitoso?               │
          └────────────┬────────────────────┘
                       │
        ┌──────────────┴──────────────┐
        ▼                              ▼
┌──────────────┐             ┌─────────────────┐
│     SÍ       │             │       NO         │
└──────┬───────┘             └────────┬────────┘
       ▼                            ▼
┌──────────────┐             ┌─────────────────┐
│8. Generar    │             │9. Mostrar error │
│   orden      │             │   de pago       │
└──────┬───────┘             └────────┬────────┘
       ▼                            ▼
┌──────────────┐             ┌─────────────────┐
│10. Confirmar │             │  FIN            │
│   pedido     │             └─────────────────┘
└──────┬───────┘
       ▼
┌──────────────┐
│ 11. Enviar   │
│    email     │
└──────┬───────┘
       ▼
┌──────────────┐
│    FIN       │
└──────────────┘
```

## Ejemplo: Login de Usuario

```
┌──────────────┐
│   Inicio     │
└──────┬───────┘
       ▼
┌──────────────────┐
│Ingresa email    │
└────────┬─────────┘
       ▼
┌──────────────────┐
│Ingresa password │
└────────┬─────────┘
       ▼
┌──────────────────────┐
│  Credenciales        │
│       válidas?       │
└────────┬─────────────┘
         │
   ┌─────┴─────┐
   ▼           ▼
  SÍ          NO
   │           │
   ▼           ▼
┌───────┐  ┌────────────────┐
│  JWT  │  │  Mostrar error │
└───┬───┘  │  "Credenciales │
   │      │   inválidas"    │
   ▼      └────────┬────────┘
┌───────┐         ▼
│  200  │  ┌───────────┐
│  OK   │  │   FIN     │
└───────┘  └───────────┘
```

## Notación

| Símbolo | Significado |
|---------|-------------|
| ○ | Nodo inicial |
| ● | Nodo final |
| ▭ | Actividad/Acción |
| ◇ | Decisión |
| ──→ | Flujo |
| ══ | Fork (paralelo) |
| ─╲ | Join (sincronización) |

## Swinlanes (Carriles)

```
┌───────────────┬───────────────┬───────────────┐
│   Cliente     │    Sistema    │   Backend     │
├───────────────┼───────────────┼───────────────┤
│Ingresa datos │               │               │
│─────────────→│               │               │
│               │Valida datos  │               │
│               │─────────────→│               │
│               │              │  Busca user  │
│               │              │─────────────→ │
│               │              │   ←────────── │
│               │  Devuelve    │               │
│               │←─────────────│               │
│  Muestra OK  │              │               │
│←─────────────│              │               │
└───────────────┴───────────────┴───────────────┘
```

[[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/index.md]]