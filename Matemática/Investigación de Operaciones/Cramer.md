#math

La Regla de Cramer es un método para resolver sistemas de ecuaciones lineales usando determinantes.

## Condiciones

- Sistema de n ecuaciones con n incógnitas
- Determinante de la matriz de coeficientes ≠ 0

## Fórmula

Para un sistema $Ax = B$:

$$x_i = \frac{det(A_i)}{det(A)}$$

Donde $A_i$ es la matriz A con la columna i reemplazada por el vector B.

## Ejemplo 2x2

Sistema:
```
2x + y = 5
3x - y = 1
```

**Matriz de coeficientes (A)**:
```
| 2 | 1 |
| 3 | -1 |
```

**Vector de términos independientes (B)**:
```
| 5 |
| 1 |
```

**Paso 1**: Calcular det(A)
```
det(A) = 2×(-1) - 1×3 = -2 - 3 = -5
```

**Paso 2**: Matriz para x (reemplazar columna 1 con B)
```
| 5 | 1 |
| 1 | -1 |

det(Ax) = 5×(-1) - 1×1 = -5 - 1 = -6
```

**Paso 3**: Matriz para y (reemplazar columna 2 con B)
```
| 2 | 5 |
| 3 | 1 |

det(Ay) = 2×1 - 5×3 = 2 - 15 = -13
```

**Solución**:
- x = det(Ax)/det(A) = -6/-5 = 6/5
- y = det(Ay)/det(A) = -13/-5 = 13/5

## Ventajas

- Solución exacta
- Útil para sistemas pequeños (2 o 3 variables)

## Desventajas

- Computacionalmente ineficiente para sistemas grandes (O(n!))
- Requiere que det(A) ≠ 0

## Relación con Gauss-Jordan

- Gauss-Jordan: O(n³) - más eficiente computacionalmente
- Cramer: Conceptualmente simple pero lento

[[Matemática/Investigación de Operaciones/Matrices.md]]