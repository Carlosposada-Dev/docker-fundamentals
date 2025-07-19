# Docker Fundamentals - Estructura Organizada

Este repositorio contiene una estructura organizada para estudiar los conceptos fundamentales de Docker, basada en el curso "Docker in a Weekend" de StackSimplify.

## 📁 Estructura del Repositorio

### 🚀 **01-getting-started/**
Conceptos básicos e instalación
- `01-docker-desktop-install/` - Instalación de Docker Desktop
- `02-pull-run-docker-image/` - Pull y ejecución de imágenes desde Docker Hub
- `03-build-push-dockerhub/` - Construir y subir imágenes a Docker Hub

### 📝 **02-dockerfile-fundamentals/**
Conceptos básicos de Dockerfile
- `04-dockerfile-labels/` - Uso de LABELS en Dockerfile
- `05-dockerfile-add-vs-copy/` - Diferencias entre ADD y COPY
- `06-dockerfile-add-url/` - ADD para obtener archivos desde URL
- `07-dockerfile-arg/` - Uso de ARG en Dockerfile
- `08-dockerfile-run-expose/` - RUN y EXPOSE
- `09-dockerfile-arg-env-cmd-workdir/` - ARG, ENV, CMD y WORKDIR
- `10-dockerfile-cmd/` - Comando CMD
- `11-dockerfile-entrypoint/` - Comando ENTRYPOINT
- `12-dockerfile-healthcheck/` - Health checks
- `13-dockerfile-user/` - Gestión de usuarios

### 🌐 **03-networking-ports/**
Redes y puertos
- `14-docker-ports/` - Gestión de puertos en Docker

### 💾 **04-volumes-storage/**
Volúmenes y almacenamiento
- `15-docker-volume-basics/` - Conceptos básicos de volúmenes
- `16-docker-volumes-containers/` - Volúmenes con contenedores
- `17-populate-volumes-containers/` - Poblar volúmenes usando contenedores
- `18-mount-volume-subdirectory/` - Montar subdirectorios de volúmenes
- `19-docker-bind-mounts/` - Bind mounts básicos
- `20-docker-bind-mounts-readonly/` - Bind mounts en modo solo lectura
- `21-volume-vs-bindmounts-nonempty/` - Volúmenes vs Bind Mounts con directorios no vacíos
- `22-docker-tmpfs-mount/` - Montajes tmpfs

### 🔧 **05-multi-container-apps/**
Aplicaciones multi-contenedor
- `23-docker-multi-container-apps/` - Aplicaciones multi-contenedor con comandos Docker

### 🎯 **06-docker-compose-basics/**
Docker Compose básico
- `24-docker-compose-volumes-env/` - Volúmenes y variables de entorno en Compose
- `25-docker-compose-named-volume/` - Volúmenes nombrados en Compose
- `26-docker-compose-ums-stack/` - Stack UMS (aplicación web + MySQL)

### 🚀 **07-docker-compose-advanced/**
Docker Compose avanzado
- `27-docker-compose-deploy/` - Despliegue y escalado con Compose
- `28-docker-compose-networks/` - Redes en Docker Compose
- `29-docker-compose-healthchecks/` - Health checks en Compose
- `30-docker-compose-startup-order/` - Orden de inicio con condiciones
- `31-docker-compose-profiles/` - Perfiles en Docker Compose
- `32-docker-compose-links/` - Enlaces entre servicios
- `33-docker-compose-aliases/` - Alias en Docker Compose
- `34-docker-compose-build/` - Construcción de imágenes en Compose

### 🔄 **08-development-workflow/**
Flujo de desarrollo
- `35-docker-compose-develop-watch-restart/` - Desarrollo con watch y restart
- `36-docker-compose-develop-watch-rebuild/` - Desarrollo con watch y rebuild

### 🏗️ **09-advanced-builds/**
Construcción avanzada de imágenes
- `37-docker-build-buildkit-buildx/` - BuildKit y buildx CLI
- `38-docker-build-multiplatform/` - Imágenes multi-plataforma
- `39-docker-build-cloud/` - Construcción en la nube
- `40-docker-build-multi-stage/` - Construcciones multi-etapa

## 🎯 Progresión de Aprendizaje

### **Fase 1: Fundamentos (01-03)**
- Instalación y configuración básica
- Conceptos fundamentales de imágenes y contenedores
- Primeros pasos con Docker Hub

### **Fase 2: Dockerfiles (04-13)**
- Creación y optimización de Dockerfiles
- Instrucciones esenciales y mejores prácticas
- Gestión de usuarios y health checks

### **Fase 3: Redes y Almacenamiento (14-22)**
- Configuración de redes y puertos
- Persistencia de datos con volúmenes
- Diferentes tipos de montajes

### **Fase 4: Aplicaciones Complejas (23-40)**
- Orquestación con Docker Compose
- Aplicaciones multi-servicio
- Flujos de desarrollo avanzados
- Construcción optimizada de imágenes

## 🚀 Cómo usar este repositorio

1. **Sigue la numeración**: Cada módulo está numerado para progresión lógica
2. **Cada carpeta contiene**:
   - `README.md` con explicaciones detalladas
   - `Dockerfile` (cuando aplique)
   - `docker-compose.yml` (cuando aplique)
   - Scripts y ejemplos prácticos
   - Documentación específica del concepto

## 📚 Mapeo del Curso Original

| Módulo Original | Nueva Estructura | Concepto |
|----------------|------------------|----------|
| 01-03 | 01-getting-started | Fundamentos |
| 04-13 | 02-dockerfile-fundamentals | Dockerfiles |
| 14 | 03-networking-ports | Redes |
| 15-22 | 04-volumes-storage | Almacenamiento |
| 23 | 05-multi-container-apps | Multi-contenedor |
| 24-26 | 06-docker-compose-basics | Compose básico |
| 27-34 | 07-docker-compose-advanced | Compose avanzado |
| 35-36 | 08-development-workflow | Desarrollo |
| 37-40 | 09-advanced-builds | Construcción avanzada |

## 🎯 Objetivos de Aprendizaje

Al completar este repositorio, serás capaz de:
- ✅ Instalar y configurar Docker Desktop
- ✅ Trabajar con imágenes y contenedores
- ✅ Crear Dockerfiles optimizados
- ✅ Gestionar volúmenes y redes
- ✅ Orquestar aplicaciones con Docker Compose
- ✅ Implementar flujos de desarrollo eficientes
- ✅ Construir imágenes multi-plataforma
- ✅ Desplegar aplicaciones en producción

---

**Nota**: Esta estructura mantiene la progresión lógica del curso original pero organiza los conceptos de manera más coherente y fácil de seguir. 