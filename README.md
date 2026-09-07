# EDUTEC Godoy Cruz

Dashboard de gestión del parque tecnológico EXO EDUTEC — Godoy Cruz. Aplicación de página única (HTML/CSS/JS, sin dependencias ni build), pensada para abrirse directo en el navegador.

## Qué muestra

- **Inventario por escuela** — las 46 escuelas del departamento, con notebooks/proyectores/ebeams/AP/gabinetes asignados. Cada escuela se puede abrir en detalle para ver ID, N° de serie y ubicación actual (en la escuela, en EDUCAR o en Casa del Futuro) de cada equipo.
- **Faltantes por escuela** — calculado automáticamente: compara lo asignado contra lo que hoy está físicamente en la escuela (excluye lo que está en reparación en EDUCAR o en Casa del Futuro).
- **En EDUCAR** — equipos actualmente en el centro esperando diagnóstico o reparación, con fecha de ingreso y problema reportado.
- **Casa del Futuro (CDF)** — equipos con batería hinchada, fuera de garantía y cajas en depósito.
- **Retiros y Devoluciones** — registro de salidas de equipos desde EDUCAR hacia las escuelas, con fecha de ingreso a EDUCAR y fecha de retiro. Al marcar un retiro como "Devuelto", el equipo se integra automáticamente al inventario de la escuela destino y desaparece de "En EDUCAR".

## Uso

Abrí `EDUTEC_GODOY_CRUZ_v2.html` directamente en cualquier navegador. Los retiros se guardan en `localStorage`, así que quedan persistidos entre sesiones en el mismo navegador/equipo.

`EDUTEC_GODOY_CRUZ.html` es la versión inicial (v1), sin el detalle por escuela ni el sistema de retiros con auto-integración.

## Datos

`school_inventory.json` / `school_inventory_js.txt` contienen el inventario detallado por escuela (ID, N° de serie, tipo de equipo) extraído de las planillas originales. Algunos registros todavía tienen datos incompletos — está pendiente completar el inventario físico de 3 escuelas (Pedro Regalado de la Plaza, Mazziotti y Padre Pedro Arce) que no figuraban en el Excel de origen.
