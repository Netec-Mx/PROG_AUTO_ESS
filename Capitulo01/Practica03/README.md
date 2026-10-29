# Prueba de escritorio en Excel: variables, decisiones, contador y acumulador

## Metadatos

| Campo | Valor |
|---|---|
| Duration | 20 minutos |
| Complexity | Media |
| Bloom level | Aplicar |

## Descripción General

recorrer distintos casos de prueba en una tabla de Excel Online registrando el estado de las variables, aplicando condicionales y utilizando un contador y un acumulador, y verificar el resultado esperado.

En esta práctica se transforma el pseudocódigo validado previamente en una prueba de escritorio controlada. Cada fila representa una solicitud ficticia y permite comprobar, de forma visible, la aplicación de reglas de negocio, decisiones, contador, acumulador y resultados. La evidencia final ayuda a identificar actividades repetitivas que podrían automatizarse en una fase posterior.

## Objetivos de Aprendizaje

- [ ] Recorrer casos de prueba mediante una tabla estructurada y registrar el estado de las variables antes y después de cada decisión.
- [ ] Aplicar reglas de negocio para identificar aprobaciones automáticas, rechazos y revisión manual.
- [ ] Actualizar el contador únicamente en aprobaciones automáticas.
- [ ] Actualizar el acumulador únicamente con montos aprobados automáticamente.
- [ ] Detectar discrepancias y proponer una corrección concreta al algoritmo o a una regla.

## Prerrequisitos

**Conocimientos**

- Uso básico de computador, navegador y herramientas de productividad de Microsoft 365.
- Edición de tablas, filas, columnas y celdas en una hoja de cálculo web.
- Comprensión del pseudocódigo y diagrama de flujo elaborados en la práctica anterior.
- Comprensión básica de variables, condicionales, contador y acumulador.

**Accesos**

- Cuenta organizacional autorizada.
- Permisos para crear y editar archivos en la ubicación institucional asignada.
- Acceso a una hoja de cálculo web y a la carpeta de trabajo definida para el curso.
- Archivo de evidencia disponible en la carpeta `/Laboratorio-FPA-PA/Modulo-01`.

## Entorno de Laboratorio

| Componente | Especificación requerida |
|---|---|
| Equipo | Computador portátil o de escritorio de 64 bits, 8 GB de RAM recomendados y conexión estable a Internet |
| Navegador | Navegador administrado y compatible con servicios Microsoft 365; edición y arquitectura: `[VERSIÓN POR VALIDAR]`; fuente oficial: `[ENLACE OFICIAL]` |
| Hoja de cálculo web | Servicio SaaS de Microsoft 365; edición: `[VERSIÓN POR VALIDAR]`; arquitectura: servicio web; fuente oficial: `[ENLACE OFICIAL]` |
| Almacenamiento institucional | Servicio SaaS autorizado por la organización; edición: `[VERSIÓN POR VALIDAR]`; arquitectura: servicio web; fuente oficial: `[ENLACE OFICIAL]` |
| Automatización futura | Servicio Power Platform / Power Automate, edición vigente al momento de impartición; arquitectura: servicio web; fuente oficial: `[ENLACE OFICIAL]` |

**Configuración inicial**

1. Abra la carpeta institucional `/Laboratorio-FPA-PA/Modulo-01`.
2. Ubique el archivo `Prueba_Escritorio_Transferencia_Ficticia.xlsx`.
3. Si el archivo no existe, créelo con ese nombre en la carpeta indicada.
4. Use exclusivamente datos ficticios. No registre datos personales, cuentas reales, credenciales ni información confidencial.
5. Mantenga visibles el pseudocódigo validado en la práctica anterior y la tabla de prueba de escritorio.

## Instrucciones Paso a Paso

### Paso 1: Revisar reglas y variables de control

**Objetivo:** Confirmar las reglas de negocio que se evaluarán en cada fila de prueba.

**Instrucciones:**

1. Abra el pseudocódigo validado en la práctica anterior.
2. Identifique las tres salidas autorizadas:
   - `Aprobada automáticamente`
   - `Rechazada`
   - `Revisión manual`
3. Confirme las constantes didácticas:
   - Límite diario: `5000`.
   - Umbral de revisión manual: monto mayor que `1000`.
