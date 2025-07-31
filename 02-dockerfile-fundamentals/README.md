# Dockerfile Fundamentals

Este repositorio contiene demostraciones prácticas de los conceptos fundamentales de Dockerfile, incluyendo LABELS, ADD vs COPY, y descarga de archivos desde URLs.

---

## 📋 **Demo-04: Dockerfile - LABELS Instruction**

### **Concepto Teórico:**
Los LABELS en Dockerfile son metadatos que se adjuntan a las imágenes Docker para proporcionar información sobre la imagen, su propósito, versión, mantenedor, etc.

### **Tipos de LABELS:**

#### **1. Custom Labels (Etiquetas Personalizadas)**
```dockerfile
LABEL maintainer="Carlosposada-dev"  
LABEL version="1.0"
LABEL description="A simple Nginx Application"
```

#### **2. OCI Labels (Estándar Open Container Initiative)**
```dockerfile
LABEL org.opencontainers.image.authors="Carlosposada-dev"
LABEL org.opencontainers.image.title="Nginx Alpine Slim Application"
LABEL org.opencontainers.image.description="A lightweight Nginx application built on Alpine."
LABEL org.opencontainers.image.version="2.0"
LABEL org.opencontainers.image.revision="1234567890abcdef" 
LABEL org.opencontainers.image.created="2025-07-30T22:15:00Z"
LABEL org.opencontainers.image.url="https://github.com/stacksimplify/docker-in-a-weekend"
LABEL org.opencontainers.image.source="https://github.com/stacksimplify/docker-in-a-weekend/tree/main/04-Dockerfile-LABELS/Dockerfiles"
LABEL org.opencontainers.image.documentation="https://github.com/stacksimplify/docker-in-a-weekend/tree/main/04-Dockerfile-LABELS"
LABEL org.opencontainers.image.vendor="Cposada"
LABEL org.opencontainers.image.licenses="Nginx-2.0"
```

### **Comandos Útiles:**
```bash
# Ver todos los labels de una imagen
docker inspect <image-name> | grep -A 20 "Labels"

# Filtrar labels específicos
docker inspect <image-name> --format='{{.Config.Labels}}'
```

---

## 📋 **Demo-05: Dockerfile - ADD vs COPY Instructions**

### **Concepto Teórico:**
Tanto `ADD` como `COPY` copian archivos y directorios al contenedor, pero tienen diferencias importantes:

| Aspecto | COPY | ADD |
|---------|------|-----|
| **Funcionalidad básica** | Solo copia archivos/directorios | Copia + funcionalidades adicionales |
| **URLs** | ❌ No soporta | ✅ Descarga automática |
| **Compresión** | ❌ No descomprime | ✅ Descomprime automáticamente |
| **Simplicidad** | ✅ Más simple y predecible | ⚠️ Más complejo, puede ser inesperado |

### **Ejemplos Prácticos:**

#### **COPY - Copia Simple**
```dockerfile
# Copiar archivo local
COPY index.html /usr/share/nginx/html

# Copiar directorio
COPY files/ /usr/share/nginx/html/
```

#### **ADD - Funcionalidades Avanzadas**
```dockerfile
# Descomprimir archivo tar.gz automáticamente
ADD files.tar.gz /usr/share/nginx/html

# Descargar desde URL
ADD https://raw.githubusercontent.com/docker/cli/master/LICENSE /usr/share/nginx/html/docker-license.txt
```

### **Mejores Prácticas:**
- **Usa COPY** para archivos locales simples
- **Usa ADD** solo cuando necesites descargar desde URLs o descomprimir archivos
- **COPY es más predecible** y recomendado por Docker

---

## 📋 **Demo-06: Dockerfile - ADD Fetch from URL (GitHub Release)**

### **Concepto Teórico:**
El comando `ADD` puede descargar archivos directamente desde URLs durante el proceso de build, lo que es útil para obtener archivos externos como licencias, configuraciones, o recursos.

### **Ejemplo Práctico:**
```dockerfile
# Descargar LICENSE de Docker desde GitHub
ADD https://raw.githubusercontent.com/docker/cli/master/LICENSE /usr/share/nginx/html/docker-license.txt
```

### **Consideraciones Importantes:**
- **Build time:** La descarga ocurre durante el build, no en runtime
- **Caché:** Si la URL cambia, Docker no detectará el cambio automáticamente
- **Fallback:** Si la URL no está disponible, el build fallará

---

## 🛠️ **Comandos Prácticos Utilizados**

### **Crear archivo .tar.gz desde la carpeta files:**
```bash
# Navegar a la carpeta files
cd files/

# Crear archivo tar.gz con todos los archivos de la carpeta
tar -czf ../files.tar.gz ./*

# Verificar el contenido del archivo
tar -tzf ../files.tar.gz
```

### **Comandos Docker útiles:**
```bash
# Construir imagen
docker build -t dockerfile-fundamentals .

# Ejecutar contenedor
docker run -p 8080:80 dockerfile-fundamentals

# Acceder al contenedor (Alpine usa sh, no bash)
docker exec -it <container-id> sh

# Ver archivos en el contenedor
ls -la /usr/share/nginx/html/

# Ver labels de la imagen
docker inspect dockerfile-fundamentals --format='{{.Config.Labels}}'
```

---

## 🔧 **Solución al Problema de Permisos de Nginx**

### **Problema:**
Nginx no podía leer el archivo `docker-license.txt` descargado desde URL, causando errores 403.

### **Causa:**
Los archivos descargados con `ADD` desde URLs mantienen los permisos originales del servidor web, que pueden no ser legibles por Nginx.

### **Solución:**
```dockerfile
# Descargar el archivo
ADD https://raw.githubusercontent.com/docker/cli/master/LICENSE /usr/share/nginx/html/docker-license.txt

# Cambiar permisos para que Nginx pueda leerlo
RUN chmod 644 /usr/share/nginx/html/docker-license.txt
```

### **Explicación:**
- **644** = `rw-r--r--` (propietario puede leer/escribir, grupo y otros pueden leer)
- Nginx necesita permisos de lectura para servir archivos estáticos
- Los archivos descargados desde URLs pueden tener permisos restrictivos

---

## 📁 **Estructura del Proyecto**

```
02-dockerfile-fundamentals/
├── dockerfile                    # Dockerfile principal con ejemplos
├── index.html                    # Página principal
├── files.tar.gz                  # Archivo comprimido con archivos web
├── files/                        # Carpeta con archivos web
│   ├── index.html               # Página principal de la carpeta files
│   ├── index-1.html             # Demo de ADD con tar
│   └── index-2.html             # Demo de ADD con URL
└── README.md                     # Este archivo
```

---

## 🚀 **Cómo Ejecutar**

1. **Construir la imagen:**
   ```bash
   docker build -t dockerfile-fundamentals .
   ```

2. **Ejecutar el contenedor:**
   ```bash
   docker run -p 8080:80 dockerfile-fundamentals
   ```

3. **Acceder a la aplicación:**
   - Página principal: http://localhost:8080/
   - Demo ADD tar: http://localhost:8080/index-1.html
   - Demo ADD URL: http://localhost:8080/index-2.html

---

## 📚 **Recursos Adicionales**

- [Dockerfile Reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Best Practices](https://docs.docker.com/develop/dev-best-practices/)
- [OCI Labels Specification](https://github.com/opencontainers/image-spec/blob/main/annotations.md)
- [Nginx Configuration](https://nginx.org/en/docs/)

---

**Autor:** Carlosposada-dev  
**Versión:** 2.0  
**Fecha:** 2025-01-30 