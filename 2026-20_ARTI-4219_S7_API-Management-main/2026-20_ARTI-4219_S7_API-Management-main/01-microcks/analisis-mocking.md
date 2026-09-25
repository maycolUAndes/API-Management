# =====================================================================
# Análisis del Mocking Dinámico con Microcks
# =====================================================================

## Servicio analizado: Petstore 1.0.0 (`petstore-with-examples.yaml`)

### 1. Operaciones disponibles

- `GET /pet/findByStatus`: busca mascotas filtrando por el parámetro de consulta obligatorio `status` (`available`, `pending` o `sold`).
- `GET /pet/{petId}`: busca una mascota por su identificador de ruta `petId`.

### 2. URL base del mock generado por Microcks

La URL base generada por Microcks es:

`http://localhost:9090/rest/Petstore/1.0.0`

Por tanto, las rutas completas se construyen agregando el path de cada operación a esa URL.

### 3. Llamadas curl al mock

#### Llamada 1:
```bash
curl -s "http://localhost:9090/rest/Petstore/1.0.0/pet/findByStatus?status=available"
```

**Respuesta obtenida:**
```json
[
     {
          "id": 1,
          "name": "Firulais",
          "status": "available",
          "category": { "id": 1, "name": "Dogs" }
     },
     {
          "id": 2,
          "name": "Misifus",
          "status": "available",
          "category": { "id": 2, "name": "Cats" }
     }
]
```

#### Llamada 2:
```bash
curl -s "http://localhost:9090/rest/Petstore/1.0.0/pet/1"
```

**Respuesta obtenida:**
```json
{
     "id": 1,
     "name": "Firulais",
     "status": "available",
     "category": { "id": 1, "name": "Dogs" },
     "photoUrls": ["https://example.com/firulais.jpg"],
     "tags": [{ "id": 1, "name": "friendly" }]
}
```

### 4. Ventaja del mocking dinámico vs. mock estático

Microcks genera las respuestas a partir del contrato y puede seleccionar ejemplos
distintos según los parámetros recibidos, por lo que el frontend puede probar
escenarios realistas sin esperar a que exista el backend. Si el contrato cambia,
el mock se puede volver a importar y conserva una representación alineada con la
API acordada. Un mock estático normalmente sirve siempre el mismo JSON y obliga a
mantener manualmente archivos y rutas, mientras que Microcks centraliza el contrato,
las operaciones, los ejemplos y las pruebas de conformidad.

> Nota: las respuestas anteriores son las respuestas esperadas según los ejemplos
> declarados en `petstore-with-examples.yaml`. Para registrar evidencia de ejecución,
> hay que levantar Microcks y ejecutar los comandos desde el Paso 6 de la guía.
