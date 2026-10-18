# Autoescola Quiz 🚗

**Web para practicar el examen teórico de conducir** con preguntas tipo test, y un panel de administración para que el profesorado gestione las preguntas.

Proyecto individual del CFGS de Desarrollo de Aplicaciones Web (Institut Pedralbes), alineado con el ODS 4 de la ONU, Educación de calidad: recursos educativos digitales, abiertos y accesibles.

**Demo:** [tr-0-daw-alpha.vercel.app](https://tr-0-daw-alpha.vercel.app)

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)

---

## Funcionalidades

**Modo práctica**
- Test de 10 preguntas aleatorias, con imagen cuando la pregunta lo necesita.
- Contrarreloj de 30 segundos con barra de progreso que cambia de color al acercarse el final. Al agotarse el tiempo, las respuestas se bloquean.
- Marcador de preguntas respondidas y puntuación final.

**Panel de administración**
- Crear, editar y eliminar preguntas con sus respuestas, marcando la correcta.
- Subida de imágenes para cada pregunta.

---

## Stack y arquitectura

| Capa | Tecnologías |
|---|---|
| **Frontend** | HTML, CSS y JavaScript sin frameworks (SPA sencilla) |
| **Backend** | API REST en PHP con `mysqli` |
| **Base de datos** | MySQL / MariaDB |
| **Calidad** | GitHub Actions y SonarQube |

La API devuelve siempre JSON. El endpoint público de preguntas no envía cuál es la respuesta correcta; solo el modo administración la recibe.

| Endpoint | Método | Qué hace |
|---|---|---|
| `api/getPreguntes.php` | GET | 10 preguntas aleatorias (con `?admin=true`, todas y con la respuesta correcta) |
| `api/crearPregunta.php` | POST | Crea una pregunta con sus respuestas e imagen opcional |
| `api/editarPregunta.php` | POST | Actualiza una pregunta, sus respuestas y su imagen |
| `api/eliminarPregunta.php` | POST | Elimina una pregunta, sus respuestas y su imagen |

---

## Cómo ejecutarlo en local

**Requisitos:** PHP 7.4+ con la extensión `mysqli`, y MySQL o MariaDB.

1. Crea la base de datos `autoescola` con las tablas `preguntes` y `respostes` (el SQL está en la [documentación original](doc/README-original.md#esquema-de-base-de-dades-mínim)).
2. Configura los datos de conexión en `api/conn.php`.
3. Arranca el servidor integrado de PHP y abre http://localhost:8000:

```bash
php -S localhost:8000 -t .
```

---

## Próximas mejoras

- Leer las credenciales de la base de datos desde variables de entorno.
- Añadir autenticación al panel de administración.
- Incluir un script SQL de inicialización con las preguntas de `data.json`.

---

Desarrollado por **Valeria Zavaleta** ([@valeriazv99](https://github.com/valeriazv99)) · [LinkedIn](https://www.linkedin.com/in/valeria-zavaleta-vasquez)
