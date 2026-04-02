#engineering #system-design

Los principios de diseño de sistemas guían la creación de arquitecturas robustas y mantenibles.

## Principios SOLID

### S - Single Responsibility (Responsabilidad Única)
Cada clase debe tener una única razón para cambiar.

```go
// ✓ Correcto: Responsabilidad única
type UserRepository interface {
    Save(user User) error
    FindByID(id string) (User, error)
}

// ✗ Incorrecto: Múltiples responsabilidades
type UserManager struct {
    SaveUser()     // datos
    SendEmail()    // notificación
    GenerateReport() // reportes
}
```

### O - Open/Closed (Abierto/Cerrado)
Abierto para extensión, cerrado para modificación.

```go
// Extender mediante composición
type PaymentProcessor interface {
    Process(amount float64) error
}

type CreditCardPayment struct{}
func (p *CreditCardPayment) Process(amount float64) error { ... }

// Agregar nuevo método sin modificar existente
type PayPalPayment struct{}
func (p *PayPalPayment) Process(amount float64) error { ... }
```

### L - Liskov Substitution (Sustitución de Liskov)
Las subclases deben ser sustituibles por sus superclases.

```go
type Reader interface {
    Read() string
}

type PDFReader struct{}
func (p *PDFReader) Read() string { return "PDF content" }

type ImageReader struct{}
func (i *ImageReader) Read() string { return "Image content" }

// Ambas pueden usarse donde se espere Reader
```

### I - Interface Segregation (Segregación de Interfaces)
Preferir interfaces pequeñas específicas.

```go
// ✓ Mejor: Interfaces pequeñas
type Printer interface { Print() }
type Scanner interface { Scan() }

// ✗ Peor: Interface grande
type MultiFunction interface {
    Print()
    Scan()
    Fax()
    Copy()
}
```

### D - Dependency Inversion (Inversión de Dependencias)
Depender de abstracciones, no de concreciones.

```go
// ✓ Correcto
type UserRepository interface { Save(User) error }

type Service struct {
    repo UserRepository  // Depende de abstracción
}

// ✗ Incorrecto
type Service struct {
    repo MySQLRepository  // Depende de implementación
}
```

## Otros Principios

### DRY (Don't Repeat Yourself)
No repetir código.

### KISS (Keep It Simple, Stupid)
Simplicidad ante todo.

### YAGNI (You Aren't Gonna Need It)
No implementar funciones por anticipado.

### CoC (Convention over Configuration)
Usar convenciones en lugar de configuraciones.

[[Diseño de Sistemas]]