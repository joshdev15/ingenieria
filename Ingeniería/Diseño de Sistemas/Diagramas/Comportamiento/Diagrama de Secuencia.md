#engineering #uml #system-design

El diagrama de secuencia muestra cómo los objetos interactúan entre sí a lo largo del tiempo, enfatizando el orden de los mensajes.

## Cuándo Usarlo

- Modelar flujos de negocio
- Definir la lógica de operaciones
- Identificar responsabilidades entre objetos
- Documentar APIs y contratos

## Ejemplo: Flujo de Login

```
┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│  Actor   │    │  Router  │    │ AuthSvc  │    │  UserDB  │
└────┬─────┘    └────┬─────┘    └────┬─────┘    └────┬─────┘
     │              │              │              │
     │ 1. POST /login              │              │
     ├─────────────→│              │              │
     │              │              │              │
     │ 2. validate()│              │              │
     ├─────────────→│              │              │
     │              │              │              │
     │ 3. findByEmail()            │              │
     ├───────────────→│              │              │
     │              │              │              │
     │ 4. SELECT * FROM users    │              │
     ├───────────────→│─────────────→│              │
     │              │              │              │
     │ 5. user     │              │              │
     │←─────────────│←─────────────│              │
     │              │              │              │
     │ 6. compare password         │              │
     ├─────────────→│              │              │
     │              │              │              │
     │ 7. JWT token│              │              │
     │←─────────────│              │              │
     │              │              │              │
     │ 8. 200 OK + JWT             │              │
     ├─────────────→│              │              │
     │              │              │              │
```

## Ejemplo: Crear Pedido (E-commerce)

```
┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│  Client  │    │ OrderCtrl│    │OrderSvc  │    │  StockAPI│
└────┬─────┘    └────┬─────┘    └────┬─────┘    └────┬─────┘
     │              │              │              │
     │ POST /orders│              │              │
     ├─────────────→│              │              │
     │              │              │              │
     │              │ createOrder()│              │
     ├─────────────→│              │              │
     │              │              │              │
     │              │ validateStock()             │
     ├───────────────→│              │              │
     │              │              │              │
     │              │              │ → 200 OK     │
     │              │←─────────────│              │
     │              │              │              │
     │              │ save()      │              │
     │              ├─────────────→│              │
     │              │              │              │
     │              │ ← Order created            │
     │              │              │              │
     │ 201 Created + Order         │              │
     ├─────────────→│              │              │
```

## Elementos

| Elemento | Símbolo | Descripción |
|----------|---------|-------------|
| Lifeline | ─── | Línea vertical del objeto |
| Actor | □ | Usuario externo |
| Mensaje | → | Flecha horizontal |
| Activación | ▌ | Barra de ejecución |
| Return | ───→ | Respuesta |
| Loop | [ ] | Repetición |
| Alt | [ ] | Alternativa |

## Código Equivalente (Go)

```go
// Este diagrama representa:
func (c *OrderController) CreateOrder(w http.ResponseWriter, r *http.Request) {
    // 1. Parse request
    var req CreateOrderRequest
    json.NewDecoder(r.Body).Decode(&req)
    
    // 2. Validate stock (OrderSvc)
    if err := orderService.ValidateStock(req.Items); err != nil {
        // Return error
    }
    
    // 3. Save order (OrderSvc)
    order, err := orderService.Create(req)
    
    // 4. Return response
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusCreated)
    json.NewEncoder(w).Encode(order)
}
```

## Fragmentos Combinados

```
┌──────────────────────────────────────┐
│  alt                                │
│  ┌─────────┐  ┌─────────┐  ┌───────┐ │
│  │ stock   │  │ payment │  │ error │ │
│  │  ok     │  │  ok     │  │       │ │
│  └────┬────┘  └────┬────┘  └───┬───┘ │
│       ▼           ▼           ▼     │
│    (continue)  (continue)  (abort)  │
└──────────────────────────────────────┘
```

[[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/index.md]]