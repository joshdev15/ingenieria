#architecture #design-patterns #layered-architecture #n-tier

# Patrón Arquitectónico: Por Capas (Layered / N-Tier)

La **Arquitectura por Capas** (*Layered Architecture* o *N-Tier*) es el patrón arquitectónico tradicional más común y extendido en la industria del software. Se basa en organizar el sistema en **capas horizontales**, donde cada capa tiene un rol y una responsabilidad técnica específica y solo interactúa con sus capas adyacentes.

---

## Índice

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|<- Volver a Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Clean Architecture.md|Ver Clean Architecture]]
- [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Hexagonal.md|Ver Arquitectura Hexagonal]]

---

## Las Capas Estándar

```
┌─────────────────────────────────────────────────────┐
│          1. Presentation Layer (Presentación)       │  ← UI, Controladores REST, Vistas, DTOs
├─────────────────────────────────────────────────────┤
│          2. Business / Application (Negocio)        │  ← Casos de uso, servicios, validaciones
├─────────────────────────────────────────────────────┤
│          3. Persistence Layer (Persistencia)        │  ← DAOs, Repositorios, ORM (Hibernate, GORM)
├─────────────────────────────────────────────────────┤
│          4. Database Layer (Base de Datos)          │  ← PostgreSQL, MySQL, Oracle
└─────────────────────────────────────────────────────┘
```

1. **Capa de Presentación**:
   - Maneja la interacción con el usuario o cliente externo (peticiones HTTP, renderizado HTML, serialización JSON).
   - No contiene reglas de negocio.
2. **Capa de Negocio / Aplicación (*Service Layer*)**:
   - Implementa las reglas y la lógica de negocio del dominio, orquestando las operaciones necesarias para cumplir una solicitud.
3. **Capa de Persistencia (*Data Access Layer*)**:
   - Abstrae el acceso al motor de almacenamiento mediante consultas SQL, mapeo objeto-relacional (*ORM*) o repositorios.
4. **Capa de Base de Datos**:
   - El almacenamiento físico de los datos.

---

## Reglas de Comunicación: Capas Cerradas vs. Abiertas

- **Capas Cerradas (*Closed Layers - Recomendado*)**: Una petición que entra por la capa de presentación debe pasar obligatoriamente por la capa de negocio antes de llegar a la persistencia. Garantiza que las reglas de negocio nunca sean omitidas.
- **Capas Abiertas (*Open Layers*)**: Permiten que una capa superior salte una capa intermedia si no se requiere lógica (ej. una consulta de solo lectura que va directo de presentación a persistencia). Puede mejorar el rendimiento pero compromete la mantenibilidad a largo plazo.

---

## Ventajas y Desventajas

| Ventajas | Desventajas |
| :--- | :--- |
| **Simplicidad y Familiaridad**: Es el punto de partida natural para la mayoría de desarrolladores y frameworks (Spring, Django, NestJS, ASP.NET). | **Antipatrón de Pozo de Paso (*Architecture Sinkhole*)**: Muchas peticiones simplemente atraviesan capas de un lado a otro sin añadir ninguna lógica real, generando código repetitivo innecesario. |
| **Separación Técnica Clara**: Facilita la división de tareas entre desarrolladores según su especialidad técnica. | **Acoplamiento hacia la Base de Datos**: En la arquitectura tradicional por capas, el negocio suele depender del modelo de datos de la base de datos (al revés de lo que promueve Clean Architecture). |
| **Fácil de Testear**: Permite crear tests unitarios aislando capas mediante mocks de interfaces. | **Dificultad de Evolución Monolítica**: Tiende a convertirse en un monolito rígido difícil de descomponer si las capas crecen sin disciplina. |

---

## Referencias y Enlaces

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|Índice de Diseño y Arquitectura]]
- [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Hexagonal.md|Arquitectura Hexagonal]]
- [[Diseño y Arquitectura/Patrones de Arquitectura/Patrón Arquitectónico - Clean Architecture.md|Clean Architecture]]
- Mark Richards: *Software Architecture Patterns (O'Reilly).*
