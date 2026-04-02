#engineering #tools #diagramas

PlantUML permite crear diagramas escribiendo texto, ideal para versionar y mantener en código.

## Características

| Feature | Descripción |
|---------|-------------|
| **Como código** | Escribir texto, generar imagen |
| **Versionable** | Git-friendly |
| ** много diagrams** | UML, flowcharts, Gantt, etc. |
| **Extensiones** | VS Code, Jenkins, Confluence |
| **Open Source** | Gratuito |

## Ejemplo: Diagrama de Clases

```
@startuml
class User {
    - id: int
    - name: string
    + getName(): string
}

class Admin extends User {
    - permissions: list
    + manageUsers()
}
@enduml
```

## Ejemplo: Diagrama de Secuencia

```
@startuml
Alice -> Bob: Hello
Bob --> Alice: Hi there
Alice -> Bob: How are you?
Bob --> Alice: Fine, thanks
@enduml

## Ejemplo: Diagrama de Actividad

```
@startuml
start
:Initialize;
if (Data valid?) then (yes)
    :Process;
    :Save;
else (no)
    :Show error;
endif
stop
@enduml
```

## Instalación y Uso

### VS Code
1. Install "Plant UML" extension
2. Preview con `Alt+D`

### Online
- [PlantUML Online Server](https://www.plantuml.com/plantuml)

## Ventajas

- Versionable en Git
- Reproducible
- Rápido para cambios
- Ideal para documentación automática

## Desventajas

- Curva de aprendizaje
- Menos intuitivo que visual
- Debugging de errores difícil

[[Ingeniería/Diseño de Sistemas/Herramientas/Herramientas de Diagramación.md]]