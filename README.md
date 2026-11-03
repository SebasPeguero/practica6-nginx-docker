# Práctica 6: Ejecutar servidor web Nginx con Docker Compose

**Estudiante:** Sebastián Peguero  
**Matrícula:** 2025-1172  
**Materia:** Electiva II  
**Repositorio:** [practica6-nginx-docker](https://github.com/SebasPeguero/practica6-nginx-docker)

---

## 🎯 Objetivo de la Práctica
Crear y ejecutar un servidor web Nginx localmente en la computadora utilizando **Docker Compose**, enlazando los archivos web mediante volúmenes de Docker para reflejar cambios dinámicamente.

---

## 📁 Estructura del Proyecto
```text
practica6-nginx-docker/
├── docker-compose.yml   # Definición del servicio Nginx, puertos y volúmenes
├── README.md            # Documentación e instrucciones
└── src/
    └── index.html       # Página web Hola Mundo servida por Nginx
```

---

## ⚙️ Configuración de Docker Compose (`docker-compose.yml`)
```yaml
services:
  web:
    image: nginx:alpine
    container_name: servidor-nginx-practica6
    restart: unless-stopped
    ports:
      - "8080:80"
    volumes:
      - ./src:/usr/share/nginx/html:ro
```

### Explicación de la configuración:
* **`image: nginx:alpine`**: Utiliza la imagen ligera oficial de Nginx basada en Alpine Linux.
* **`container_name: servidor-nginx-practica6`**: Asigna un nombre descriptivo al contenedor.
* **`ports: ["8080:80"]`**: Mapea el puerto local `8080` de la máquina al puerto `80` interno del contenedor.
* **`volumes: [./src:/usr/share/nginx/html:ro]`**: Mapea el directorio local `./src` al directorio raíz de Nginx (`/usr/share/nginx/html`) dentro del contenedor en modo solo lectura (`:ro`).

---

## 🚀 Pasos para ejecutar el proyecto

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/SebasPeguero/practica6-nginx-docker.git
   cd practica6-nginx-docker
   ```

2. **Iniciar el contenedor en segundo plano con Docker Compose:**
   ```bash
   docker compose up -d
   ```

3. **Verificar el funcionamiento:**
   Abrir en el navegador web:
   ```text
   http://localhost:8080
   ```
   O mediante consola:
   ```bash
   curl http://localhost:8080
   ```

4. **Ver estado de los contenedores:**
   ```bash
   docker compose ps
   ```

5. **Detener el contenedor:**
   ```bash
   docker compose down
   ```
