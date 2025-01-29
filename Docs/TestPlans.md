Plan de Pruebas para SmartFinanceTracker

Introducción

Este documento describe el plan de pruebas para SmartFinanceTracker, abarcando desde pruebas unitarias hasta pruebas de extremo a extremo, asegurando la calidad y funcionalidad del producto.

Objetivos del Testing

	•	Verificar que todas las funcionalidades descritas en el PRD funcionen según lo previsto.
	•	Asegurar que la aplicación sea robusta, segura, y de alta calidad.
	•	Detectar y corregir defectos lo antes posible en el ciclo de desarrollo.
	•	Proveer confianza en la estabilidad y rendimiento de la aplicación antes del lanzamiento.

Tipos de Pruebas

1. Pruebas Unitarias

	•	Objetivo: Verificar que cada función o método funcione correctamente de manera aislada.
	•	Herramienta: Jest para JavaScript.
	•	Cobertura:
	•	Frontend: Componentes React, hooks, servicios.
	•	Backend: Controladores, servicios, middleware.
	•	Ejemplo:

describe('TransactionController', () => {
    describe('uploadPDF', () => {
        it('should process PDF and return success message', async () => {
            // Test setup and assertions
        });
    });
});

2. Pruebas de Integración

	•	Objetivo: Asegurar que las diferentes partes del sistema trabajen juntas correctamente.
	•	Herramienta: Supertest para testear rutas de Express.
	•	Cobertura:
	•	Comunicación entre frontend y backend.
	•	Integración de la API de Grok 2 para la categorización.
	•	Ejemplo:

const request = require('supertest');
const app = require('../server');

describe('Transaction Routes', () => {
    it('responds with json', (done) => {
        request(app)
            .get('/api/transactions')
            .set('Accept', 'application/json')
            .expect('Content-Type', /json/)
            .expect(200, done);
    });
});

3. Pruebas de Extremo a Extremo (E2E)

	•	Objetivo: Probar la aplicación como lo haría un usuario final, de principio a fin.
	•	Herramienta: Cypress para pruebas E2E en navegadores.
	•	Cobertura:
	•	Flujo completo desde la carga de un PDF hasta la exportación de datos.
	•	Interacciones de usuario, navegación entre páginas.
	•	Ejemplo:

describe('Transaction Workflow', () => {
    it('loads transactions and displays them', () => {
        cy.visit('/transactions');
        cy.get('button').contains('Load Transactions').click();
        cy.get('ul li').should('have.length', 5);  // Assuming 5 transactions are loaded
    });
});

Cronograma de Testing

	•	Desarrollo: Pruebas unitarias e integración se ejecutarán durante el desarrollo de cada feature.
	•	Pre-lanzamiento: Una semana dedicada a pruebas E2E y pruebas de regresión antes del lanzamiento.
	•	Post-lanzamiento: Pruebas continuas basadas en feedback de usuarios beta.

Casos de Prueba

Frontend

	•	Cargar PDF y ver feedback visual.
	•	Navegar entre páginas.
	•	Interactuar con la interfaz de categorización de transacciones.

Backend

	•	Subir y procesar un PDF.
	•	Crear, leer, actualizar y eliminar transacciones.
	•	Exportar datos en diferentes formatos.

Integración

	•	Verificar que la API de Grok 2 responda correctamente.
	•	Comprobar la persistencia de datos en la base de datos.

Reporte y Manejo de Bugs

	•	Herramientas: GitHub Issues para reportar y gestionar bugs.
	•	Proceso:
	•	Bugs se reportan con una descripción detallada, pasos para reproducir el problema, y capturas de pantalla si es necesario.
	•	Asignación de prioridad basada en impacto y urgencia.
	•	Resolución de bugs en sprints de desarrollo, con pruebas de regresión para asegurar que la corrección no introduce nuevos problemas.
