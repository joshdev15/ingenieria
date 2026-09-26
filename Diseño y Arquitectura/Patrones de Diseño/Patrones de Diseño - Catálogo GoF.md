#architecture #design-patterns #gof

# Catálogo General de Patrones de Diseño (GoF)

Los patrones de diseño son soluciones estandarizadas y reutilizables a problemas de diseño de software comunes y recurrentes en la programación orientada a objetos y el desarrollo modular. Fueron formalizados originalmente por el *Gang of Four* (Erich Gamma, Richard Helm, Ralph Johnson y John Vlissides).

---

## Categorías GoF

### 1. Patrones Creacionales (Creational)
Resuelven la creación e instanciación de objetos de forma flexible, desacoplando el código cliente de las clases concretas y evitando el uso indiscriminado del operador de instanciación directo (`new`).

| Patrón | Descripción | Guía Detallada |
|--------|-------------|----------------|
| **Singleton** | Garantiza una única instancia de una clase en todo el ciclo de vida de la aplicación con acceso global controlado. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Singleton.md\|Ver Singleton]] |
| **Factory Method** | Define una interfaz de creación pero delega en las subclases o funciones la decisión de qué clase concreta instanciar. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Factory Method.md\|Ver Factory Method]] |
| **Abstract Factory** | Proporciona una interfaz para crear familias de objetos relacionados o dependientes sin especificar sus clases concretas. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Abstract Factory.md\|Ver Abstract Factory]] |
| **Builder** | Permite construir objetos complejos paso a paso con configuraciones personalizadas y parámetros opcionales. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Builder.md\|Ver Builder]] |
| **Prototype** | Permite copiar o clonar objetos existentes sin que el código dependa de sus clases concretas. | Conceptual |

---

### 2. Patrones Estructurales (Structural)
Explican cómo ensamblar objetos y clases en estructuras más grandes a la vez que se mantiene la flexibilidad y eficiencia del sistema.

| Patrón | Descripción | Guía Detallada |
|--------|-------------|----------------|
| **Adapter** | Convierte la interfaz de una clase en otra interfaz esperada por los clientes, permitiendo la colaboración de clases incompatibles. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Adapter.md\|Ver Adapter]] |
| **Decorator** | Añade dinámicamente nuevas responsabilidades y comportamientos a objetos individuales envolviéndolos sin usar herencia. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Decorator.md\|Ver Decorator]] |
| **Facade** | Proporciona una interfaz simplificada y de alto nivel a una biblioteca, framework o conjunto complejo de subsistemas. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Facade.md\|Ver Facade]] |
| **Proxy** | Proporciona un sustituto o intermediario de otro objeto para controlar el acceso, cachear, validar seguridad o retrasar su carga. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Proxy.md\|Ver Proxy]] |
| **Composite** | Compone objetos en estructuras de árbol para representar jerarquías de parte-todo, tratando hojas y contenedores de forma uniforme. | Conceptual |
| **Bridge** | Desacopla una abstracción de su implementación para que ambas puedan variar de manera independiente. | Conceptual |
| **Flyweight** | Comparte eficientemente el estado intrínseco común entre múltiples objetos para soportar grandes cantidades de grano fino sin agotar memoria. | Conceptual |

---

### 3. Patrones de Comportamiento (Behavioral)
Se encargan de la asignación efectiva de responsabilidades entre objetos y de los algoritmos y mecanismos de comunicación e interacción entre ellos.

| Patrón | Descripción | Guía Detallada |
|--------|-------------|----------------|
| **Observer** | Define un mecanismo de suscripción 1-a-N para notificar automáticamente a múltiples observadores sobre cualquier evento. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Observer.md\|Ver Observer]] |
| **Strategy** | Define una familia de algoritmos, los encapsula en clases independientes y los hace intercambiables dinámicamente. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Strategy.md\|Ver Strategy]] |
| **Command** | Encapsula una solicitud como un objeto, permitiendo parametrizar acciones, encolar operaciones y soportar *Undo/Redo*. | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - Command.md\|Ver Command]] |
| **State** | Permite a un objeto alterar su comportamiento cuando su estado interno cambia, modelando una máquina de estados finita (*FSM*). | [[Diseño y Arquitectura/Patrones de Diseño/Patrón de Diseño - State.md\|Ver State]] |
| **Chain of Responsibility** | Pasa solicitudes a lo largo de una cadena de manejadores potenciales hasta que uno la procesa. | Conceptual |
| **Iterator** | Permite recorrer secuencialmente elementos de una colección sin exponer su representación subyacente. | Conceptual |
| **Mediator** | Reduce las dependencias caóticas entre objetos restringiendo la comunicación directa y forzándola a través de un objeto mediador. | Conceptual |
| **Memento** | Captura y externaliza el estado interno de un objeto sin violar el encapsulamiento para poder restaurarlo posteriormente. | Conceptual |
| **Template Method** | Define el esqueleto de un algoritmo en una superclase y permite a las subclases redefinir ciertos pasos sin cambiar la estructura general. | Conceptual |
| **Visitor** | Permite separar algoritmos u operaciones de los objetos sobre los cuales operan, agregando funciones sin modificar las clases. | Conceptual |

---

## Criterios de Selección y 'Code Smells'

> [!TIP] ¿Cuándo aplicar un patrón?
> - **Problemas recurrentes y validados**: El problema encaja de forma natural en la solución del patrón.
> - **Evolución del sistema**: Cuando los requisitos cambian constantemente y se necesita desacoplar componentes (OCP/DIP).
> - **Vocabulario ubicuo del equipo**: Facilita la comunicación entre ingenieros (*"apliquemos un Observer para los eventos de cobro"*).

> [!CAUTION] ¿Cuándo NO aplicarlo? (Antipatrón de Sobreingeniería)
> - **Complejidad innecesaria**: Aplicar patrones a problemas triviales antes de que surja la necesidad (*YAGNI - You Aren't Gonna Need It*).
> - **Patternitis**: Tratar de forzar cada trozo de código dentro de un patrón del catálogo GoF.
> - Si un `switch` simple con 3 casos resuelve el problema sin vistas a crecer, no crees 5 clases y 2 interfaces de Strategy.

---

## Navegación

- [[Diseño y Arquitectura/Diseño y Arquitectura.md|<- Volver al Índice Principal de Diseño y Arquitectura]]