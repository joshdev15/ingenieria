#development #docker

Docker Desktop es la aplicación GUI de Docker para Windows y macOS.

## Instalación

### Windows
1. Descargar Docker Desktop desde [docker.com](https://www.docker.com/products/docker-desktop/)
2. Ejecutar el instalador
3. WSL2 se instalará automáticamente (requerido)
4. Iniciar Docker Desktop

### macOS
1. Descargar Docker Desktop para Mac
2. Arrastrar a Applications
3. Iniciar Docker Desktop

## Características

| Característica | Windows | macOS |
|----------------|---------|-------|
| Contenedores | ✅ | ✅ |
| Kubernetes | ✅ | ✅ |
| Docker Compose | ✅ | ✅ |
| Volumes | ✅ | ✅ |
| WSL2 Backend | ✅ (Windows) | ❌ |
| Hypervisor | Hyper-V/WSL2 | Hypervisor.framework |

## Interfaz

### Dashboard
- Lista de contenedores
- Imágenes
- Volumes
- Networks
- Kubernetes

### Settings

```json
// Configuraciones principales
- Resources: CPU, Memory, Disk
- Docker Engine: Configuración del daemon
- Kubernetes: Habilitar/Configurar
- Experimental: Features en desarrollo
```

## Configuración

### Aumentar Recursos

```
Settings → Resources
- Memory: 4GB+ recomendado
- CPU: 2+ cores
- Disk space: 50GB+ recomendado
```

### Docker Daemon Config

```json
// settings → docker engine
{
  "builder": {
    "gc": {
      "enabled": true,
      "defaultKeepStorage": "20GB"
    }
  },
  "experimental": false,
  "features": {
    "buildkit": true
  }
}
```

## WSL2 (Windows)

```bash
# Ver distribuciones WSL
wsl -l -v

# Instalar Ubuntu en WSL
wsl --install -d Ubuntu

# Actualizar WSL
wsl --update
```

## Troubleshooting

### Windows

```bash
# Reiniciar Docker
docker system reset

# Ver logs
%LOCALAPPDATA%\Docker\log\vm-debug.log

# Habilitar WSL2 si falla
wsl --set-default-version 2
```

### macOS

```bash
# Reset Docker Desktop
# Hold Option + Click en el icono

# Ver logs
~/Library/Containers/com.docker.docker/Data/log
```

## Docker Extensions

```bash
# Extensions disponibles en Docker Desktop
- Docker Scout
- Portainer
- DDEV
- Okteto
- Lens
```

## Kubernetes

```bash
# Habilitar Kubernetes en Docker Desktop
# Settings → Kubernetes → Enable Kubernetes

# Ver contexto
kubectl config get-contexts

# Cambiar a docker-desktop
kubectl config use-context docker-desktop

# Ver nodos
kubectl get nodes
```

## Quick Commands

```bash
# Desde Docker Desktop dashboard
- Start/Stop contenedores
- Ver logs
- Executar terminal
- Remove containers/images
- Clean up
```

## Comparación

| Aspecto | Docker Desktop | Rancher Desktop | Colima |
|---------|---------------|-----------------|--------|
| Costo | Paid/Free | Gratis | Gratis |
| UI | ✅ | ✅ | ❌ |
| Kubernetes | ✅ | ✅ | ❌ |
| WSL2 | ✅ | ✅ | ❌ |
| macOS | ✅ | ✅ | ✅ |

[[Desarrollo de Software/Herramientas/Docker/Docker.md]]
