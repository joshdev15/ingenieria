#os

## Hilo

Un hilo, se podría definir como un proceso dentro de otro proceso,
es posible crear varios hilos dentro de un proceso pero su
característica diferencial es que comparten el mismo espacio de
direcciones con otros hilos.

## Uso de Hilos

Dentro de los argumentos para usar hilos, se encuentra que,
comparten datos del proceso padre e hilos hermanos, consumen menos
recursos para crearlos y destruirlos, además entre hilos se pueden
traslapar, por tanto se agiliza el uso del CPU haciendo las tareas
en menor tiempo y uso de recursos.

## El modelo clásico de hilo

Afirmando el concepto de hilo, un hilo comparte el espacio de
direcciones con su padre y sus posibles hermanos.

La CPU reparte el tiempo de ejecución entre los hilos de un proceso
dando la impresión de que todos se ejecutan al mismo tiempo.

## Hilos en POSIX

 - **POSIX**: Portable Operative System Interface for uniX, es un
     estandar de API que todo programa para un sistema operativo
     Unix debe cumplir, lo que impacta positivamente en la
     portabilidad, compatibilidad e interoperabilidad de las
     aplicaciones orientadas a este sistema operativo

El IEEE define un estándar con nombre 1003.1c que contiene el API para la creación y funcionalidad general para los hilos. En el lenguaje de programación **C** existe un paquete llamado **Pthreads**, el cual tiene mas de sesenta métodos para gestionar la correcta funcionalidad de los hilos.

## Implementación de hilos en el espacio de usuario

Usar los hilos a nivel del espacio de usuario permite crearlos y
hacerlos funcionar dentro de un proceso compartiendo los recursos
en ejecución, sin que el kernel se entere de que existe.

## Implementación de hilos en el kernel

En este caso, el kernel es el ente que maneja todos los recursos,
por ejemplo si algún hilo debe crearse, bloquearse o destruirse, el
kernel posee una tabla en donde almacena los registros de los hilos.

## Implementación híbridas

Cuando es de forma hibrida el kernel solo conoce sus hilos, pero en
el espacio de usuario se crean y funcionan otros hilos que
comparten recursos y turnan para cumplir su función.

## Activaciones del planificador

Debido a que los hilos del kernel son mas lentos, cuando se bloquea
un hilo, el kernel activa al sistema en tiempo de ejecución
(a esto se le llama **upcall**) en una dirección conocida
(como un punto de control).

El sistema en tiempo de ejecución replanifica sus hilos y marca el
actual como bloqueado, toma otro de la lista y reinicia el
bloqueado. Cuando el kernel se entera que el hilo bloqueado ya
responde realiza otro **upcall** para que el sistema en tiempo de
ejecución lo use a discreción.

- **Contra Activaciones del planificador**:
    Los contras de las Activaciones del planificador, son
    principalmente fundamentadas en que una **upcall** viola el
    principio de los sistemas por capas, ya que hace comunicaciones
    entre capas sin el debido procedimiento de estos sistemas.

## Hilo emergente

Un Hilo emergente es un procedimiento en el cual la llegada de un
mensaje genera un hilo para manejar ese mensaje, al ser un mensaje
que no tiene ningún recurso previamente utilizado, es muy rápida su
creación y ejecución, ya que no debe restaurar ningún estado,
prácticamente inicia desde cero.

## Conversión de código de hilado simple a multihilado

La conversión es compleja, debido a que se presentan diversos
problemas, en principio el uso de variables globales y su escritura
y sobreescritura por todo código que la use. Para ello hay varias
posibles soluciones con consecuencias diversas como el bloqueo de
la escritura de una variable global mientras esté en uso, pero esto
deshabilita el paralelismo en ese código, la implementación de las
señales, así como tener una pila por hilo, dependiendo del ámbito
en el que se desarrolle cada hilo. En conclusión es bastante
difícil implementar la conversión sin mencionar que se deba
mantener la retro compatibilidad.
