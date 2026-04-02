#engineering

El Documento de Especificación de Requisitos de Software (SRS - Software Requirements Specification) es un documento formal según el estándar IEEE 830.

## Estructura IEEE 830

### 1. Introducción
- **1.1 Propósito**: Definir el alcance del documento
- **1.2 Alcance**: Qué producto se desarrolla
- **1.3 Definiciones**: Glosario de términos
- **1.4 Referencias**: Documentos relacionados
- **1.5 Visión general**: Resumen del documento

### 2. Descripción General
- **2.1 Perspectiva del producto**: Contexto del sistema
- **2.2 Funciones del producto**: Resumen de funcionalidades
- **2.3 Clases de usuarios**: Identificar tipos de usuarios
- **2.4 Restricciones de diseño**: Limitaciones técnicas

### 3. Requisitos Específicos

#### 3.1 Requisitos Funcionales
| ID | Descripción | Prioridad | Validación |
|----|-------------|-----------|------------|
| RF-01 | El sistema debe permitir login con email | Alta | Prueba funcional |
| RF-02 | El sistema debe mostrar dashboard | Alta | Prueba funcional |

#### 3.2 Requisitos No Funcionales
- **Rendimiento**: Tiempo de respuesta < 2 segundos
- **Seguridad**: Autenticación con JWT
- **Disponibilidad**: Uptime 99.9%
- **Usabilidad**: Interfaz intuitiva

#### 3.3 Requisitos de Interfaz
- **Interfaces de usuario**: Prototipos, wireframes
- **Interfaces de hardware**: Dispositivos soportados
- **Interfaces de software**: APIs, integraciones

### 4. Apéndices
- Glosario
- Análisis de requisitos
- Historial de cambios

## Mejores Prácticas

1. **Específicos**: Evitar ambigüedad
2. **Medibles**: Incluir métricas
3. **Alcanzables**: Realistas
4. **Relevantes**: Para el negocio
5. **Trazables**: Identificar fuente

[[Ingeniería/Ingeniería de Requisitos/Ingeniería de Requisitos.md]]
[[Ingeniería/Ingeniería de Requisitos/Casos de Uso.md]]