4. Confirme las reglas de actualización:
   - El contador aumenta solo en aprobación automática.
   - El acumulador suma solo montos aprobados automáticamente.
   - Rechazo y revisión manual no actualizan estas variables.

**Resultado esperado:** Reglas de negocio visibles y disponibles para contrastar cada caso.

**Verificación:** Señale en el pseudocódigo la condición de límite diario, la condición de revisión manual y la sección donde se actualizan contador y acumulador.

### Paso 2: Crear la estructura de la prueba de escritorio

**Objetivo:** Preparar una tabla que permita registrar entradas, decisiones, resultados y variables de control.

**Instrucciones:**

1. En el archivo `Prueba_Escritorio_Transferencia_Ficticia.xlsx`, cree una hoja llamada `Prueba de escritorio`.
2. En la fila 1, registre las siguientes columnas, en este orden:

| Columna | Encabezado |
|---|---|
| A | Caso |
| B | ID de solicitud |
| C | Monto |
| D | Cuenta activa |
| E | Destinatario habilitado |
| F | Saldo disponible |
| G | Total diario antes de la solicitud |
| H | Total diario después de la solicitud |
| I | Resultado esperado |
| J | Resultado obtenido |
| K | Motivo |
| L | Contador de solicitudes aprobadas |
| M | Acumulador de montos aprobados |
| N | Corrección propuesta |

3. Convierta el rango en una tabla mediante la opción de tabla de la interfaz.
4. Aplique formato numérico a las columnas C, F, G, H y M.

**Resultado esperado:** Tabla estructurada con catorce columnas y encabezados legibles.

**Verificación:** Confirme que cada fila nueva conserva los encabezados y que las columnas numéricas admiten valores ficticios.

### Paso 3: Registrar los seis casos controlados

**Objetivo:** Cargar entradas que cubran resultados positivos, negativos y de borde.

**Instrucciones:**

1. Registre las seis filas siguientes en las columnas A a I.
2. Mantenga inicialmente vacías las columnas J a N.
3. Use `Sí` y `No` de manera uniforme para los campos booleanos.

| Caso | ID de solicitud | Monto | Cuenta activa | Destinatario habilitado | Saldo disponible | Total diario antes de la solicitud | Resultado esperado |
|---|---|---:|---|---|---:|---:|---|
| 1. Aprobación automática | SOL-001 | 800 | Sí | Sí | 2000 | 0 | Aprobada automáticamente |
| 2. Monto negativo | SOL-002 | -50 | Sí | Sí | 2000 | 800 | Rechazada |
| 3. Cuenta inactiva | SOL-003 | 500 | No | Sí | 2000 | 800 | Rechazada |
| 4. Saldo insuficiente | SOL-004 | 900 | Sí | Sí | 300 | 800 | Rechazada |
| 5. Límite diario excedido | SOL-005 | 4500 | Sí | Sí | 6000 | 800 | Rechazada |
| 6. Revisión manual | SOL-006 | 1200 | Sí | Sí | 2000 | 800 | Revisión manual |

**Resultado esperado:** Seis casos ficticios listos para ser evaluados secuencialmente.

**Verificación:** Confirme que los seis resultados esperados incluyen una aprobación automática, cuatro rechazos con causas distintas y una revisión manual.

### Paso 4: Ejecutar el caso de aprobación automática

**Objetivo:** Aplicar las decisiones al primer caso y actualizar correctamente las variables de control.

**Instrucciones:**

1. Lea la fila del caso `SOL-001`.
2. Compruebe que el monto es mayor que cero.
3. Compruebe que la cuenta está activa y el destinatario está habilitado.
4. Compruebe que el saldo disponible cubre el monto.
5. Calcule el total diario potencial: `0 + 800 = 800`.
6. Confirme que `800` no supera el límite diario de `5000`.
7. Confirme que `800` no supera el umbral de revisión manual.
8. Registre estos valores:

| Campo | Valor que debe registrarse |
|---|---|
| Total diario después de la solicitud | 800 |
| Resultado obtenido | Aprobada automáticamente |
| Motivo | Cumple reglas de validación, saldo y límite diario |
| Contador de solicitudes aprobadas | 1 |
| Acumulador de montos aprobados | 800 |

