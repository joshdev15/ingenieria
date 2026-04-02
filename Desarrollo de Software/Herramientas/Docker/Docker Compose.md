#development #docker

Docker Compose permite definir y ejecutar aplicaciones multi-contenedor.

## docker-compose.yml

```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DB_HOST=db
    depends_on:
      - db
      - redis
    networks:
      - mi-red

  db:
    image: postgres:15-alpine
    environment:
      - POSTGRES_USER=app
      - POSTGRES_PASSWORD=secret
      - POSTGRES_DB=mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - mi-red

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    networks:
      - mi-red

  nginx:
    image: nginx:latest
    ports:
      - "80:80"
    depends_on:
      - app
    volumes:
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
    networks:
      - mi-red

volumes:
  postgres_data:

networks:
  mi-red:
    driver: bridge
```

## Comandos Compose

```bash
# Iniciar servicios
docker-compose up

# Iniciar en background
docker-compose up -d

# Detener servicios
docker-compose down

# rebuild y iniciar
docker-compose up --build

# Ver logs
docker-compose logs -f

# Ver logs de servicio específico
docker-compose logs -f app

# Listar servicios
docker-compose ps

# Escalar servicio
docker-compose up -d --scale app=3

# Ejecutar comando en servicio
docker-compose exec app sh

# Detener y eliminar volúmenes
docker-compose down -v
```

## Variables de Entorno

```yaml
# .env file
POSTGRES_USER=app
POSTGRES_PASSWORD=secret
POSTGRES_DB=mydb

# docker-compose.yml
services:
  db:
    image: postgres:15-alpine
    environment:
      - POSTGRES_USER=${POSTGRES_USER}
      - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
      - POSTGRES_DB=${POSTGRES_DB}
```

## healthcheck

```yaml
services:
  db:
    image: postgres:15-alpine
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U app -d mydb"]
      interval: 10s
      timeout: 5s
      retries: 5

  app:
    depends_on:
      db:
        condition: service_healthy
```

## Override

```yaml
# docker-compose.override.yml
# Se combina automáticamente con docker-compose.yml
services:
  app:
    environment:
      - DEBUG=true
    ports:
      - "3001:3000"
```

## Comandos Avanzados

```bash
# Pull de imágenes sin iniciar
docker-compose pull

# Validar configuración
docker-compose config

# Generar eventos
docker-compose events

# Restart de servicios
docker-compose restart

# Top de procesos
docker-compose top
```

## Ejemplo with Build

```yaml
services:
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    ports:
      - "3000:3000"

  backend:
    build:
      context: ./backend
      args:
        - NODE_ENV=production
    ports:
      - "3001:3001"
```

[[Desarrollo de Software/Herramientas/Docker/Docker.md]]
