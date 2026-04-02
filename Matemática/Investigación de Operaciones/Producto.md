#math

El producto de matrices (multiplicación matricial) es una operación donde se combinan dos matrices para obtener una tercera.

## Definición

Para multiplicar matrices, el número de **columnas de A** debe ser igual al número de **filas de B**.

Si $A$ es de $m \times n$ y $B$ es de $n \times p$, entonces $A \cdot B$ será de $m \times p$.

## Fórmula

$$(A \cdot B)_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj}$$

Cada elemento de la posición (i,j) se calcula multiplicando la fila i de A por la columna j de B.

## Ejemplo

Matriz A (2x3):
```
| 1 | 2 | 3 |
| 4 | 5 | 6 |
```

Matriz B (3x2):
```
| 7 | 8 |
| 9 | 10 |
| 11 | 12 |
```

Resultado (2x2):
```
| 1×7+2×9+3×11 | 1×8+2×10+3×12 |
| 4×7+5×9+6×11 | 4×8+5×10+6×12 |

= | 58 | 64 |
  | 139 | 154 |
```

## Propiedades

1. **Asociativa**: $(A \cdot B) \cdot C = A \cdot (B \cdot C)$
2. **Distributiva**: $A \cdot (B + C) = A \cdot B + A \cdot C$
3. **Elemento neutro**: $I \cdot A = A$ (donde I es la matriz identidad)
4. **No conmutativa**: $A \cdot B \neq B \cdot A$ (en general)

[[Matemática/Investigación de Operaciones/Matrices.md]]