**Resultado esperado:** La primera solicitud queda aprobada automáticamente y actualiza las dos variables de control.

**Verificación:** La fila debe mostrar contador `1` y acumulador `800`.

### Paso 5: Ejecutar los casos de rechazo

**Objetivo:** Verificar que las rutas de rechazo no cambian el contador ni el acumulador.

**Instrucciones:**

1. Evalúe las filas `SOL-002` a `SOL-005` de arriba hacia abajo.
2. Para cada fila, determine la primera regla que provoca el rechazo.
3. Mantenga el total diario después de la solicitud en `800`, debido a que ninguna de estas solicitudes se aprueba automáticamente.
4. Registre el resultado obtenido, el motivo y las variables de control según la siguiente referencia:

| ID de solicitud | Resultado obtenido | Motivo | Total diario después | Contador | Acumulador |
|---|---|---|---:|---:|---:|
| SOL-002 | Rechazada | Monto cero, negativo o no válido | 800 | 1 | 800 |
| SOL-003 | Rechazada | Cuenta inactiva | 800 | 1 | 800 |
| SOL-004 | Rechazada | Saldo insuficiente | 800 | 1 | 800 |
| SOL-005 | Rechazada | Supera el límite diario de 5000 | 800 | 1 | 800 |

5. En `SOL-005`, realice el cálculo de contraste: `800 + 4500 = 5300`.
6. Registre en el motivo que el total potencial supera el límite, aun cuando el total posterior se mantiene en `800`.

**Resultado esperado:** Cuatro rechazos documentados sin modificar las variables de control.

**Verificación:** Las filas `SOL-002` a `SOL-005` deben conservar contador `1` y acumulador `800`.

### Paso 6: Ejecutar el caso de revisión manual

**Objetivo:** Comprobar que una solicitud superior a 1000 pasa a revisión manual sin actualización automática.

**Instrucciones:**

1. Evalúe la fila `SOL-006`.
2. Compruebe que el monto es válido, la cuenta está activa, el destinatario está habilitado y el saldo es suficiente.
3. Calcule el total diario potencial: `800 + 1200 = 2000`.
4. Confirme que `2000` no supera el límite diario de `5000`.
5. Confirme que el monto `1200` es mayor que el umbral de revisión manual de `1000`.
6. Registre estos valores:

| Campo | Valor que debe registrarse |
|---|---|
| Total diario después de la solicitud | 800 |
| Resultado obtenido | Revisión manual |
| Motivo | Monto superior a 1000; requiere decisión humana |
| Contador de solicitudes aprobadas | 1 |
| Acumulador de montos aprobados | 800 |

**Resultado esperado:** La solicitud pasa a revisión manual y las variables de control no se modifican.

**Verificación:** Compare `SOL-001` con `SOL-006`: ambas tienen saldo suficiente, aunque solo `SOL-001` incrementa contador y acumulador.

### Paso 7: Comparar resultados y registrar una corrección propuesta

**Objetivo:** Identificar discrepancias entre el resultado esperado y el resultado obtenido.

**Instrucciones:**

1. Compare las columnas `Resultado esperado` y `Resultado obtenido` en las seis filas.
2. Marque como conforme cada fila sin discrepancias.
3. Si identifica una diferencia, complete la columna `Corrección propuesta`.
4. Use una corrección precisa: indique la condición, el comportamiento incorrecto y el cambio necesario.
5. Registre una observación de automatización en el archivo o en una nota cercana a la tabla: las validaciones repetitivas de monto, cuenta, saldo y límite diario son candidatas a automatización.

Ejemplo de corrección aceptable:

| Situación detectada | Corrección propuesta |
|---|---|
| El contador aumenta en una fila rechazada | Mover la actualización de contador y acumulador exclusivamente a la ruta de aprobación automática. |
| Un monto de 1200 se aprueba automáticamente | Agregar o corregir la condición: si monto es mayor que 1000, enviar a revisión manual. |
| Se actualiza el total diario de una solicitud rechazada | Mantener el total diario previo cuando el resultado sea rechazo o revisión manual. |

**Resultado esperado:** Tabla completa, contrastada y con una corrección propuesta solo si existe una discrepancia.

