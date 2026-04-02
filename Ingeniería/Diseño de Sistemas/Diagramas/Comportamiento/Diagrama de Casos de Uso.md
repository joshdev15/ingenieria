#engineering #uml #system-design

El diagrama de casos de uso muestra las funcionalidades del sistema desde la perspectiva del usuario (actor).

## Cuándo Usarlo

- Definir requisitos funcionales
- Comunicar con stakeholders
- Identificar actores del sistema
- Validar el alcance del proyecto

## Ejemplo: Sistema de Biblioteca

```
┌─────────────────────────────────────────────────────────────────┐
│                        SISTEMA BIBLIOTECA                       │
│                                                                  │
│  ┌─────────────────┐                                           │
│  │   Lector        │◄─────────────────────────┐               │
│  └────────┬────────┘                          │               │
│           │                                   │               │
│           │ 1. Buscar libros                  │               │
│           ├───────────────────────────────────┤               │
│           │                                   │               │
│           │ 2. Reservar libro                 │               │
│           ├───────────────────────────────────┤               │
│           │                                   │               │
│           │ 3. Prestar libro                  │               │
│           ├───────────────────────────────────┤               │
│           │                                   │               │
│  ┌────────▼────────┐                          │               │
│  │  Bibliotecario  │◄──────────────────────────┘               │
│  └────────┬────────┘                                          │
│           │                                                    │
│           │ 4. Registrar usuario                              │
│           │ 5. Gestionar inventario                           │
│           │ 6. Generar reportes                               │
│           │                                                    │
└───────────┼────────────────────────────────────────────────────┘
            │
            ▼
┌────────────────────────────────────────────────────────────────┐
│                      CASOS DE USO                             │
├────────────────────────────────────────────────────────────────┤
│ UC-001: Buscar Libros                                          │
│   Actor: Lector                                               │
│   Desc: El usuario busca libros por título, autor, ISBN      │
│   Flujo: 1) Ingresa criterios → 2) Sistema muestra resultados │
├────────────────────────────────────────────────────────────────┤
│ UC-002: Reservar Libro                                         │
│   Actor: Lector                                               │
│   Desc: El usuario reserva un libro disponible                 │
│   Precond: Usuario autenticado, libro disponible               │
├────────────────────────────────────────────────────────────────┤
│ UC-003: Prestar Libro                                         │
│   Actor: Bibliotecario                                         │
│   Desc: Prestar libro a usuario con miembro activo             │
│   Precond: Usuario tiene membresía vigente                    │
├────────────────────────────────────────────────────────────────┤
│ UC-004: Registrar Usuario                                      │
│   Actor: Bibliotecario                                         │
│   Desc: Crear nuevo usuario en el sistema                     │
└────────────────────────────────────────────────────────────────┘
```

## Relaciones entre Casos de Uso

### Include (Inclusion obligatoria)
```
┌─────────────┐         ┌─────────────┐
│   Login     │◄───include────│ Ver Dashboard │
└─────────────┘         └─────────────┘
```
El usuario debe hacer login para ver el dashboard.

### Extend (Extensión opcional)
```
┌─────────────┐         ┌─────────────┐
│   Buscar    │◄───extend─────│ Ver Detalles  │
└─────────────┘         └─────────────┘
```
"Ver detalles" extiende "Buscar" con información adicional.

### Herencia
```
       ┌─────────────┐
       │  Usuario    │
       └──────┬──────┘
             △
    ┌────────┴────────┐
    │                 │
┌───▼───┐       ┌───▼───┐
│Lector │       │Admin  │
└───────┘       └───────┘
```

## Actores

| Tipo | Descripción |
|------|-------------|
| **Primario** | Usuario principal del sistema |
| **Secundario** | Soporta al sistema |
| **Externo** | Sistema externo que interactúa |

[[Ingeniería/Diseño de Sistemas/Diagramas/Comportamiento/index.md]]