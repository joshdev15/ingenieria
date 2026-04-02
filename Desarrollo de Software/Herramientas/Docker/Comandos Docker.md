#development #docker

Docker es una plataforma de contenerización que permite empaquetar aplicaciones con todas sus dependencias.

## Imágenes

```bash
# Listar imágenes
docker images

# Buscar imagen
docker search nginx

# Descargar imagen
docker pull nginx:latest

# Eliminar imagen
docker rmi nginx

# Construir imagen desde Dockerfile
docker build -t mi-app .
```

## Contenedores

```bash
# Crear y ejecutar contenedor
docker run -d -p 8080:80 --name mi-nginx nginx

# Listar contenedores activos
docker ps

# Listar todos los contenedores
docker ps -a

# Ejecutar comando en contenedor
docker exec -it mi-nginx bash

# Detener contenedor
docker stop mi-nginx

# Iniciar contenedor
docker start mi-nginx

# Eliminar contenedor
docker rm mi-nginx

# Ver logs
docker logs -f mi-nginx
```

## Variables de Entorno

```bash
# Con variables de entorno
docker run -d -e NODE_ENV=production -e PORT=3000 mi-app

# Desde archivo .env
docker run --env-file .env mi-app
```

## Volúmenes

```bash
# Montar volumen
docker run -v /mi/dato:/app/datos mi-app

# Volume específico
docker volume create mi-volumen
docker run -v mi-volumen:/app/datos mi-app
```

## Redes

```bash
# Crear red
docker network create mi-red

# Conectar contenedor a red
docker network connect mi-red mi-contenedor

# Inspecionar red
docker network inspect mi-red
```

## Dockerfile

```dockerfile
# Imagen base
FROM node:20-alpine

# Directorio de trabajo
WORKDIR /app

# Copiar archivos
COPY package*.json ./
COPY . .

# Instalar dependencias
RUN npm install

# Exponer puerto
EXPOSE 3000

# Comando inicial
CMD ["npm", "start"]
```

## Comandos Útiles

```bash
# Ver uso de recursos
docker stats

# Ver procesos dentro de contenedor
docker top mi-nginx

# Copiar archivos desde contenedor
docker cp mi-nginx:/app/logs ./logs

# Limpiar recursos
docker system prune

# Ver información de contenedor
docker inspect mi-nginx
```

## Tips

| Comando | Descripción |
|---------|-------------|
| `-d` | Modo detached (background) |
| `-p` | Mapear puerto (host:container) |
| `-v` | Volumen |
| `-e` | Variable de entorno |
| `-it` | Interactivo con terminal |
| `--name` | Nombre del contenedor |
| `--link` | Vincular contenedores (legacy) |

[[Desarrollo de Software/Herramientas/Docker/Docker.md]]
