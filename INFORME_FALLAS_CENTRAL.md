# Informe de inconsistencias en el sistema central — escuelas de Godoy Cruz

Generado el 2026-09-16 a partir de la API `/schools` y `/inventory` (departamento Godoy Cruz).

## 1. Escuelas duplicadas (54 números repetidos, 29 de ellas del programa EDUTEC)

Aparecen dos registros con el mismo nombre, mismo CUE y mismo nivel, diferenciados solo por `anexo` = 0 y 1. No son anexos reales.

| N° | Nombre | CUE | Registros |
|---|---|---|---|
| 1-016 | PETRONA G.DE BURGOA | 5001149 | 2 (anexo 0, 1) |
| 1-075 | CORDILLERA DE LOS ANDES | 5001173 | 2 (anexo 0, 1) |
| 1-077 | PROVINCIA DE BUENOS AIRES | 5000617 | 2 (anexo 0, 1) |
| 1-078 | SANTIAGO DEL ESTERO | 5000639 | 2 (anexo 0, 1) |
| 1-108 | DR. JULIO LEMOS | 5000631 | 2 (anexo 0, 1) |
| 1-191 | JULIO LEONIDAS AGUIRRE | 5001179 | 2 (anexo 0, 1) |
| 1-337 | JUAN FRANCISCO COBO | 5000586 | 2 (anexo 0, 1) |
| 1-356 | DR. VICTORIANO MONTES | 5000620 | 2 (anexo 0, 1) |
| 1-419 | EMAUS | 5000634 | 2 (anexo 0, 1) |
| 1-552 | BANDERA ARGENTINA | 5000589 | 2 (anexo 0, 1) |
| 1-579 | PETROLEROS ARGENTINOS | 5000592 | 2 (anexo 0, 1) |
| 1-580 | DR. CARLOS PADIN | 5000590 | 2 (anexo 0, 1) |
| 1-585 | 1º DE FEBRERO | 5000619 | 2 (anexo 0, 1) |
| 1-617 | SAN GABRIEL | 5000603 | 2 (anexo 0, 1) |
| 1-620 | CORONEL PEDRO REGALADO DE LA PLAZA | 5001154 | 2 (anexo 0, 1) |
| 1-622 | PADRE PEDRO ARCE | 5001152 | 2 (anexo 0, 1) |
| 1-628 | LEONARDO DA VINCI | 5000588 | 2 (anexo 0, 1) |
| 1-629 | CARLOS PELLEGRINI | 5000584 | 2 (anexo 0, 1) |
| 1-635 | DR. RODOLFO COROMINAS SEGURA | 5000601 | 2 (anexo 0, 1) |
| 1-658 | TROPERO SOSA | 5000578 | 2 (anexo 0, 1) |
| 1-666 | BATALLA DEL PILAR | 5000621 | 2 (anexo 0, 1) |
| 1-669 | AQUILES WILSON MAZZIOTTI | 5000583 | 2 (anexo 0, 1) |
| 1-672 | RENATO DELLA SANTA | 5000580 | 2 (anexo 0, 1) |
| 1-674 | PROF. GERÓNIMO SOSA | 5000624 | 2 (anexo 0, 1) |
| 1-688 | CERRO ACONCAGUA | 5001170 | 2 (anexo 0, 1) |
| 1-691 | RAUL SCALABRINI ORTIZ | 5000579 | 2 (anexo 0, 1) |
| 1-698 | PROVINCIA DE MENDOZA | 5000604 | 2 (anexo 0, 1) |
| 1-712 | MAESTRO JESÚS DE NAZARET | 5001318 | 2 (anexo 0, 1) |
| 1-714 | CIUDAD DE BRASILIA | 5001319 | 2 (anexo 0, 1) |

## 2. Números de escuela mal formados en `inventory.assigned_to` (5)

`010331`, `1620`, `4001`, `4010`, `4148`

Deberían ser `1-620`, `4-001`, `4-010`, `4-148`, etc.

## 3. Escuelas con el número repetido dentro del nombre (2)

- `4-052` → "4-052 JUAN DRAGHI LUCERO" (genera un registro distinto del correcto)
- `4-109` → "4-109 ALVAREZ CONDARCO" (genera un registro distinto del correcto)

## 4. Equipamiento sin escuela asignada (34 registros)

Un kit completo (30 netbooks + pizarra + proyector + notebook docente + gabinete) con `assigned_to` vacío o `?`.

## 5. Campos vacíos en las 46 escuelas EDUTEC

| Campo | Sin dato |
|---|---|
| director | 46/46 |
| telefono | 46/46 |
| domicilio | 28/46 |
| email | 28/46 |

## 6. Campo `status` con mayúsculas inconsistentes

| Valor | Registros |
|---|---|
| `ACTIVO` | 1504 |
| `Activo` | 139 |
| `En Servicio Técnico` | 88 |
| `En Reparación` | 31 |
| `Duplicado` | 16 |
| `Para Reparar` | 7 |
| `Robado` | 1 |

`ACTIVO` y `Activo` deberían ser un solo valor.

## 7. Nombres que difieren entre el central y la planilla EDUTEC (3)

| N° | Planilla EDUTEC | Central |
|---|---|---|
| 1-635 | Coromina Segura | DR. RODOLFO COROMINAS SEGURA |
| 1-191 | Julio Leónidas de Aguirre | JULIO LEONIDAS AGUIRRE |
| 1-337 | Juan F. Cobos | JUAN FRANCISCO COBO |

## 8. Campo `codigo_gc` vacío en toda la provincia

La tabla `inventory` tiene la columna `codigo_gc` pero ninguno de los 33.790 registros la tiene cargada. Es el campo que permitiría cruzar el equipamiento EXO EDUTEC (identificado por código GC y serie de fábrica) con el central (identificado por CUPI).

## 9. Documentación de la API desactualizada

- La tabla `carros_godoy_cruz` no existe (404).
- Las columnas de `schools` se llaman `school_number` y `school_name`, no `number` y `name`.