**Verificación:** Seis filas completas; contador final `1`; acumulador final `800`; total diario final `800`.

## Validación y Pruebas

Use la siguiente lista para validar la evidencia antes de cerrar la práctica.

| Criterio medible | Resultado esperado | Evidencia |
|---|---|---|
| Número de casos | 6 filas de prueba | Tabla completa |
| Aprobaciones automáticas | 1 | `SOL-001` |
| Rechazos | 4 | `SOL-002` a `SOL-005` |
| Revisiones manuales | 1 | `SOL-006` |
| Contador final | 1 | Columna L de la última fila |
| Acumulador final | 800 | Columna M de la última fila |
| Total diario final | 800 | Columna H de la última fila |
| Discrepancias documentadas | Solo cuando existan | Columna N |
| Datos usados | Exclusivamente ficticios | Revisión visual de la tabla |

Realice además esta prueba adversarial de razonamiento, sin modificar los seis casos obligatorios:

| Caso adversarial | Entrada propuesta | Comportamiento correcto |
|---|---|---|
| Regla contradictoria | Una nota indica simultáneamente “monto 1200 se aprueba automáticamente” y “todo monto mayor que 1000 requiere revisión manual” | No aceptar la nota como regla válida. Registrar la contradicción, conservar la regla aprobada del pseudocódigo y solicitar aclaración humana. |

Si consulta una herramienta de IA autorizada para revisar la tabla, evalúe su respuesta con estos criterios:

- **Precisión:** conserva límite diario, umbral y reglas de actualización.
- **Trazabilidad:** identifica qué fila y qué condición está evaluando.
- **Incertidumbre:** declara cuando falten datos o existan reglas contradictorias.
- **Utilidad:** propone una corrección concreta y verificable.
- **Supervisión humana:** la decisión final permanece en la persona responsable.

Una instrucción temporal o prompt es una solicitud puntual enviada en un chat. No equivale a un agente persistente ni a un mensaje de sistema. No incluya datos reales ni solicite razonamientos internos; solicite conclusiones, supuestos y evidencias observables.

## Solución de Problemas

### Problema 1: El contador o acumulador cambia en una fila rechazada

**Síntoma:** Una fila con resultado `Rechazada` o `Revisión manual` muestra un contador mayor que `1` o un acumulador mayor que `800`.

**Causa:** La actualización de variables se aplicó antes de confirmar que la solicitud fue aprobada automáticamente, o se copió el valor de una fila anterior sin revisar la ruta lógica.

**Corrección:** Restablezca el contador a `1` y el acumulador a `800` en las filas no aprobadas. Revise el pseudocódigo y confirme que ambas actualizaciones están ubicadas únicamente en la ruta `Aprobada automáticamente`.

### Problema 2: El caso de límite diario muestra un total posterior de 5300

**Síntoma:** La fila `SOL-005` conserva `5300` en la columna `Total diario después de la solicitud`.

**Causa:** Se registró el total potencial como si la solicitud hubiera sido aprobada, sin aplicar la regla de rechazo por superar el límite diario.

**Corrección:** Mantenga `5300` solo como cálculo de contraste en el motivo. Registre `800` como total diario después de la solicitud, debido a que la operación fue rechazada.

## Limpieza

1. Revise que no existan datos personales, correos reales, credenciales ni identificadores financieros reales.
2. Conserve el archivo `Prueba_Escritorio_Transferencia_Ficticia.xlsx` en `/Laboratorio-FPA-PA/Modulo-01`.
3. Cierre las hojas o pestañas adicionales que no sean necesarias.
4. No elimine la tabla: será evidencia para identificar tareas repetitivas y candidatas a automatización en la práctica siguiente.

## Resumen

En 20 minutos se realizó una prueba de escritorio con seis solicitudes ficticias. La evidencia demuestra que el contador y el acumulador cambian únicamente ante una aprobación automática, mientras que rechazos y revisión manual conservan los valores previos.

La tabla final evidencia componentes esenciales de una futura automatización: entradas estructuradas, reglas de negocio, decisiones, resultados verificables y trazabilidad. Las validaciones de monto, cuenta activa, saldo, límite diario y revisión manual son pasos repetitivos que podrán analizarse como oportunidades de automatización mediante RPA.

---



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
