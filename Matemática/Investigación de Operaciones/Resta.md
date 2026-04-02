La resta de matrices es una operación en
donde se resta 2 matrices de las mismas
dimensiones, pongamos `Matriz A` y
`Matriz B`.

Para llevar a cabo la resta, se toma en
cuenta la posición, es decir la fila y
la columna y el valor se suma con el valor
en la misma posición de la otra matriz

Por ejemplo:

```
Matriz A       -      Matriz B

| 9 | 8 |            | 1 | 2 |
| 7 | 6 |            | 3 | 4 |
```

Tomando en cuenta las matrices, el valor
de la fila 1, columna 1 de la matriz A, "9"
debe restarse con el valor de la fila 1,
columna 1, de la matriz B, "1", dando
como resultado el valor de "8".

Los resultados debes ser colocados en una
nueva matriz con las mismas dimensiones.

Por ejemplo, primera suma:

Matriz resultante:

```
A: fila 1, columna 1 = 9
B: fila 1, columna 1 = 1
Total: 8

| 8 |   |
|   |   |
```

Al realizar la totalidad de las operaciones:

```
A: fila 1, columna 2 = 8
B: fila 1, columna 1 = 2
Total: 6

A: fila 2, columna 1 = 7
B: fila 2, columna 1 = 3
Total: 4

A: fila 2, columna 1 = 6
B: fila 2, columna 1 = 4
Total: 4

Matriz final:

| 8 | 6 |
| 4 | 4 |
```