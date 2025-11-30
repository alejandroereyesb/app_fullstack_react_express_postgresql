# Proyecto Fullstack con Docker y Render

Este proyecto es una aplicación fullstack que utiliza un backend en Node.js con Express y una base de datos PostgreSQL. El frontend está construido con Vite. Todo el sistema está dockerizado para facilitar su despliegue y ejecución.

---

## **Estructura del Proyecto**

```
app_fullstack/
├── backend/          # Código del backend (Node.js + Express)
│   ├── config/       # Configuración de la base de datos y otros ajustes
│   ├── models/       # Modelos de datos
│   ├── routes/       # Rutas de la API
│   ├── seeder.js     # Script para inicializar la base de datos
│   └── ...
├── frontend/         # Código del frontend (Vite)
│   ├── src/          # Código fuente del frontend
│   └── ...
├── Dockerfile        # Configuración de Docker para el sistema completo
├── docker-compose.yml # Orquestación de servicios con Docker Compose
└── README.md         # Documentación del proyecto
```

---

## **Requisitos Previos**

- **Docker**: Asegúrate de tener Docker instalado en tu sistema.
- **Docker Compose**: Necesario para orquestar los servicios.
- **Render**: Cuenta en Render para el despliegue.

---

## **Comandos Útiles**

### **Construir y ejecutar el sistema con Docker Compose**
```bash
docker-compose up --build
```
- Esto construirá las imágenes y levantará los contenedores.

### **Parar los contenedores**
```bash
docker-compose down
```
- Detiene y elimina los contenedores.

### **Ver los contenedores en ejecución**
```bash
docker ps
```

### **Acceder a un contenedor**
```bash
docker exec -it <container_id> sh
```
- Reemplaza `<container_id>` con el ID del contenedor al que deseas acceder.

---

## **Variables de Entorno**

Las variables de entorno se configuran en archivos `.env`. Hay un archivo de ejemplo en `backend/.env.example`. Crea los siguientes archivos según el entorno:

- **Desarrollo**: `.env.development`
- **Producción**: `.env.production`
- **Test**: `.env.test`
- **Staging**: `.env.staging`

Ejemplo de archivo `.env`:
```env
# Datos BBDD PostgreSQL
PG_USER=postgres
PG_HOST=localhost
PG_DATABASE=postgres
PG_PASSWORD=123456
PG_PORT=5433
PG_SSL=false

# Servidor
PORT=3000

# Entorno
NODE_ENV=development
```

---

## **Despliegue en Render**

### **Pasos para desplegar**
1. **Crear un servicio para el backend**:
   - Sube el contenido de la carpeta `backend` a un repositorio en GitHub.
   - En Render, crea un nuevo servicio web y conecta el repositorio.
   - Configura las variables de entorno necesarias en la sección "Environment".

2. **Crear un servicio para el frontend**:
   - Sube el contenido de la carpeta `frontend` a un repositorio en GitHub.
   - En Render, crea un nuevo servicio web estático y conecta el repositorio.
   - Configura el comando de build: `npm run build`.
   - Configura el directorio de salida: `dist`.

3. **Configurar la base de datos**:
   - En Render, crea una nueva base de datos PostgreSQL.
   - Copia las credenciales y configúralas en las variables de entorno del backend.

4. **Desplegar**:
   - Render se encargará de construir y desplegar automáticamente los servicios al hacer push en el repositorio.

---

## **Notas Adicionales**

- Asegúrate de que el backend sirva correctamente el frontend en producción.
- Usa rutas relativas (`/api`) para evitar problemas con las URLs en diferentes entornos.
- Verifica los logs de los servicios en Render para solucionar problemas.

---

## **Licencia**

Este proyecto está bajo la licencia MIT.