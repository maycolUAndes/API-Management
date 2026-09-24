# =====================================================================
# Análisis del Catálogo de APIs en Backstage
# =====================================================================

## Fecha: 2026-09-23
## Nombre: ____________________

### 1. Información visible de la API en el catálogo

Al sincronizar una API de Microcks, el catálogo de Backstage muestra la entidad
`API` con su nombre y versión, descripción, propietario, sistema, etiquetas y
enlaces asociados. En el detalle también se puede consultar la definición del
contrato OpenAPI, sus metadatos y los enlaces a los mocks publicados por Microcks.
Los campos exactos dependen de las etiquetas configuradas en el provider, como
`systemLabel` y `ownerLabel`, y de la información disponible en el contrato.

### 2. Valor del catálogo centralizado para equipos grandes

El catálogo centralizado evita que los ingenieros tengan que conocer de memoria
la ubicación de cada contrato o preguntar a otros equipos dónde está una API.
El descubrimiento automático mantiene el inventario actualizado cuando Microcks
importa nuevas versiones, lo que reduce el registro manual y los duplicados en
un equipo de 50 o más ingenieros. Además, facilita comparar APIs, identificar
propietarios y pasar rápidamente desde la documentación hasta un mock utilizable.

### 3. Diferencia entre Component y API en Backstage

Un `Component` representa una pieza de software que el equipo desarrolla o
mantiene, por ejemplo un servicio, una aplicación o una librería. Una `API`
representa el contrato de una interfaz que puede ser consumida por otros
componentes, como sus rutas HTTP, esquemas y versión. Por eso un componente
puede proporcionar una API y también consumir otras APIs; son entidades
relacionadas, pero no describen el mismo objeto del catálogo.
