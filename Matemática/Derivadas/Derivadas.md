#math

## Qué son las derivadas?

En matemáticas, la derivada de una función nos dice cómo cambia la función a medida que变化 su variable independiente. En términos más simples, la derivada nos da la **tasa de cambio instantánea** de la función en un punto dado.

## Definición Formal

La derivada de una función f(x) en un punto x se define como:

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

## Interpretación Geométrica

La derivada representa la **pendiente de la recta tangente** a la curva en un punto.

## Reglas de Derivación

### 1. Constante
$$\frac{d}{dx}(c) = 0$$

### 2. Potencia
$$\frac{d}{dx}(x^n) = nx^{n-1}$$

### 3. Suma/Resta
$$\frac{d}{dx}(f + g) = f' + g'$$

### 4. Producto
$$\frac{d}{dx}(f \cdot g) = f' \cdot g + f \cdot g'$$

### 5. Cociente
$$\frac{d}{dx}\left(\frac{f}{g}\right) = \frac{f' \cdot g - f \cdot g'}{g^2}$$

### 6. Cadena (Regla de la cadena)
$$\frac{d}{dx}(f(g(x))) = f'(g(x)) \cdot g'(x)$$

## Derivadas de Funciones Comunes

| Función | Derivada |
|---------|----------|
| $c$ | 0 |
| $x^n$ | $nx^{n-1}$ |
| $\sin(x)$ | $\cos(x)$ |
| $\cos(x)$ | $-\sin(x)$ |
| $e^x$ | $e^x$ |
| $\ln(x)$ | $\frac{1}{x}$ |

## Aplicaciones

- **Física**: Velocidad como derivada de posición, aceleración como derivada de velocidad
- **Economía**: Marginal Cost, Marginal Revenue
- **Optimización**: Encontrar máximos y mínimos de funciones

## Ejemplo

$$f(x) = x^3 + 2x^2 - 5x + 1$$

$$f'(x) = 3x^2 + 4x - 5$$

[[Matemática]]