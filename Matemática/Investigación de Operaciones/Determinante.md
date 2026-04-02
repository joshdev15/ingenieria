#math

El determinante es un número especial que se calcula a partir de los elementos de una matriz cuadrada.

## Definición

Solo existe determinante para **matrices cuadradas** (mismo número de filas y columnas).

Notación: $det(A)$ o $|A|$

## Para matrices 2x2

Si $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$, entonces:

$$det(A) = ad - bc$$

### Ejemplo

```
| 3 | 2 |
| 1 | 4 |

det = 3×4 - 2×1 = 12 - 2 = 10
```

## Para matrices 3x3 (Regla de Sarrus)

```
| a11 | a12 | a13 |
| a21 | a22 | a23 |
| a31 | a32 | a33 |
```

$$det(A) = a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32} - a_{13}a_{22}a_{31} - a_{12}a_{21}a_{33} - a_{11}a_{23}a_{32}$$

## Propiedades

1. $det(A) = det(A^T)$
2. $det(A \cdot B) = det(A) \cdot det(B)$
3. Si una fila es toda ceros, $det(A) = 0$
4. Si dos filas son iguales, $det(A) = 0$
5. $det(I) = 1$ (matriz identidad)

## Aplicaciones

- Resolver sistemas de ecuaciones (Regla de Cramer)
- Calcular área y volumen
- Determinar si una matriz es invertible ($det(A) \neq 0$)

[[Matrices]]