#engineering #uml #system-design

Los diagramas de comportamiento muestran como el sistema responde a estimulos.

## Índice

.
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/index.md|index.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Actividad.md|Diagrama de Actividad.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Casos de Uso.md|Diagrama de Casos de Uso.md]]
├── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Estados.md|Diagrama de Estados.md]]
└── [[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Comportamiento/Diagrama de Secuencia.md|Diagrama de Secuencia.md]]

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

| Relacion | Simbolo | Descripción |
|----------|---------|-------------|
| **Include** | <<include>> | Obligatorio |
| **Extend** | <<extend>> | Opcional |
| **Generalizacion** | △ | Herencia |

---

## Diagrama de Secuencia

Muestra como los objetos interactuan en el tiempo.

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
│  metodo()  │  ← mensaje sincrono
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

### Simbolos

| Simbolo | Significado |
|---------|-------------|
| ○ | Nodo inicial |
| ● | Nodo final |
| ▭ | Actividad |
| ◇ | Decision |
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

[[Diseño y Arquitectura/Modelado y Diagramación/Diagramas/Diagramas UML.md|<- Volver a Diagramas UML]]