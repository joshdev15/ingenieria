#engineering

Los casos de uso son una técnica para capturar requisitos funcionales describiendo cómo el sistema interactúa con los actores.

## Componentes de un Caso de Uso

### Elementos Básicos

| Elemento | Descripción |
|----------|-------------|
| **Actor** | Usuario o sistema que interactúa con el sistema |
| **Caso de uso** | Serie de acciones que proporcionan valor al actor |
| **Precondiciones** | Estado del sistema antes de iniciar |
| **Postcondiciones** | Estado del sistema después de completar |

### Flujo

- **Flujo principal**: Camino happy path
- **Flujos alternativos**: Variaciones del comportamiento
- **Flujos de error**: Manejo de excepciones

## Ejemplo

**Caso de uso:** Iniciar Sesión

**Actor:** Usuario

**Precondiciones:** El usuario está registrado en el sistema

**Flujo principal:**
1. El usuario ingresa su correo electrónico
2. El usuario ingresa su contraseña
3. El usuario hace clic en "Iniciar sesión"
4. El sistema valida las credenciales
5. El sistema muestra el dashboard

**Flujos alternativos:**
- Si el correo no existe, mostrar error
- Si la contraseña es incorrecta, mostrar error

**Postcondiciones:** El usuario está autenticado en el sistema

## Beneficios

- Enfoque en el usuario
- Comunicación clara con stakeholders
- Facilita la trazabilidad
- Identifica requisitos funcionales

## UML

```
┌─────────────┐       ┌──────────────────┐
│   Actor     │──────>│   Caso de Uso    │
└─────────────┘       └──────────────────┘
```

[[Ingeniería/Ingeniería de Requisitos/Ingeniería de Requisitos.md]]
[[Ingeniería/Ingeniería de Requisitos/Técnicas de Elicitación.md]]