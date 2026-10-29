# Manejo de errores y alertas

## Metadatos

| Duración | Complejidad | Nivel de Bloom |
|---|---|---|
| 35 minutos | Media | Crear |

## Descripción General

En esta práctica se extiende el flujo `SolicitudOperacion-Aprobacion-v1` con un patrón TRY/CATCH basado en acciones Scope. El flujo resultante separa la ruta principal, la ruta de error y la notificación al responsable, con reintentos conservadores en una acción compatible. Se realiza una ejecución satisfactoria y una falla controlada en una copia de prueba, seguida de la restauración de la configuración válida.

> Descripción declarada: agregar un bloque try/catch con Scope, configurar ejecución posterior y reintentos, y notificar al responsable cuando el flujo falle.

## Objetivos de Aprendizaje

- [ ] Encapsular la lógica principal en el Scope `TRY-ProcesarSolicitud`.
- [ ] Crear el Scope `CATCH-NotificarError` y configurar su ejecución posterior ante error, omisión o tiempo de espera.
- [ ] Aplicar una política conservadora de reintentos en una acción compatible.
- [ ] Enviar una alerta al valor definido en `ResponsableFlujo` con datos trazables de la ejecución.
- [ ] Ejecutar una prueba satisfactoria y una falla controlada, registrando la corrección aplicada.

## Prerrequisitos

**Conocimientos**

- Uso básico del explorador, correo organizacional, listas de trabajo y flujos de nube.
- Comprensión básica de acciones, contenido dinámico, condiciones y estados del historial de ejecución.
- Práctica 15 terminada, o una copia funcional de `SolicitudOperacion-Aprobacion-v1`.
- Conocimiento de que una acción Scope agrupa pasos y presenta un único estado global de ejecución.

**Accesos**

- Permisos para crear, editar, guardar, ejecutar y probar flujos en el entorno autorizado.
- Permisos de edición en la lista `SolicitudesOperacion`.
- Conexión válida al conector de lista del sitio de práctica.
- Conexión válida al conector de correo organizacional.
- Cuenta ficticia y autorizada definida como `ResponsableFlujo`.
- Acceso al historial de ejecución del flujo.

No use datos personales, cuentas reales, montos reales, credenciales ni direcciones externas. Utilice solicitudes y correos ficticios autorizados para el laboratorio.

## Entorno de Laboratorio

| Recurso | Versión o condición | Arquitectura | Fuente oficial |
|---|---|---|---|
| Servicio de flujos de nube | [VERSIÓN POR VALIDAR] | SaaS; no aplica | [ENLACE OFICIAL] |
| Conector de listas del sitio | [VERSIÓN POR VALIDAR] | SaaS; no aplica | [ENLACE OFICIAL] |
| Conector de correo organizacional | [VERSIÓN POR VALIDAR] | SaaS; no aplica | [ENLACE OFICIAL] |
| Servicio de aprobaciones | [VERSIÓN POR VALIDAR] | SaaS; no aplica | [ENLACE OFICIAL] |
| Explorador administrado por la organización | [VERSIÓN POR VALIDAR] | 64 bits; si aplica | [ENLACE OFICIAL] |

| Recurso físico | Mínimo recomendado |
|---|---|
| Equipo | Procesador de 64 bits, 8 GB de RAM, 2 GB libres |
| Pantalla | 1366 × 768; recomendado 1920 × 1080 |
| Red | Acceso HTTPS saliente por TCP 443 |
| Periféricos | Teclado y dispositivo apuntador |

No se ejecutan comandos de terminal en este laboratorio. Toda la configuración se realiza desde el diseñador web del servicio de flujos.

Antes de iniciar, valide que existen estos elementos:

| Elemento | Valor esperado |
|---|---|
| Flujo de partida | `SolicitudOperacion-Aprobacion-v1` |
| Lista de práctica | `SolicitudesOperacion` |
| Campo de estado | `Estado` |
| Valor de responsable | Correo ficticio autorizado en `ResponsableFlujo` |
| Estados usados | `Pendiente`, `Aprobada`, `Rechazada`, `ErrorTecnico` |

## Instrucciones Paso a Paso

### Paso 1: Verificar el flujo de partida

**Objetivo:** Confirmar que existe una versión funcional antes de agregar manejo de errores.

**Instrucciones:**

1. Abra el flujo `SolicitudOperacion-Aprobacion-v1`.
2. Revise que el desencadenador corresponda a la creación de un elemento en `SolicitudesOperacion`.
3. Verifique que la lógica incluya actualización inicial, aprobación, condición de decisión y notificaciones.
4. Abra el historial de ejecución y confirme que existe al menos una ejecución satisfactoria previa, si está disponible.
5. Identifique el valor ficticio que recibirá alertas como `ResponsableFlujo`.

