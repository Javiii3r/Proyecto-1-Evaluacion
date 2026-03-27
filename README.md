<div align="center">
   <h1>🏋️ Elevion Fitness</h1>

   ### Plataforma fullstack para la gestión de ejercicios de gimnasio

   [![Node.js](https://img.shields.io/badge/Node.js-339933.svg?logo=nodedotjs&logoColor=white)](https://nodejs.org/)
   [![Express](https://img.shields.io/badge/Express-5.x-000000.svg?logo=express&logoColor=white)](https://expressjs.com/)
   [![SQLite](https://img.shields.io/badge/SQLite-003B57.svg?logo=sqlite&logoColor=white)](https://www.sqlite.org/)
   [![Knex.js](https://img.shields.io/badge/Knex.js-Query%20Builder-e16426.svg)](https://knexjs.org/)
   [![HTML5](https://img.shields.io/badge/HTML5-E34F26.svg?logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
   [![CSS3](https://img.shields.io/badge/CSS3-1572B6.svg?logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
   [![Postman](https://img.shields.io/badge/Postman-Ready-FF6C37.svg?logo=postman&logoColor=white)](https://www.postman.com/)

   <p align="center">
      <strong>Una API REST robusta y una interfaz web moderna</strong> para crear, consultar, actualizar y eliminar ejercicios de gimnasio, con persistencia en SQLite y un frontend responsive listo para usar.
   </p>
</div>

---

## 📋 Descripción

**Elevion Fitness** es una aplicación web fullstack desarrollada como proyecto de la 1ª Evaluación del ciclo **DAW (Desarrollo de Aplicaciones Web)**. Está compuesta por dos módulos independientes:

- **Back-End:** API REST con Express.js que expone un CRUD completo sobre la entidad `exercises`, utilizando SQLite como base de datos persistente gestionada mediante Knex.js como query builder.
- **Front-End:** Interfaz web estática con HTML5 semántico y CSS3 moderno, con página principal interactiva, galería de instalaciones, sección de experiencias de usuarios y formulario de registro de ejercicios.

## ✨ Características

- 💪 **CRUD Completo** — Crear, leer, actualizar y eliminar ejercicios mediante endpoints REST
- 🗄️ **Base de datos persistente** — SQLite inicializado automáticamente en el primer arranque
- ✅ **Validaciones de datos** — Campos obligatorios, tipos numéricos y unicidad de nombre
- 📄 **Respuestas JSON estándar** — Códigos HTTP correctos en cada situación
- 🌐 **Frontend responsive** — Diseño adaptado a escritorio y móvil con menú hamburguesa
- 🧩 **Arquitectura por capas** — Routes → Controller → Service → Database
- 📬 **Colección Postman incluida** — Lista para importar y probar los 5 endpoints
- ⚡ **Sin configuración extra** — La base de datos se crea sola al iniciar el servidor

## 🛠️ Tecnologías Utilizadas

### Back-End

| Tecnología | Versión | Enlace |
|------------|---------|--------|
| **Node.js** | LTS | [nodejs.org](https://nodejs.org/) |
| **Express.js** | ^5.1.0 | [expressjs.com](https://expressjs.com/) |
| **Knex.js** | ^3.1.0 | [knexjs.org](https://knexjs.org/) |
| **SQLite3** | ^5.1.7 | [sqlite.org](https://www.sqlite.org/) |

### Front-End

| Tecnología | Uso |
|------------|-----|
| **HTML5** | Estructura semántica de las páginas |
| **CSS3** | Estilos personalizados y diseño responsive |
| **Ionicons** | Iconografía de la interfaz |
| **Font Awesome** | Iconos de redes sociales |

## 📦 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

| Requisito | Versión | Enlace |
|-----------|---------|--------|
| **Node.js** | LTS recomendada | [Descargar](https://nodejs.org/) |
| **npm** | Incluido con Node.js | — |
| **Postman** (opcional) | Última estable | [Descargar](https://www.postman.com/downloads/) |
| **Navegador moderno** | Chrome / Firefox / Edge | — |

## 🚀 Instalación y Arranque

### 1. Clona el Repositorio

```bash
git clone https://github.com/Javiii3r/Proyecto-1-Evaluacion.git
cd Proyecto-1-Evaluacion
```

### 2. Instala las Dependencias del Backend

```bash
cd Back-End/API-gym
npm install
```

### 3. Inicia el Servidor

```bash
npm start
```

✅ **La API estará disponible en** `http://localhost:8080`

> La base de datos SQLite se crea automáticamente en el primer arranque. No se requiere ninguna configuración adicional.

### 4. Abre el Frontend

Abre directamente en el navegador el archivo:

```
Front-End/Principal.html
```

## 🔌 API — Endpoints

Base URL: `http://localhost:8080/api`

| Método | Endpoint | Descripción | Código éxito |
|--------|----------|-------------|:------------:|
| `GET` | `/exercises` | Lista todos los ejercicios | `200` |
| `GET` | `/exercises/:id` | Obtiene un ejercicio por ID | `200` |
| `POST` | `/exercises` | Crea un nuevo ejercicio | `201` |
| `PUT` | `/exercises/:id` | Actualiza un ejercicio existente | `204` |
| `DELETE` | `/exercises/:id` | Elimina un ejercicio por ID | `204` |

### Modelo de Datos

| Campo | Tipo | Obligatorio | Default | Descripción |
|-------|------|:-----------:|---------|-------------|
| `id` | `integer` | Auto | — | Identificador único (autoincremental) |
| `name` | `string` | ✅ | — | Nombre del ejercicio (único) |
| `duration` | `integer` | ✅ | — | Duración en minutos |
| `difficulty` | `string` | ✅ | — | Nivel: `easy`, `medium`, `hard` |
| `calories` | `integer` | ❌ | `0` | Calorías quemadas |
| `date` | `datetime` | ❌ | Fecha actual | Fecha del ejercicio |
| `active` | `boolean` | ❌ | `true` | Si el ejercicio está activo |
| `notes` | `text` | ❌ | `""` | Notas adicionales |

### Ejemplo de Body (POST / PUT)

```json
{
  "name": "Press Banca",
  "duration": 45,
  "difficulty": "medium",
  "calories": 250,
  "date": "2024-01-15",
  "active": true,
  "notes": "Ejercicio de pecho principal"
}
```

### Códigos de Respuesta

| Código | Título | Cuándo ocurre |
|--------|--------|---------------|
| `200 OK` | — | GET exitoso |
| `201 Created` | — | POST exitoso |
| `204 No Content` | — | PUT o DELETE exitoso |
| `400 Bad Request` | `bad-request` | Faltan campos obligatorios o tipos incorrectos |
| `404 Not Found` | `not-found` | El ejercicio con ese ID no existe |
| `409 Conflict` | `conflict` | Ya existe un ejercicio con ese nombre |

## 📁 Estructura del Proyecto

```text
Proyecto-1-Evaluacion/
│
├── Back-End/
│   └── API-gym/
│       ├── src/
│       │   ├── app.js                      # Punto de entrada — configura Express y arranca el servidor
│       │   ├── configuration/
│       │   │   ├── database.js             # Conexión Knex + SQLite
│       │   │   └── init-db.js              # Creación automática de la tabla exercises
│       │   ├── routes/
│       │   │   └── exercises.js            # Definición de rutas REST
│       │   ├── controller/
│       │   │   └── exercises.js            # Lógica de control, validaciones y respuestas HTTP
│       │   └── service/
│       │       └── exercises.js            # Operaciones CRUD sobre la base de datos
│       ├── gym.postman_collection.json     # Colección Postman lista para importar
│       ├── package.json
│       └── .gitignore
│
└── Front-End/
    ├── Principal.html                      # Página principal de Elevion Fitness
    ├── Registro.html                       # Formulario de creación de ejercicios
    ├── StylesPrincipal.css                 # Estilos de la página principal
    ├── RegistroStyles.css                  # Estilos del formulario de registro
    ├── Imagenes/                           # Imágenes del sitio (galería, perfiles, logo)
    └── FaviconUsuario/                     # Favicon e iconos de la aplicación
```

### Flujo de Datos

```text
Cliente HTTP / Postman / Frontend
         ↓
   Express Router
  (routes/exercises.js)
         ↓
   Controller Layer
 (controller/exercises.js)
   Validaciones + HTTP
         ↓
   Service Layer
  (service/exercises.js)
   Queries con Knex
         ↓
   SQLite Database
   (exercises.db)
```

## 📬 Pruebas con Postman

El proyecto incluye una colección de Postman lista para importar con los 5 endpoints preconfigurados:

```
Back-End/API-gym/gym.postman_collection.json
```

**Pasos para importarla:**
1. Abre Postman
2. Haz clic en **Import**
3. Selecciona el archivo `gym.postman_collection.json`
4. Asegúrate de que el servidor está corriendo en `localhost:8080`

### Checklist de Validación

```text
[ ] GET /api/exercises         → devuelve array de ejercicios
[ ] GET /api/exercises/:id     → devuelve el ejercicio o 404
[ ] POST /api/exercises        → crea y devuelve 201
[ ] PUT /api/exercises/:id     → actualiza y devuelve 204
[ ] DELETE /api/exercises/:id  → elimina y devuelve 204
[ ] POST sin campos            → devuelve 400 bad-request
[ ] POST nombre duplicado      → devuelve 409 conflict
```

## 🌐 Frontend

El frontend es una aplicación web estática que no requiere instalación. Se abre directamente en el navegador.

### Páginas

| Archivo | Descripción |
|---------|-------------|
| `Principal.html` | Página principal con galería de instalaciones, menú de opciones, experiencias de usuarios y footer completo |
| `Registro.html` | Formulario para registrar un nuevo ejercicio con todos sus atributos |

### Características del Diseño

- 📱 Diseño **responsive** con menú hamburguesa en móvil
- 🖼️ Galería de imágenes de las instalaciones del gimnasio
- ⭐ Sección de experiencias con valoraciones por estrellas
- 🔗 Navegación con anclas a las secciones de la aplicación
- 📣 Footer con redes sociales, enlaces rápidos y formulario de inicio de sesión

---

## 👤 Autor

<div align="center">
   <table>
      <tr>
         <td align="center">
            <a href="https://github.com/Javiii3r">
               <img src="https://avatars.githubusercontent.com/u/232877625?v=4" width="100px;" alt="Javi"/><br />
               <sub><b>Javi</b></sub>
            </a>
            <br />
            <p><strong>Full Stack Developer</strong></p>
         </td>
      </tr>
   </table>
</div>

## 🏆 Créditos y Agradecimientos

<div align="center">
   <p>Proyecto desarrollado como parte de la <strong>1ª Evaluación</strong> del ciclo formativo <strong>DAW — Desarrollo de Aplicaciones Web</strong>.</p>

   **Desarrollado con ❤️ para Elevion Fitness**

   ---

   Agradecimientos a:
   - **Express.js** por su simplicidad y potencia como framework HTTP
   - **Knex.js** por hacer las consultas SQL elegantes y mantenibles
   - **La comunidad open source** por las herramientas e inspiración
</div>

---

<div align="center">

   [⬆ Volver al inicio](#️-elevion-fitness)

</div>