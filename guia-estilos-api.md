# Guía de Estilos para APIs REST

Versión 1.0
Estado: Activa
Alcance: Todas las APIs públicas e internas

Usa SIEMPRE el inglés como lenguaje para la especificación de la API.

------------------------------------------------------------------------

## 1. Diseño orientado a recursos

-   Usa sustantivos en plural para los recursos.
-   Evita verbos en la URL.
-   Representa relaciones mediante sub-recursos cuando tenga sentido.

**Ejemplos:**

    GET /users
    GET /users/{userId}
    GET /users/{userId}/orders

------------------------------------------------------------------------

## 2. Uso correcto de métodos HTTP

-   `GET` → Obtener recursos (idempotente).
-   `POST` → Crear recursos.
-   `PUT` → Reemplazar completamente un recurso.
-   `PATCH` → Actualización parcial.
-   `DELETE` → Eliminar recurso.

No uses `POST` para todo.

------------------------------------------------------------------------

## 3. Convenciones de nombres

-   Usa **snake_case** para todos los campos JSON.
-   Los identificadores deben llamarse `id`.
-   Usa nombres descriptivos y claros.
-   Los parámetros de query también deben seguir snake_case.
-   Los valores de los enums deben estar en mayúsculas.

**Ejemplo:**

``` json
{
  "id": "123",
  "first_name": "Ana",
  "created_at": "2026-02-23T10:00:00Z"
}
```

------------------------------------------------------------------------

## 4. Manejo de errores estándar

-   Usa códigos HTTP correctos.
-   Devuelve siempre un cuerpo de error consistente.

**Ejemplo:**

``` json
{
  "code": "USER_NOT_FOUND",
  "message": "User not found",
  "details": []
}
```

Códigos comunes:

-   `400` Bad Request\
-   `401` Unauthorized\
-   `403` Forbidden\
-   `404` Not Found\
-   `409` Conflict\
-   `500` Internal Server Error

------------------------------------------------------------------------

## 5. Formato y contenido de respuestas

-   Usa `application/json`.
-   Las fechas deben representarse como **timestamps numéricos** (epoch en milisegundos).
-   Las respuestas de creación (`POST`) deben devolver `201 Created` y
    el recurso creado.
-   Incluye encabezado `Location` cuando aplique.

------------------------------------------------------------------------

## 6. Seguridad y autenticación

-   Todas las APIs deben usar HTTPS.
-   Autenticación mediante Bearer Token (API Key).
-   Nunca expongas información sensible en la URL.

------------------------------------------------------------------------