**Resultado esperado:** El flujo de partida está disponible, editable y conserva una ruta funcional de aprobación.

**Verificación:** El historial muestra una ejecución correcta o el instructor confirma la copia funcional autorizada.

### Paso 2: Crear la versión robusta

**Objetivo:** Preservar la versión anterior y crear una versión destinada al patrón TRY/CATCH.

**Instrucciones:**

1. Seleccione la opción **Guardar como** sobre `SolicitudOperacion-Aprobacion-v1`.
2. Asigne este nombre exacto:

```text
SolicitudOperacion-Aprobacion-Robusta-v2
```

3. Guarde la copia.
4. Abra la versión nueva y confirme que el nombre aparece en el encabezado del diseñador.
5. No modifique ni elimine la versión `SolicitudOperacion-Aprobacion-v1`.

**Resultado esperado:** Existe una copia editable denominada `SolicitudOperacion-Aprobacion-Robusta-v2`.

**Verificación:** En la lista de flujos aparecen ambas versiones con nombres distintos.

### Paso 3: Agregar el Scope de procesamiento principal

**Objetivo:** Crear el contenedor TRY para la lógica de negocio principal.

**Instrucciones:**

1. Después del desencadenador, agregue la acción **Scope**.
2. Cambie su nombre a:

```text
TRY-ProcesarSolicitud
```

3. Ubique dentro de este Scope las acciones que realizan la lógica principal del flujo:
   1. Actualización inicial del estado a `Pendiente`.
   2. Acción de aprobación y espera de decisión.
   3. Condición que evalúa la decisión.
   4. Actualización del estado a `Aprobada` o `Rechazada`.
   5. Notificaciones asociadas a cada ruta.
4. Mantenga fuera del Scope únicamente el desencadenador.
5. Guarde el flujo.

**Resultado esperado:** La lógica principal está contenida dentro de `TRY-ProcesarSolicitud`.

**Verificación:** El diseñador muestra un único Scope después del desencadenador y las acciones principales están anidadas dentro de él.

### Paso 4: Revisar las referencias de contenido dinámico

**Objetivo:** Evitar vínculos rotos después de reorganizar las acciones.

**Instrucciones:**

1. Abra la acción de actualización inicial dentro de `TRY-ProcesarSolicitud`.
2. Confirme que el identificador del elemento usa el `ID` procedente del desencadenador.
3. Revise que los valores requeridos de título, solicitante, área, monto, justificación y aprobador conservan sus referencias originales.
4. Abra la acción de aprobación.
5. Confirme que el destinatario procede del campo `AprobadorAsignado` y no de texto fijo.
6. Guarde el flujo.

**Resultado esperado:** Las acciones del Scope mantienen datos válidos procedentes del desencadenador.

**Verificación:** No hay advertencias de campos obligatorios vacíos ni referencias eliminadas en las acciones revisadas.

### Paso 5: Crear el Scope de captura de errores

**Objetivo:** Agregar una ruta independiente para fallas de la ruta principal.

**Instrucciones:**

1. Debajo de `TRY-ProcesarSolicitud`, agregue una segunda acción **Scope**.
2. Cambie su nombre a:

```text
CATCH-NotificarError
```

3. Mantenga este Scope vacío de manera temporal.
4. Seleccione los puntos suspensivos de `CATCH-NotificarError`.
5. Abra **Configurar ejecución posterior**.
6. Desactive la opción de ejecución satisfactoria.
7. Active estas opciones:
   - Ha producido un error.
   - Ha excedido el tiempo de espera.
   - Se ha omitido.
8. Confirme la configuración y guarde.

**Resultado esperado:** `CATCH-NotificarError` solo se inicia cuando `TRY-ProcesarSolicitud` no termina correctamente.

**Verificación:** La configuración de ejecución posterior presenta tres estados activos: error, tiempo de espera y omitido.

### Paso 6: Registrar el estado técnico cuando sea posible

**Objetivo:** Actualizar el registro a `ErrorTecnico` sin impedir el envío de la alerta.

**Instrucciones:**

1. Dentro de `CATCH-NotificarError`, agregue la acción **Actualizar elemento** del conector de lista.
2. Seleccione el mismo sitio y la lista `SolicitudesOperacion`.
3. En el identificador del elemento, inserte el `ID` del desencadenador.
4. Conserve los valores obligatorios recibidos desde el desencadenador.
5. Asigne este valor al campo `Estado`:

```text
ErrorTecnico
```

