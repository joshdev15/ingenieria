#math

El método de Gauss-Jordan es un algoritmo para resolver sistemas de ecuaciones lineales y encontrar la inversa de una matriz.

## Idea Central

Consiste en aplicar operaciones elementales a una matriz aumentada hasta transformarla en la **matriz identidad**.

## Operaciones Elementales

1. Intercambiar filas
2. Multiplicar una fila por un escalar no nulo
3. Sumar a una fila un múltiplo de otra fila

## Pasos para Resolver un Sistema

1. **Formar la matriz aumentada**: [A | B] donde A es la matriz de coeficientes y B es el vector de términos independientes.

2. **Aplicar eliminación hacia adelante**: Transformar la matriz triangular superior.

3. **Aplicar eliminación hacia atrás**: Transformar en matriz identidad.

## Ejemplo

Sistema:
```
2x + y = 5
3x - y = 1
```

Matriz aumentada:
```
| 2 | 1 | 5 |
| 3 | -1 | 1 |
```

**Paso 1**: Hacer ceros debajo del pivote (2,1)
- F2 = F2 - (3/2)F1

```
| 2 | 1 | 5 |
| 0 | -5/2 | -13/2 |
```

**Paso 2**: Normalizar segunda fila
- F2 = F2 × (-2/5)

```
| 2 | 1 | 5 |
| 0 | 1 | 13/5 |
```

**Paso 3**: Hacer cero arriba del pivote
- F1 = F1 - F2

```
| 2 | 0 | 12/5 |
| 0 | 1 | 13/5 |
```

**Paso 4**: Normalizar primera fila
- F1 = F1 / 2

```
| 1 | 0 | 6/5 |
| 0 | 1 | 13/5 |
```

**Solución**: x = 6/5, y = 13/5

## Para Calcular la Inversa

Si quieres la inversa de A, aplica Gauss-Jordan a [A | I] y obtendras [I | A⁻¹].

[[Matrices]]