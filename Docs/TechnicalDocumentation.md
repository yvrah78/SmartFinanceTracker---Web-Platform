Documentación Técnica de SmartFinanceTracker

Arquitectura del Sistema

SmartFinanceTracker se estructura en un modelo cliente-servidor, con el frontend en React y el backend en Node.js con Express, utilizando PostgreSQL como base de datos.

	•	Frontend: React con hooks para manejar el estado y la lógica de la aplicación.
	•	Backend: Node.js con Express para gestionar las solicitudes HTTP y Sequelize como ORM para interactuar con PostgreSQL.
	•	Base de Datos: PostgreSQL para almacenar datos de usuarios y transacciones.

Componentes Principales

Frontend

	•	Componentes: Reutilizables para la interfaz de usuario, como UploadPDF, TransactionList, y FinancialAnalysis.
	•	Páginas: Vistas principales como Home, Dashboard, Transactions.
	•	Servicios: apiService.js para manejar las peticiones al backend.

Backend

	•	Rutas: Manejo de endpoints para la API RESTful, definidos en server/routes/.
	•	Controladores: Lógica de negocio ubicada en server/controllers/.
	•	Modelos: Estructura de datos en server/models/, usando Sequelize para ORM.

Modelos de Datos

Usuario

const User = sequelize.define('User', {
    id: { type: DataTypes.INTEGER, primaryKey: true, autoIncrement: true },
    username: { type: DataTypes.STRING, unique: true, allowNull: false },
    password: { type: DataTypes.STRING, allowNull: false },
    email: { type: DataTypes.STRING, unique: true, allowNull: false }
});

Transacción

const Transaction = sequelize.define('Transaction', {
    id: { type: DataTypes.INTEGER, primaryKey: true, autoIncrement: true },
    date: { type: DataTypes.DATE, allowNull: false },
    description: { type: DataTypes.STRING, allowNull: false },
    amount: { type: DataTypes.DECIMAL(10, 2), allowNull: false },
    category: { type: DataTypes.STRING, allowNull: true },
    userId: { type: DataTypes.INTEGER, references: { model: 'Users', key: 'id' }, allowNull: false }
});

Rutas API

Autenticación

	•	POST /register: Registrar un nuevo usuario.
	•	POST /login: Autenticación de usuario existente.

Transacciones

	•	POST /api/transactions/upload: Subir un PDF de estado de cuenta.
	•	GET /api/transactions: Obtener todas las transacciones del usuario.
	•	PUT /api/transactions/:id: Actualizar la categoría de una transacción.
	•	GET /api/transactions/category-summary: Obtener un resumen de gastos por categoría.
	•	GET /api/transactions/export: Exportar datos de transacciones en Excel o PDF.

Seguridad

	•	Autenticación: JWT (JSON Web Tokens) para autenticar y autorizar usuarios.
	•	CORS: Configurado para permitir peticiones desde el frontend en React.
	•	HTTPS: Todas las comunicaciones están cifradas.
	•	Cifrado de Datos: En reposo usando PostgreSQL y en tránsito con HTTPS.
	•	Validación de Datos: Usando express-validator para prevenir inyecciones y validar datos de entrada.

Manejo de Errores

	•	Middleware de Errores: Implementado para manejar y responder a errores de manera uniforme.
	•	Logging: Uso de winston o morgan para registrar errores y solicitudes en producción.

Buenas Prácticas de Código

	•	Estándares de Código: Seguir las guías de estilo de JavaScript (Airbnb o Standard).
	•	Testing: Implementar pruebas unitarias con Jest, integración con Supertest, y E2E con Cypress.
	•	Documentación Interna: Comentarios en el código donde sea necesario para explicaciones complejas.

Consideraciones de Desempeño

	•	Optimización de Consultas: Usar índices en PostgreSQL para mejorar el rendimiento de consultas frecuentes.
	•	Caching: Implementar caching para datos que no cambien con frecuencia.