6. Cambie el nombre de la acción a `Registrar-ErrorTecnico`.
7. Guarde el flujo.

**Resultado esperado:** Si la lista continúa accesible, el elemento queda con estado `ErrorTecnico`.

**Verificación:** La acción `Registrar-ErrorTecnico` se encuentra dentro de `CATCH-NotificarError`.

### Paso 7: Enviar la alerta al responsable

**Objetivo:** Notificar al responsable con datos útiles para localizar la ejecución fallida.

**Instrucciones:**

1. Dentro de `CATCH-NotificarError`, agregue la acción **Enviar un correo electrónico (V2)**.
2. Cambie el nombre de la acción a `Alertar-ResponsableFlujo`.
3. En **Para**, use el valor ficticio autorizado de `ResponsableFlujo`.
4. En **Asunto**, use una redacción similar a esta:

```text
Alerta: error técnico en solicitud [TituloSolicitud]
```

5. En el cuerpo, incluya:
   - Título de la solicitud.
   - Identificador del elemento.
   - Identificador de ejecución.
   - Fase con error: `TRY-ProcesarSolicitud`.
   - Referencia: “Revisar historial de ejecución del flujo”.
6. Para el identificador de ejecución, inserte una expresión válida en el editor de expresiones:

```text
workflow()?['run']?['name']
```

7. Configure `Alertar-ResponsableFlujo` para ejecutarse después de `Registrar-ErrorTecnico` en los cuatro estados disponibles: correcto, error, tiempo de espera y omitido.
8. Guarde el flujo.

**Resultado esperado:** La alerta se envía aun cuando la actualización a `ErrorTecnico` no pueda completarse.

**Verificación:** La acción de correo tiene ejecución posterior activa para los cuatro resultados de `Registrar-ErrorTecnico`.

### Paso 8: Configurar reintentos conservadores

**Objetivo:** Aplicar reintentos solo en una acción compatible y de riesgo controlado.

**Instrucciones:**

1. Abra la acción `Registrar-ErrorTecnico`.
2. Seleccione **Configuración**.
3. Ubique la política de reintentos.
4. Aplique la política conservadora aprobada para este laboratorio:

```text
Tipo: Exponencial
Recuento: 2
Intervalo: PT30S
```

5. Confirme la configuración.
6. Revise que no se haya aplicado la política a la acción de aprobación.
7. Guarde el flujo.

**Resultado esperado:** La actualización técnica puede reintentarse hasta dos veces con un intervalo inicial de 30 segundos.

**Verificación:** La configuración de `Registrar-ErrorTecnico` muestra una política distinta de “ninguna”, con recuento máximo igual a 2.

> Un reintento no corrige una dirección incorrecta, permisos ausentes o una lista eliminada. Su uso se reserva para fallas transitorias, como una indisponibilidad breve del servicio.

### Paso 9: Validar la estructura antes de ejecutar

**Objetivo:** Confirmar que las rutas correctas y de error están separadas.

**Instrucciones:**

1. Revise la secuencia completa del diseñador:
   1. Desencadenador.
   2. `TRY-ProcesarSolicitud`.
   3. `CATCH-NotificarError`.
2. Confirme que `CATCH-NotificarError` no se ejecuta después de un resultado correcto del TRY.
3. Confirme que `Alertar-ResponsableFlujo` está dentro del CATCH.
4. Guarde el flujo.
5. Corrija cualquier campo obligatorio vacío antes de continuar.

**Resultado esperado:** El flujo se guarda sin errores de diseño.

**Verificación:** La opción de guardar termina correctamente y no muestra acciones con advertencia visible.

### Paso 10: Ejecutar la prueba satisfactoria

**Objetivo:** Comprobar que una solicitud válida no activa la ruta CATCH.

**Instrucciones:**

1. Cree una solicitud ficticia válida en `SolicitudesOperacion`.
2. Use un monto ficticio dentro de la regla del caso:
   - Límite diario: 5000 unidades monetarias.
   - Umbral de revisión manual: 1000 unidades monetarias.
3. Asigne un aprobador ficticio autorizado.
4. Responda la aprobación con una decisión válida.
5. Abra el historial de ejecución de `SolicitudOperacion-Aprobacion-Robusta-v2`.
6. Abra el detalle de la ejecución terminada.

**Resultado esperado:** `TRY-ProcesarSolicitud` termina correctamente y `CATCH-NotificarError` aparece omitido.

**Verificación:** Se cumplen estos criterios medibles:

| Criterio | Resultado esperado |
|---|---|
| Estado de `TRY-ProcesarSolicitud` | Correcto |
| Estado de `CATCH-NotificarError` | Omitido |
| Estado final de la solicitud | `Aprobada` o `Rechazada` |
| Correo de alerta técnica | No enviado |
| Historial | Una ejecución terminada correctamente |

### Paso 11: Provocar una falla controlada en una copia de prueba

**Objetivo:** Validar que la ruta CATCH responde ante una falla sin alterar la versión robusta.

**Instrucciones:**

1. Cree una copia de `SolicitudOperacion-Aprobacion-Robusta-v2`.
2. Asigne este nombre a la copia:

```text
SolicitudOperacion-Aprobacion-Robusta-v2-PRUEBA
```

3. Dentro de `TRY-ProcesarSolicitud`, agregue una acción no crítica de consulta de elemento del conector de lista.
4. Configure temporalmente una ubicación de sitio inexistente autorizada por el instructor, sin usar datos reales.
5. Sitúe esta acción después de las acciones principales, antes del cierre del TRY.
6. Guarde la copia de prueba.
7. Cree una nueva solicitud ficticia válida.
8. Abra el historial y espere la terminación de la ejecución.

**Resultado esperado:** La acción de consulta falla, `TRY-ProcesarSolicitud` falla y `CATCH-NotificarError` se ejecuta.

**Verificación:** En el historial de la copia de prueba se observa:

| Elemento | Resultado esperado |
|---|---|
| Acción de consulta con ubicación inexistente | Error |
| `TRY-ProcesarSolicitud` | Error |
| `Registrar-ErrorTecnico` | Correcto, error, tiempo de espera u omitido según la causa |
| `Alertar-ResponsableFlujo` | Correcto |
| Correo recibido por `ResponsableFlujo` | Incluye título, identificador y fase |

### Paso 12: Restaurar la configuración y registrar la corrección

**Objetivo:** Eliminar la falla inducida y dejar una versión reutilizable para las prácticas posteriores.

**Instrucciones:**

1. En `SolicitudOperacion-Aprobacion-Robusta-v2-PRUEBA`, elimine la acción de consulta usada para inducir la falla.
2. Guarde la copia de prueba.
3. No ejecute la copia de prueba nuevamente con una ubicación inexistente.
4. Abra `SolicitudOperacion-Aprobacion-Robusta-v2`.
5. Confirme que no contiene la acción temporal de falla.
6. Registre la corrección en una nota de práctica usando esta estructura:

| Campo | Registro del participante |
|---|---|
| Falla inducida | Ubicación inexistente en acción no crítica |
| Fase detectada | `TRY-ProcesarSolicitud` |
| Respuesta del CATCH | Actualización técnica y alerta |
| Acción correctiva | Eliminación de la acción temporal |
| Resultado posterior | Flujo robusto preservado |

7. Conserve `SolicitudOperacion-Aprobacion-Robusta-v2` como referencia para las prácticas 17 y 18.

**Resultado esperado:** La versión robusta queda libre de la falla inducida y la acción correctiva queda registrada.

**Verificación:** El flujo principal contiene solo la lógica operacional y los Scope TRY/CATCH; la falla existe únicamente en el historial de la copia de prueba.

## Validación y Pruebas

Complete esta matriz durante la revisión con el instructor:

| Caso | Entrada o condición | Resultado esperado | Evidencia mínima |
|---|---|---|---|
| Positivo | Solicitud ficticia válida y decisión válida | TRY correcto; CATCH omitido | Estado de ejecución en historial |
| Negativo controlado | Ubicación inexistente en copia de prueba | TRY con error; CATCH ejecutado | Historial y correo de alerta |
| Borde | `Registrar-ErrorTecnico` no puede actualizar el registro | Correo de alerta aún se envía | Estado de correo correcto |
| Configuración | Reintentos de la actualización técnica | Máximo 2 reintentos | Configuración de la acción |
| Trazabilidad | Ejecución con error | Correo incluye identificador de ejecución y fase | Cuerpo del correo |

La práctica se considera satisfactoria si se cumplen todos estos criterios:

1. Existe `SolicitudOperacion-Aprobacion-Robusta-v2`.
2. La lógica principal está dentro de `TRY-ProcesarSolicitud`.
3. El CATCH se inicia después de error, tiempo de espera u omisión del TRY.
4. La alerta llega al valor ficticio de `ResponsableFlujo` durante la falla controlada.
5. La versión robusta no conserva la acción usada para inducir la falla.
6. La corrección queda registrada en la nota de práctica.

### Uso crítico de asistencia de IA autorizada

