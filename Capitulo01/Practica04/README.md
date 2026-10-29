# Identificación de candidatos a RPA

## Metadatos

| Campo | Valor |
|---|---|
| Duration | 15 minutos |
| Complexity | Fácil |
| Bloom level | Aplicar |

## Descripción General

clasificar en una matriz digital las tareas de un proceso según su potencial de automatización, la intervención humana requerida y las excepciones a contemplar, apoyándose en C​opilot Chat para contrastar criterios.

A partir del algoritmo, pseudocódigo, diagrama y prueba de escritorio de las prácticas previas, se separan las tareas rutinarias de las decisiones que requieren juicio humano. La matriz resultante permite priorizar tareas candidatas a flujos de nube y reconocer controles, riesgos y excepciones que no deben delegarse.

## Objetivos de Aprendizaje

- [ ] Clasificar diez tareas del proceso ficticio mediante una escala de alto, medio o bajo.
- [ ] Identificar tareas repetitivas, digitales y basadas en reglas que pueden ser candidatas a automatización.
- [ ] Diferenciar la automatización del envío o registro de una decisión respecto de la decisión humana misma.
- [ ] Contrastar la clasificación con un asistente IA autorizado, evaluando precisión, trazabilidad, incertidumbre, utilidad y supervisión humana.
- [ ] Registrar excepciones y riesgos que impidan una automatización sin controles.

## Prerrequisitos

**Conocimientos**

- Uso básico de navegador, archivos web y tablas.
- Resultados de las Prácticas 1, 2 y 3: algoritmo, pseudocódigo, diagrama y prueba de escritorio.
- Comprensión de variables, condicionales, contador, acumulador, reglas de negocio y excepciones.
- Conocimiento de la diferencia entre una tarea repetitiva y una decisión con juicio humano.

**Accesos**

- Cuenta organizacional autorizada con permiso para crear y editar archivos en la ubicación institucional asignada.
- Acceso a un editor web de hojas de cálculo o a una plantilla de matriz entregada por el instructor.
- Acceso opcional a C​opilot Chat o a un asistente IA autorizado.
- Carpeta de trabajo existente: `/Laboratorio-FPA-PA/Modulo-01`.

## Entorno de Laboratorio

