Guía de Estilo de Código para SmartFinanceTracker

Introducción

Este documento define las convenciones de estilo de código que se deben seguir en el desarrollo de SmartFinanceTracker. Adherirse a estas guías asegura la consistencia, legibilidad, y mantenibilidad del código.

General

	•	Lenguaje: JavaScript (ES6+), con TypeScript para mejor tipado en el backend si se decide usar.
	•	Formateo: Utilizaremos Prettier para el formateo automático del código, garantizando una consistencia visual.

JavaScript/TypeScript

Estilo de Código

	•	Indentación: 2 espacios.
	•	Semicolons: No requeridos, pero permitidos por consistencia.
	•	Comillas: Comillas simples (').

Nombres

	•	Funciones y Variables: camelCase (uploadPDF, transactionAmount).
	•	Constantes: SCREAMING_SNAKE_CASE (API_URL, MAX_TRANSACTIONS).
	•	Clases: PascalCase (TransactionModel, UserService).

Funciones

	•	Parámetros: Si una función tiene más de 3 parámetros, considerar el uso de un objeto destructurado.

function processTransactions({ userId, transactions, bank }) {
    // ...
}

	•	Arrow Functions: Preferibles para funciones cortas.

const categorize = (transaction) => {
    // ...
};

Importaciones

	•	Preferir import sobre require:

import express from 'express';
import { Transaction } from '../models/Transaction';

Espaciado

	•	Espacios alrededor de operadores: let sum = 1 + 2;
	•	No espacios antes de paréntesis: if (condition) {

Comentarios

	•	JSDoc para funciones: Especialmente para funciones complejas o de API.

/**
 * Uploads and processes a PDF statement.
 * @param {Object} req - Express request object
 * @param {Object} res - Express response object
 * @returns {Promise<void>}
 */
async function uploadPDF(req, res) {
    // ...
}

CSS

	•	Formateo: Seguir el estilo de CSS en cascada, con selectores de menor a mayor especificidad.
	•	Nombres de clases: BEM (Block Element Modifier) para componentes React.

.button {
  /* Block */
}
.button--primary {
  /* Modifier */
}
.button__icon {
  /* Element */
}

	•	Unidades: Preferir rem para tamaños de fuente y espaciados.

HTML

	•	Atributos: Nombres de atributos en minúsculas, valores en comillas dobles.

<div class="transaction-list" aria-label="List of transactions">
    <!-- ... -->
</div>

Git

Commit Messages

	•	Formato: <tipo>(ámbito): <descripción>
	•	Tipos: feat (nueva característica), fix (corrección de bug), docs (solo documentación), style (formato, no afecta código), refactor, test, chore (mantenimiento).
	•	Ejemplo: feat(frontend): Implement user authentication

Ramas

	•	Nombres de ramas: tipo-de-cambio-descripción (por ejemplo, bugfix/login-issue)
	•	Rama principal: main o master, dependiendo de la configuración del proyecto.

Herramientas de Linting

	•	ESLint: Configurar para JavaScript/TypeScript.
	•	Stylelint: Para CSS.