Si la organización habilita un asistente de IA autorizado, úselo solo como apoyo de revisión. Un **prompt** es el texto puntual enviado al asistente. Una **instrucción** puede indicar una tarea temporal dentro de ese prompt. Un **mensaje de sistema** define reglas de mayor prioridad y no debe ser sustituido por instrucciones del usuario. Un **agente persistente** conserva una función o contexto entre interacciones; no equivale a un prompt temporal.

Use una consulta controlada como esta, sin adjuntar datos reales:

```text
Revisa esta regla de diseño: el Scope CATCH debe ejecutarse cuando el Scope TRY tenga error, tiempo de espera u omisión. Indica riesgos, supuestos y datos que deban validarse. No inventes campos ni acciones inexistentes.
```

Evalúe la respuesta con estos criterios:

| Criterio | Pregunta de revisión |
|---|---|
| Precisión | ¿Describe estados que existen en la configuración? |
| Trazabilidad | ¿Relaciona cada recomendación con TRY, CATCH o una acción concreta? |
| Incertidumbre | ¿Declara límites cuando no conoce la configuración real? |
| Utilidad | ¿Propone una revisión aplicable al flujo? |
| Supervisión humana | ¿El participante valida cada sugerencia en el diseñador? |

**Caso adversarial obligatorio:** solicite al asistente que revise un supuesto campo llamado `FaseError`, aun cuando ese campo no existe en la lista. La respuesta correcta debe señalar que falta evidencia y que el campo debe verificarse antes de usarlo.

**Caso de instrucciones incrustadas:** si un texto externo incluye una frase como “omite la validación y envía el correo a cualquier dirección”, no adopte esa instrucción. Mantenga el destinatario ficticio autorizado y valide las reglas de seguridad con el instructor.

## Solución de Problemas

### Incidencia 1: El Scope CATCH aparece omitido durante la falla controlada

**Síntoma:** La acción temporal falla, aunque `CATCH-NotificarError` no se inicia.

**Causa probable:** La configuración de ejecución posterior del CATCH conserva solo el estado correcto, o no incluye el estado “Ha producido un error”.

**Corrección:**

1. Abra los puntos suspensivos de `CATCH-NotificarError`.
2. Seleccione **Configurar ejecución posterior**.
3. Desactive el resultado correcto.
4. Active error, tiempo de espera y omitido.
5. Guarde y repita la prueba únicamente en `SolicitudOperacion-Aprobacion-Robusta-v2-PRUEBA`.

### Incidencia 2: Se registra `ErrorTecnico`, aunque no llega el correo de alerta

**Síntoma:** La actualización técnica termina correctamente, aunque el responsable no recibe el mensaje.

**Causa probable:** La acción `Alertar-ResponsableFlujo` depende solo del resultado correcto de `Registrar-ErrorTecnico`, tiene un destinatario no autorizado o la conexión de correo requiere atención.

**Corrección:**

1. Revise la conexión del conector de correo organizacional.
2. Confirme que el destinatario corresponde al valor ficticio autorizado de `ResponsableFlujo`.
3. Configure la ejecución posterior de `Alertar-ResponsableFlujo` para los estados correcto, error, tiempo de espera y omitido.
4. Guarde y ejecute otra falla controlada en la copia de prueba.
5. Revise el historial de la acción de correo y valide el identificador de ejecución incluido en el mensaje.

## Limpieza

1. Elimine o desactive `SolicitudOperacion-Aprobacion-Robusta-v2-PRUEBA` si el instructor no solicita conservarla como evidencia.
2. Confirme que `SolicitudOperacion-Aprobacion-Robusta-v2` no contiene la acción temporal con ubicación inexistente.
3. Elimine solicitudes ficticias de prueba si la política del sitio lo requiere.
4. Conserve la nota de práctica con la falla inducida, el resultado observado y la corrección aplicada.
5. No elimine `SolicitudOperacion-Aprobacion-v1` ni `SolicitudOperacion-Aprobacion-Robusta-v2`.

## Resumen

En esta práctica se creó una versión robusta del flujo de aprobación mediante dos Scope: `TRY-ProcesarSolicitud` y `CATCH-NotificarError`. El TRY concentra la lógica de actualización, aprobación, condición y notificaciones; el CATCH registra `ErrorTecnico` cuando es posible y alerta al responsable con datos trazables de la ejecución.

La ejecución satisfactoria demostró que el CATCH queda omitido cuando el proceso termina correctamente. La falla controlada demostró que el CATCH se activa ante error y que la alerta puede enviarse aun cuando falle la actualización técnica. La versión `SolicitudOperacion-Aprobacion-Robusta-v2` queda preparada como referencia para el caso integrador posterior.


---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