| Recurso | Versión o edición | Arquitectura | Fuente oficial |
|---|---|---|---|
| Power Automate | Servicio SaaS, edición de nube, [VERSIÓN POR VALIDAR] | No aplica | [Documentación oficial](https://learn.micr&#111;soft.com/es-es/power-automate/) |
| Editor web de hojas de cálculo | Servicio SaaS, edición web, [VERSIÓN POR VALIDAR] | No aplica | [Ayuda oficial](https://support.micr&#111;soft.com/) |
| C​opilot Chat | Servicio SaaS, [VERSIÓN POR VALIDAR] | No aplica | [Documentación oficial](https://learn.micr&#111;soft.com/es-es/copilot/) |
| Navegador administrado por la organización | [VERSIÓN POR VALIDAR] | 64 bits o arquitectura administrada | [Ayuda oficial](https://support.micr&#111;soft.com/) |

> **Licencias y configuración:** Power Automate requiere una licencia de Microsoft 365 que permita usar conectores estándar y operar flujos en un entorno autorizado. C​opilot Chat es opcional: su acceso depende de la licencia, configuración y protección de datos del tenant. M​icrosoft 365 C​opilot, C​opilot Chat, Designer y Planner son productos o capacidades distintas; esta práctica solo admite C​opilot Chat, si está habilitado. No se requiere licencia Premium, Power Automate Desktop ni AI Builder.

> **Preparación:** no se ejecutan comandos en este laboratorio. Abra la plantilla entregada por el instructor y guárdela como `/Laboratorio-FPA-PA/Modulo-01/Matriz_RPA_Transferencia_Ficticia.xlsx`. Use únicamente datos ficticios.

## Instrucciones Paso a Paso

### Paso 1: Abrir la matriz y reconocer las tareas

**Objetivo:** disponer de una matriz digital con las diez tareas del proceso ficticio.

**Instrucciones**

1. Abra la plantilla de matriz entregada por el instructor.
2. Guárdela con el nombre `Matriz_RPA_Transferencia_Ficticia.xlsx` en la carpeta de trabajo.
3. Confirme que incluye estas columnas: **Tarea**, **Frecuencia**, **Repetitividad**, **Reglas claras**, **Datos digitales**, **Riesgo**, **Intervención humana**, **Excepciones** y **Potencial de automatización**.
4. Registre las siguientes tareas en la primera columna, una por fila:
   - Recibir solicitud.
   - Validar campos obligatorios.
   - Consultar estado de cuenta.
   - Validar destinatario.
   - Verificar saldo.
   - Calcular total diario.
   - Clasificar resultado.
   - Solicitar revisión humana.
   - Notificar al solicitante.
   - Registrar decisión.

**Expected output:** matriz guardada con diez filas de tareas y nueve columnas de análisis.

**Verification:** el nombre del archivo coincide exactamente con `Matriz_RPA_Transferencia_Ficticia.xlsx` y la tabla contiene las diez tareas.

### Paso 2: Aplicar la escala de clasificación

**Objetivo:** usar una escala común y comparable para todas las tareas.

**Instrucciones**

1. Use exclusivamente los valores **Alto**, **Medio** o **Bajo** en cada criterio.
2. Aplique estas reglas:
   - **Alto** en repetitividad: la tarea se repite de modo similar en cada solicitud.
   - **Alto** en reglas claras: existe una condición comprobable, tal como monto mayor a 1.000 o total diario superior a 5.000.
   - **Alto** en datos digitales: los datos ya existen en una lista, tabla o registro autorizado.
   - **Alto** en riesgo: un error puede afectar privacidad, saldo, destinatario o decisión.
   - **Alto** en intervención humana: una persona debe juzgar, autorizar o resolver una excepción.
3. Considere que una tarea con riesgo alto puede automatizarse solo si dispone de controles, permisos y trazabilidad adecuados.
4. Recuerde que automatizar una notificación no equivale a automatizar la autorización humana.

**Expected output:** criterios aplicados de modo consistente antes de clasificar cada fila.

**Verification:** puede explicar por qué “riesgo alto” no significa automáticamente “potencial bajo”.

### Paso 3: Clasificar las tareas del proceso

**Objetivo:** completar la matriz usando las reglas de negocio ya probadas.

**Instrucciones**

1. Clasifique cada tarea según el comportamiento observado en la prueba de escritorio.
2. Use las reglas ficticias ya definidas:
   - Límite diario: 5.000 unidades monetarias.
   - Umbral de revisión manual: 1.000 unidades monetarias.
   - Contador: solicitudes aprobadas automáticamente.
   - Acumulador: suma de montos aprobados automáticamente.
3. En la columna **Excepciones**, anote una excepción breve para cada tarea que la requiera, por ejemplo: “dato obligatorio vacío”, “destinatario no validado”, “saldo insuficiente” o “dato no disponible”.
4. En **Potencial de automatización**, priorice tareas repetitivas, con reglas claras y datos digitales disponibles.

**Expected output:** matriz completa con una clasificación y, cuando aplique, una excepción por tarea.

**Verification:** la tarea “Solicitar revisión humana” tiene **Intervención humana: Alto**, aun si la tarea de enviar el aviso puede tener **Potencial de automatización: Alto**.

### Paso 4: Contrastar criterios con asistencia IA opcional

**Objetivo:** usar un asistente IA como apoyo crítico, sin delegar la decisión final.

**Instrucciones**

1. Si el acceso está habilitado, envíe este prompt al asistente IA autorizado:

   > Actúa como apoyo para clasificar tareas de un proceso ficticio de solicitudes bancarias. Usa solo estos datos: límite diario 5.000, revisión manual desde 1.000, no hay datos reales y las decisiones de autorización permanecen bajo control humano. Clasifica cada tarea como candidata alta, media o baja a automatización y explica riesgos, excepciones y evidencia necesaria. No inventes conectores bancarios ni supongas autorización automática.

2. Compare la respuesta con su matriz.
3. Marque una sugerencia útil y una sugerencia que requiera corrección, evidencia adicional o supervisión humana.
4. No copie datos personales, credenciales, cuentas reales ni contenido confidencial.
5. Distinga los conceptos:
   - El **prompt** es una instrucción temporal enviada por la persona usuaria.
   - Un **mensaje de sistema** define reglas de mayor prioridad y no debe suponerse visible.
   - Un asistente persistente puede conservar una configuración autorizada; no es equivalente a un prompt temporal.

**Expected output:** una observación crítica registrada en una celda de notas o comentario de la matriz.

**Verification:** la observación menciona al menos uno de estos criterios: precisión, trazabilidad, incertidumbre, utilidad o supervisión humana.

### Paso 5: Priorizar candidatos para flujos de nube

**Objetivo:** identificar qué partes podrían abordarse después mediante conectores estándar.

**Instrucciones**

1. Revise las filas con potencial alto.
2. Marque como candidatas iniciales de flujo de nube:
   - Recibir solicitud, si proviene de un origen digital autorizado.
   - Validar campos obligatorios.
   - Calcular total diario.
   - Clasificar resultado según reglas.
   - Solicitar revisión humana mediante aviso y asignación.
   - Notificar al solicitante.
   - Registrar decisión.
3. Marque como dependientes de revisión, integración autorizada o control adicional:
   - Consultar estado de cuenta.
   - Validar destinatario.
   - Verificar saldo.
4. Agregue al final de la matriz una nota: “La automatización propuesta no ejecuta operaciones bancarias reales ni reemplaza decisiones humanas”.

**Expected output:** candidatos priorizados y límites de automatización documentados.

**Verification:** la matriz separa claramente la automatización de tareas de registro, cálculo, clasificación y aviso respecto de la autorización humana.

## Validación y Pruebas

Use esta referencia para validar la clasificación. Se aceptan variaciones justificadas, siempre que respeten controles, excepciones y revisión humana.

| Tarea | Potencial esperado | Intervención humana esperada | Justificación verificable |
|---|---|---|---|
| Recibir solicitud | Alto | Bajo | Actividad repetitiva si el origen digital está autorizado. |
| Validar campos obligatorios | Alto | Bajo | Reglas objetivas: campo presente, tipo válido o dato vacío. |
| Consultar estado de cuenta | Medio | Medio | Depende de acceso autorizado, fuente confiable y trazabilidad. |
| Validar destinatario | Medio | Alto | Requiere resolver coincidencias ambiguas o alertas. |
| Verificar saldo | Medio | Medio | La regla puede ser clara; el acceso al dato es sensible. |
| Calcular total diario | Alto | Bajo | Usa acumulador y límite diario definidos. |
| Clasificar resultado | Alto | Bajo | Aplica condicionales ya probados. |
| Solicitar revisión humana | Alto | Alto | El aviso puede automatizarse; la revisión no. |
| Notificar al solicitante | Alto | Bajo | Mensaje repetitivo basado en el resultado. |
| Registrar decisión | Alto | Medio | Registro repetitivo con validación de permisos y trazabilidad. |

**Criterios medibles de aceptación**

- La matriz tiene diez filas de tareas y las nueve columnas requeridas.
- Cada fila tiene una clasificación de Alto, Medio o Bajo en los criterios definidos.
- Se registran al menos cinco excepciones concretas.
- Se identifican al menos cinco tareas candidatas a automatización.
- Se identifica al menos una tarea donde el aviso es automatizable y la decisión sigue siendo humana.
- La matriz incluye la nota de límites: no existen operaciones bancarias reales ni autorización automática.

**Prueba adversarial de IA**

Evalúe esta afirmación generada por un asistente IA:

> “Todas las solicitudes inferiores a 1.000 pueden aprobarse sin consultar saldo, destinatario ni límite diario.”

La afirmación debe rechazarse. Contradice las reglas: el monto inferior al umbral no elimina la validación de destinatario, saldo, límite diario, datos obligatorios ni controles de riesgo. Registre en la matriz: “Sugerencia rechazada por falta de evidencia y contradicción con reglas de negocio”.

## Solución de Problemas

1. **Síntoma:** la matriz clasifica “Solicitar revisión humana” con potencial bajo porque exige una persona.  
   **Causa:** se confundió la decisión humana con la tarea de enviar, registrar o asignar la solicitud de revisión.  
   **Solución:** mantenga **Intervención humana: Alto** y clasifique como **Potencial de automatización: Alto** el envío del aviso y el registro de la solicitud. La autorización final sigue bajo control humano.

2. **Síntoma:** el asistente IA recomienda automatizar la consulta de saldo o la validación de destinatario sin indicar fuente de datos, permisos ni controles.  
   **Causa:** la respuesta asumió datos o integraciones no demostradas.  
   **Solución:** clasifique la tarea como potencial medio, registre la falta de evidencia y exija fuente autorizada, permisos, trazabilidad y tratamiento de excepciones antes de proponer un flujo.

## Limpieza

1. Guarde la matriz final en `/Laboratorio-FPA-PA/Modulo-01/Matriz_RPA_Transferencia_Ficticia.xlsx`.
2. Cierre las pestañas usadas para la práctica.
3. No elimine la matriz: será evidencia para módulos posteriores.
4. Elimine de la conversación con IA cualquier dato que no corresponda al caso ficticio, según las normas de la organización.

## Resumen

En 15 minutos se clasificaron tareas del proceso ficticio según repetitividad, reglas, datos digitales, riesgo, intervención humana y excepciones. Las tareas de cálculo, clasificación, aviso y registro son candidatas claras para flujos de nube con conectores estándar; las decisiones de autorización, casos ambiguos y datos sensibles requieren supervisión humana y controles verificables.

La matriz `Matriz_RPA_Transferencia_Ficticia.xlsx` conecta el algoritmo y la prueba de escritorio con una futura automatización basada en disparador, acciones, datos dinámicos, notificaciones y trazabilidad.

---



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
