Guía de Implementación para SmartFinanceTracker

Introducción

Esta guía describe cómo configurar, desarrollar y ejecutar SmartFinanceTracker, nuestro sistema de gestión financiera personal que permite a los usuarios cargar, procesar y analizar sus estados de cuenta bancarios.

Configuración del Entorno de Desarrollo

Frontend (React)

	1.	Clonar el Repositorio:
git clone <URL_DE_TU_REPOSITORIO> SmartFinanceTracker
cd SmartFinanceTracker/client

	2.	Instalar Dependencias:
npm install

	3.	Iniciar el Servidor de Desarrollo:
npm start

Esto lanzará el servidor de desarrollo en localhost:3000.

Backend (Node.js con Express)

	1.	Moverse al Directorio del Backend:
cd ../server

	2.	Instalar Dependencias:
npm install

	3.	Configurar Variables de Entorno:
	•	Crea un archivo .env en la raíz del directorio server/ con las siguientes variables:
DB_HOST=localhost
DB_USER=tu_usuario
DB_PASSWORD=tu_contraseña
DB_NAME=smartfinancetracker
JWT_SECRET=tu_secreto_jwt

	4.	Iniciar el Servidor:
npm start

El backend se ejecutará en localhost:5000.

Estructura del Proyecto

Frontend

	•	/client/src/components: Componentes reutilizables.
	•	/client/src/pages: Páginas o vistas de la aplicación.
	•	/client/src/services: Servicios para hacer peticiones al backend.
	•	/client/src/styles: Estilos CSS/SCSS.
	•	/client/src/utils: Funciones de utilidad.

Backend

	•	/server/controllers: Lógica de negocio.
	•	/server/models: Definición de modelos de datos.
	•	/server/routes: Rutas de la API.
	•	/server/middleware: Middleware para autenticación, validación, etc.
	•	/server/config: Configuración del servidor.

Proceso de Desarrollo

Desarrollo del Frontend

	•	Componentes React: Crear componentes dentro de client/src/components para reutilización.
	•	Rutas: Utilizar react-router-dom para manejar la navegación entre páginas en client/src/pages.
	•	API Calls: Usar axios para comunicarse con el backend desde client/src/services.

Desarrollo del Backend

	•	Rutas y Controladores: Añadir nuevas rutas en server/routes y su lógica correspondiente en server/controllers.
	•	Modelos de Datos: Definir los modelos de datos en server/models usando Sequelize.
	•	Manejo de Archivos: Configurar multer para manejar la carga de archivos PDF.

Integración

	•	Asegúrate de que las peticiones desde el frontend (localhost:3000) puedan acceder al backend (localhost:5000) configurando CORS en server/server.js.

Despliegue

Para Heroku

	1.	Heroku CLI:
	•	Asegúrate de tener Heroku CLI instalado y configurado.
	•	heroku login
	2.	Crear una App en Heroku:
heroku create smartfinancetracker

	3.	Preparar para Despliegue:
	•	Añade heroku-postbuild a tu package.json en la carpeta client:
"scripts": {
  "start": "node server.js",
  "heroku-postbuild": "cd client && npm install && npm run build"
}

	4.	Desplegar:
git push heroku main

	5.	Configurar Variables de Entorno:
	•	Añade las variables de entorno a Heroku:
heroku config:set DB_HOST=<valor> DB_USER=<valor> DB_PASSWORD=<valor> DB_NAME=<valor> JWT_SECRET=<valor>

	6.	Abrir la App:
heroku open

