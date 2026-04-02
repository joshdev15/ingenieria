#engineering #uml #system-design

Los diagramas de comportamiento muestran cómo el sistema responde a estímulos.

## Índice

- [[Diagrama de Casos de Uso]] - Funcionalidades desde perspectiva del usuario
- [[Diagrama de Secuencia]] - Interacciones ordenadas en el tiempo
- [[Diagrama de Actividad]] - Flujos de trabajo y procesos
- [[Diagrama de Estados]] - Estados de un objeto y transiciones

---

## Diagrama de Casos de Uso

Muestra las funcionalidades del sistema desde la perspectiva del usuario.

```
    ┌──────────────┐
    │   Actor      │  ← Usuario externo
    └──────────────┘
          │
          │
    ┌─────▼─────┐
    │   Caso    │  ← Funcionalidad
    │   de Uso  │
    └───────────┘
```

### Relaciones entre Casos de Uso

| Relación | Símbolo | Descripción |
|----------|---------|-------------|
| **Include** | <<include>> | Obligatorio |
| **Extend** | <<extend>> | Opcional |
| **Generalización** | △ | Herencia |

---

## Diagrama de Secuencia

Muestra cómo los objetos interactúan en el tiempo.

```
Usuario          LoginService          Database
  │                    │                    │
  │ 1. Ingresa datos   │                    │
  │───────────────────→│                    │
  │                    │                    │
  │                    │ 2. Validar         │
  │                    │───────────────────→│
  │                    │                    │
  │                    │ 3. Resultado       │
  │                    │←───────────────────│
  │                    │                    │
  │ 4. Respuesta       │                    │
  │←───────────────────│                    │
```

### Elementos

```
┌────────────┐
│  Objeto    │  ← lifeline
├────────────┤
│  método()  │  ← mensaje sincrono
│────────────│
│  return    │  ← mensaje de retorno
└────────────┘
```

---

## Diagrama de Actividad

Muestra flujos de trabajo (procesos de negocio).

```
┌──────────────┐
│    Inicio    │
└──────┬───────┘
       ▼
┌─────────────────┐
│  Validar datos  │ ──→ ┌───────────┐
└────────┬────────┘     │  Error    │
         │              └───────────┘
         ▼
┌─────────────────┐
│  Procesar       │
└────────┬────────┘
         │
         ▼
    ┌────────┐
    │  Fin   │
    └────────┘
```

### Símbolos

| Símbolo | Significado |
|---------|-------------|
| ○ | Nodo inicial |
| ● | Nodo final |
| ▭ | Actividad |
| ◇ | Decisión |
| → | Flujo |

---

## Diagrama de Estados

Muestra los estados de un objeto y las transiciones.

```
                            ┌───────────────┐
          ┌─────────────────│   Pendiente   │
          │                 └───────┬───────┘
          │                         │
          ▼                         ▼
┌─────────────────┐           ┌───────────────┐
│  Cancelado      │ ←──────── │  Procesando   │
└────────┬────────┘           └───────┬───────┘
         │                           │
         │                     ┌─────▼─────┐
         │                     │  Enviado  │
         │                     └─────┬─────┘
         │                           │
         │                     ┌─────▼─────┐
         └─────────────────────│ Entregado│
                                └───────────┘
```

[[Diagramas UML]]