#architecture #security

La seguridad es un aspecto crítico en el diseño de software.

## Principios de Seguridad

### Defense in Depth
Múltiples capas de seguridad, no depender de una sola.

### Least Privilege
Dar solo los permisos mínimos necesarios.

### Fail Secure
Ante errores, el sistema debe comportarse de forma segura.

### Separation of Duties
Dividir responsabilidades para evitar fraude.

## Vulnerabilidades Comunes (OWASP Top 10)

| # | Vulnerabilidad | Descripción |
|---|---------------|-------------|
| 1 | **A01: Broken Access Control** | Acceso no autorizado a datos |
| 2 | **A02: Cryptographic Failures** | Datos no cifrados o mal cifrados |
| 3 | **A03: Injection** | Inyección SQL, NoSQL, LDAP |
| 4 | **A04: Insecure Design** | Diseño sin consideraciones de seguridad |
| 5 | **A05: Security Misconfiguration** | Configuración incorrecta |
| 6 | **A06: Vulnerable Components** | Dependencias desactualizadas |
| 7 | **A07: Auth Failures** | Autenticación débil o mal implementada |
| 8 | **A08: Data Integrity Failures** | Validación insuficiente de datos |
| 9 | **A09: Logging Failures** | Falta de logs de seguridad |
| 10 | **A10: SSRF** | Server-Side Request Forgery |

## Autenticación y Autorización

### Autenticación (Who are you?)
- Contraseñas hashadas (bcrypt, scrypt)
- MFA (Multi-Factor Authentication)
- JWT (JSON Web Tokens)
- OAuth 2.0 / OpenID Connect

### Autorización (What can you do?)
- RBAC (Role-Based Access Control)
- ABAC (Attribute-Based Access Control)
- Permissions vs Roles

## HTTPS y Certificados

- **TLS 1.3** es la versión recomendada
- Certificados válidos (Let's Encrypt, etc.)
- HSTS (HTTP Strict Transport Security)

## Validación de Datos

```go
import (
    "regexp"
    "html"
)

// Ejemplo de validación en Go
func validateEmail(email string) bool {
    pattern := `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`
    return regexp.MustCompile(pattern).MatchString(email)
}

func sanitizeInput(userInput string) string {
    return html.EscapeString(userInput)
}
```

```kotlin
// Ejemplo de validación en Kotlin
fun validateEmail(email: String): Boolean {
    val pattern = Regex("^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$")
    return pattern.matches(email)
}

fun sanitizeInput(userInput: String): String {
    return userInput.replace("<", "&lt;")
                    .replace(">", "&gt;")
                    .replace("\"", "&quot;")
}
```

## Logging de Seguridad

Registrar:
- Intentos de login exitosos y fallidos
- Cambios de permisos
- Acceso a datos sensibles
- Errores y excepciones

No registrar:
- Contraseñas
- Tokens de sesión
- Datos personales sensibles

[[Ingeniería/Arquitectura de Software/Arquitectura de Software.md]]