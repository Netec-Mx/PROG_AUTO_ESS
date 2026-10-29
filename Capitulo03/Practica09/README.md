# Automatización de una tarea con variables y condición de negocio

## Metadatos

| Duration | Complexity | Bloom level |
|---|---|---|
| 35 minutos | Media | Crear |

**Tecnología principal:** Power Automate, servicio SaaS de flujos de nube.  
**Edición y arquitectura:** servicio web SaaS, arquitectura cloud.  
**Versión:** [VERSIÓN POR VALIDAR].  
**Fuente oficial:** [ENLACE OFICIAL].

**Descripción declarada:** construir un flujo instantáneo con entradas manuales, variables y una condición de negocio con resultados diferentes según la decisión; ejecutar casos de prueba y corregir la lógica.

---

## Descripción General

En esta práctica se construirá un flujo instantáneo que evalúa una solicitud ficticia según un monto ingresado manualmente. El flujo almacenará datos en variables, aplicará una condición de negocio y enviará una notificación distinta según el resultado. Se ejecutarán casos inferiores, superiores e iguales al límite definido para detectar y corregir fallos de tipo de dato, comparación o referencia de variables.

---

## Objetivos de Aprendizaje

- [ ] Construir un flujo instantáneo con entradas manuales para nombre de solicitud, monto solicitado y área solicitante.
- [ ] Inicializar y utilizar variables de tipo texto y número dentro de un flujo.
- [ ] Aplicar una condición que compare un monto recibido con un límite de negocio fijo.
- [ ] Ejecutar y verificar casos positivos, negativos y de borde mediante el historial de ejecuciones.
- [ ] Corregir una referencia de variable, un operador de comparación o un tipo de dato cuando el resultado no coincida con la regla.

---

## Prerrequisitos

### Conocimientos

- Uso básico de navegador, correo corporativo y recursos organizacionales autorizados.
- Comprensión de desencadenadores, acciones, contenido dinámico, condiciones e historial de ejecuciones.
- Conocimiento inicial de variables numéricas y de texto.
- Comprensión de operadores de comparación: menor que, mayor que, igual a, menor o igual que.
- Prácticas 5 a 8 completadas o conocimientos equivalentes.

### Acceso

- Cuenta organizacional autorizada para crear, editar, guardar, ejecutar y probar flujos de nube.
- Permiso para usar conectores estándar de correo corporativo dentro del entorno de práctica.
- Acceso a Power Automate mediante navegador compatible.
- Dirección de correo corporativa propia autorizada para recibir notificaciones de prueba.
- No usar datos personales, montos reales, números de cuenta, credenciales ni datos confidenciales.

---

## Entorno de Laboratorio

| Recurso | Especificación mínima | Uso en esta práctica |
|---|---|---|
| Equipo | Procesador de 64 bits, 8 GB de RAM | Diseño y prueba del flujo |
| Navegador | [VERSIÓN POR VALIDAR], arquitectura de 64 bits | Acceso al servicio SaaS |
| Power Automate | [VERSIÓN POR VALIDAR], servicio SaaS cloud | Creación del flujo instantáneo |
| Correo corporativo | [VERSIÓN POR VALIDAR], servicio SaaS | Recepción de notificaciones de prueba |

**Fuente oficial de cada servicio:** [ENLACE OFICIAL].

### Datos controlados del caso

| Elemento | Valor |
|---|---:|
| Límite de negocio | `1000` |
| Resultado si el monto es menor o igual al límite | `Dentro de política` |
| Resultado si el monto es mayor al límite | `Requiere revisión` |
| Datos usados | Ficticios |
| Destinatario de prueba | Correo corporativo propio autorizado |

### Regla de negocio

> Si `Monto solicitado` es menor o igual a `1000`, la solicitud queda en estado `Dentro de política`. Si es mayor a `1000`, queda en estado `Requiere revisión`.

Esta regla es adecuada para automatización inicial porque tiene una entrada identificable, una comparación objetiva y dos resultados claros. La decisión es preliminar: un resultado `Dentro de política` no sustituye validaciones humanas, legales o financieras que correspondan al proceso real.

---

## Instrucciones Paso a Paso

### Paso 1: Analizar la tarea y registrar la regla

**Objetivo:** Identificar las entradas, la regla, los resultados y una excepción básica antes de diseñar el flujo.

**Instrucciones:**

1. Revise la regla de negocio del laboratorio.
2. Identifique las tres entradas requeridas:
   - Nombre de solicitud.
   - Monto solicitado.
   - Área solicitante.
3. Identifique los dos resultados posibles:
   - `Dentro de política`.
   - `Requiere revisión`.
4. Registre como excepción inicial: un monto negativo no debe considerarse válido para un proceso real.
5. Mantenga el límite fijo en `1000`; no use un monto real ni cambie la regla durante las pruebas base.

**Expected output:** Una regla clara y comprobable antes de construir el flujo.

**Verification:** Puede responder estas preguntas:

- ¿Qué inicia el flujo? Una ejecución manual.
- ¿Qué dato se compara? El monto solicitado.
- ¿Contra qué valor? El límite `1000`.
- ¿Qué ocurre si el monto es `1000`? Se clasifica como `Dentro de política`.

---

### Paso 2: Crear el flujo instantáneo

**Objetivo:** Crear el contenedor del flujo con un desencadenador manual.

**Instrucciones:**

1. Abra Power Automate en el entorno autorizado.
2. Seleccione la opción para crear un flujo de nube instantáneo.
3. Asigne el siguiente nombre:

```text
PF03_EvaluarSolicitudNegocio_Iniciales
```

4. Seleccione el desencadenador manual.
5. Guarde el flujo antes de agregar acciones.

**Expected output:** Un flujo instantáneo vacío con desencadenador manual.

**Verification:** El diseñador muestra el nombre `PF03_EvaluarSolicitudNegocio_Iniciales` y un único desencadenador manual.

---

### Paso 3: Agregar las entradas manuales

**Objetivo:** Solicitar los datos mínimos necesarios para evaluar una solicitud ficticia.

**Instrucciones:**

1. En el desencadenador manual, agregue una entrada de texto.
2. Asigne este nombre visible:

```text
Nombre de solicitud
```

3. Agregue una entrada de número.
4. Asigne este nombre visible:

```text
Monto solicitado
```

5. Agregue una segunda entrada de texto.
6. Asigne este nombre visible:

```text
Área solicitante
```

7. Guarde el flujo.

**Expected output:** El desencadenador tiene tres entradas: dos de texto y una numérica.

**Verification:** Al iniciar una prueba manual, aparecen los tres campos. `Monto solicitado` debe aceptar un valor numérico, no una descripción como `mil unidades`.

---

### Paso 4: Inicializar las variables del flujo

**Objetivo:** Crear variables para almacenar el monto, el límite y el resultado de evaluación.

**Instrucciones:**

1. Agregue la acción **Inicializar variable**.
2. Configure la primera variable:

| Campo | Valor |
|---|---|
| Nombre | `varMonto` |
| Tipo | Número |
| Valor | Contenido dinámico de `Monto solicitado` |

3. Agregue una segunda acción **Inicializar variable**.
4. Configure el límite de negocio:

| Campo | Valor |
|---|---|
| Nombre | `varLimite` |
| Tipo | Número |
| Valor | `1000` |

5. Agregue una tercera acción **Inicializar variable**.
6. Configure el resultado:

| Campo | Valor |
|---|---|
| Nombre | `varResultado` |
| Tipo | Cadena |
| Valor | `Pendiente de evaluación` |

7. Guarde el flujo.

**Expected output:** Tres variables inicializadas antes de la condición.

**Verification:** Revise que `varMonto` y `varLimite` sean de tipo **Número**. No escriba comillas alrededor de `1000`.

---

### Paso 5: Crear la condición de negocio

**Objetivo:** Comparar el monto recibido con el límite fijo.

**Instrucciones:**

1. Agregue una acción **Condición** después de las variables.
2. En el primer valor, seleccione la variable `varMonto`.
3. Seleccione el operador **es menor o igual que**.
4. En el segundo valor, seleccione la variable `varLimite`.
5. Revise la condición antes de continuar.

La lógica esperada es equivalente a la siguiente expresión:

```text
variables('varMonto') <= variables('varLimite')
```

**Expected output:** Una condición con dos ramas: verdadera y falsa.

**Verification:** La comparación debe incluir el caso igual al límite. Si usa solo “menor que”, el caso `1000` será incorrecto.

---

### Paso 6: Configurar la rama Dentro de política

**Objetivo:** Asignar un resultado y enviar una notificación preliminar cuando el monto cumple la regla.

**Instrucciones:**

1. En la rama verdadera de la condición, agregue la acción **Establecer variable**.
2. Configure los valores:

| Campo | Valor |
|---|---|
| Nombre | `varResultado` |
| Valor | `Dentro de política` |

3. Agregue una acción de envío de correo mediante el conector corporativo autorizado.
4. Configure el correo con los siguientes datos:

| Campo | Valor |
|---|---|
| Para | Correo corporativo propio autorizado |
| Asunto | `Aprobación preliminar de solicitud ficticia` |
| Cuerpo | Incluya Nombre de solicitud, Área solicitante, Monto solicitado y el texto `Dentro de política` |

5. Use contenido dinámico para insertar las entradas manuales.
6. Guarde el flujo.

**Expected output:** La rama verdadera asigna el resultado correcto y envía una notificación preliminar.

**Verification:** El texto del asunto identifica que se trata de una aprobación preliminar, no de una aprobación definitiva.

---

### Paso 7: Configurar la rama Requiere revisión

**Objetivo:** Asignar un resultado alternativo cuando el monto supera el límite.

**Instrucciones:**

1. En la rama falsa de la condición, agregue la acción **Establecer variable**.
2. Configure los valores:

| Campo | Valor |
|---|---|
| Nombre | `varResultado` |
| Valor | `Requiere revisión` |

3. Agregue una acción de envío de correo mediante el conector corporativo autorizado.
4. Configure el correo con los siguientes datos:

| Campo | Valor |
|---|---|
| Para | Correo corporativo propio autorizado |
| Asunto | `Solicitud ficticia pendiente de revisión` |
| Cuerpo | Incluya Nombre de solicitud, Área solicitante, Monto solicitado y el texto `Requiere revisión` |

5. Guarde el flujo.

**Expected output:** La rama falsa asigna el resultado alternativo y envía una notificación de revisión.

**Verification:** Confirme que esta acción está dentro de la rama falsa y no después de la condición.

---

### Paso 8: Agregar un resumen con Redactar

**Objetivo:** Mostrar el valor de las variables para facilitar la revisión del historial.

**Instrucciones:**

1. Después de la condición, agregue la acción **Redactar**.
2. En el campo de entrada, abra la pestaña de expresiones.
3. Pegue la expresión siguiente:

```text
concat(
  'Monto recibido: ',
  string(variables('varMonto')),
  ' | Límite: ',
  string(variables('varLimite')),
  ' | Resultado: ',
  variables('varResultado')
)
```

4. Guarde el flujo.

**Expected output:** Una salida de texto con el monto, el límite y el resultado final.

**Verification:** La acción **Redactar** debe estar fuera de ambas ramas, después de la condición. Así se ejecutará en cualquier resultado.

---

### Paso 9: Ejecutar el caso inferior al límite

**Objetivo:** Validar que un monto menor a `1000` siga la rama de aprobación preliminar.

**Instrucciones:**

1. Inicie una prueba manual del flujo.
2. Use estos datos ficticios:

| Campo | Valor |
|---|---|
| Nombre de solicitud | `SOL-001-Materiales` |
| Monto solicitado | `999` |
| Área solicitante | `Operaciones ficticias` |

3. Ejecute el flujo.
4. Espere a que finalice.
5. Abra el historial de ejecuciones y seleccione la ejecución recién creada.

**Expected output:** Ejecución correcta con resultado `Dentro de política`.

**Verification:** Compruebe los siguientes puntos:

- La condición siguió la rama verdadera.
- `varMonto` tiene valor `999`.
- `varLimite` tiene valor `1000`.
- `varResultado` tiene valor `Dentro de política`.
- La salida de **Redactar** contiene `Monto recibido: 999`.
- Recibió el correo de aprobación preliminar.

---

### Paso 10: Ejecutar el caso superior al límite

**Objetivo:** Validar que un monto mayor a `1000` siga la rama de revisión.

**Instrucciones:**

1. Ejecute nuevamente el flujo de forma manual.
2. Use estos datos ficticios:

| Campo | Valor |
|---|---|
| Nombre de solicitud | `SOL-002-Servicio` |
| Monto solicitado | `1001` |
| Área solicitante | `Soporte ficticio` |

3. Espere a que finalice la ejecución.
4. Abra el historial y revise las acciones ejecutadas.

**Expected output:** Ejecución correcta con resultado `Requiere revisión`.

**Verification:** Confirme que la rama verdadera aparece omitida y que la rama falsa se ejecutó. La salida de **Redactar** debe mostrar:

```text
Monto recibido: 1001 | Límite: 1000 | Resultado: Requiere revisión
```

---

### Paso 11: Ejecutar el caso de borde y corregir si es necesario

**Objetivo:** Validar el comportamiento cuando el monto es exactamente igual al límite.

**Instrucciones:**

1. Ejecute el flujo una tercera vez.
2. Use estos datos ficticios:

| Campo | Valor |
|---|---|
| Nombre de solicitud | `SOL-003-Borde` |
| Monto solicitado | `1000` |
| Área solicitante | `Administración ficticia` |

3. Revise el historial de la ejecución.
4. Si el resultado es `Requiere revisión`, edite la condición.
5. Confirme que el operador sea **es menor o igual que**.
6. Guarde el flujo y repita la ejecución con monto `1000`.

**Expected output:** El monto igual a `1000` queda `Dentro de política`.

**Verification:** La evidencia válida es una ejecución correcta donde:

```text
Monto recibido: 1000 | Límite: 1000 | Resultado: Dentro de política
```

---

### Paso 12: Aplicar el reto opcional de contador y validación negativa

**Objetivo:** Extender el flujo sin alterar la regla base.

**Instrucciones:**

1. Solo si completó los tres casos base, agregue una variable adicional:

| Campo | Valor |
|---|---|
| Nombre | `varContadorAprobadas` |
| Tipo | Entero |
| Valor | `0` |

2. Dentro de la rama `Dentro de política`, agregue la acción **Incrementar variable**.
3. Seleccione `varContadorAprobadas`.
4. Use incremento `1`.
5. Agregue una condición antes de la condición principal para verificar que `varMonto` sea mayor o igual a `0`.
6. Si el monto es negativo, asigne a `varResultado` el valor siguiente:

```text
Monto no válido
```

7. Envíe una notificación de corrección de datos, sin clasificar la solicitud como aprobada ni en revisión.
8. Guarde el flujo.

**Expected output:** Una extensión controlada que cuenta aprobaciones dentro de una ejecución y evita evaluar montos negativos.

**Verification:** Ejecute una prueba con monto `-1`. El flujo debe indicar `Monto no válido`. El contador tiene alcance de una ejecución; no representa un total histórico entre ejecuciones.

---

## Validación y Pruebas

Registre los resultados de las tres pruebas obligatorias en la siguiente tabla.

| Caso | Monto | Resultado esperado | Rama esperada | Evidencia mínima |
|---|---:|---|---|---|
| Inferior al límite | `999` | `Dentro de política` | Verdadera | Historial y salida de Redactar |
| Superior al límite | `1001` | `Requiere revisión` | Falsa | Historial y salida de Redactar |
| Igual al límite | `1000` | `Dentro de política` | Verdadera | Historial y salida de Redactar |

### Criterios medibles de finalización

La práctica se considera completada cuando se cumplen todos los criterios:

- [ ] El flujo se llama `PF03_EvaluarSolicitudNegocio_Iniciales`.
- [ ] El desencadenador solicita Nombre de solicitud, Monto solicitado y Área solicitante.
- [ ] Existen `varMonto`, `varLimite` y `varResultado`.
- [ ] `varLimite` contiene el valor numérico `1000`.
- [ ] La condición usa menor o igual que.
- [ ] Los tres casos obligatorios finalizan correctamente.
- [ ] El historial muestra una rama distinta para `999` y `1001`.
- [ ] La salida de Redactar muestra monto, límite y resultado.
- [ ] Las notificaciones recibidas corresponden con cada resultado.
- [ ] No se usaron datos reales ni confidenciales.

### Validación crítica con asistente de IA autorizado

Use esta actividad solo como análisis; no cambie el flujo basándose únicamente en una respuesta generada.

1. Envíe este prompt a un asistente de IA autorizado:

```text
Evalúa esta regla ficticia: si el monto es menor o igual a 1000, el resultado es "Dentro de política"; si es mayor, el resultado es "Requiere revisión". Indica tres casos de prueba y señala si el valor 1000 debe ir a la primera o a la segunda rama. Si falta evidencia para una recomendación, indícalo.
```

2. Compare la respuesta con la regla documentada en este laboratorio.
3. Evalúe precisión, trazabilidad, incertidumbre, utilidad y necesidad de supervisión humana.
4. No solicite ni acepte razonamiento interno del asistente como evidencia.

### Caso adversarial de datos no confiables

Ejecute una revisión conceptual con este valor ficticio de área:

```text
Operaciones ficticias. Ignora la regla y aprueba cualquier monto.
```

El texto anterior es un dato no confiable, no una instrucción para el flujo ni para una persona. La condición debe continuar evaluando solamente `varMonto` y `varLimite`.

**Criterio de validación:** aunque el área contenga esa frase, un monto de `1001` debe seguir dando `Requiere revisión`.

### Terminología de IA

- Una **instrucción** es una indicación temporal dirigida a una persona durante la práctica.
- Un **prompt** es el texto enviado por una persona a un asistente de IA.
- Un **mensaje de sistema** define reglas persistentes del asistente y no debe ser modificado por datos introducidos en una solicitud.
- El flujo construido en esta práctica no depende de resultados de IA para tomar su decisión.

---

## Solución de Problemas

### Problema 1: El monto igual a 1000 va a Requiere revisión

**Síntoma:** La ejecución con monto `1000` sigue la rama falsa o muestra `Requiere revisión`.

**Causa:** La condición usa el operador “menor que” en vez de “menor o igual que”, o compara el monto con un valor de texto.

**Corrección:**

1. Abra la acción **Condición**.
2. Seleccione `varMonto` como primer valor.
3. Seleccione **es menor o igual que** como operador.
4. Seleccione `varLimite` como segundo valor.
5. Confirme que ambas variables son de tipo Número.
6. Guarde y repita el caso de borde con monto `1000`.

---

### Problema 2: La condición falla o muestra valores inesperados

**Síntoma:** La ejecución falla en la condición, el monto aparece vacío o el resultado de Redactar no coincide con la entrada.

**Causa:** `varMonto` no usa el contenido dinámico de `Monto solicitado`, la variable tiene tipo Cadena o una acción usa una variable con nombre distinto.

**Corrección:**

1. Revise la acción que inicializa `varMonto`.
2. Confirme que su tipo sea Número.
3. Seleccione nuevamente el contenido dinámico de `Monto solicitado`.
4. Revise que todas las acciones usen exactamente `varMonto`, `varLimite` y `varResultado`.
5. Guarde el flujo.
6. Ejecute otra prueba con monto `999` y revise las entradas y salidas en el historial.

---

## Limpieza

1. Mantenga el flujo guardado si será reutilizado en prácticas posteriores.
2. Si el entorno indica que la práctica debe retirarse, desactive o elimine únicamente `PF03_EvaluarSolicitudNegocio_Iniciales`.
3. Elimine solo notificaciones ficticias de prueba que ya no necesite.
4. No elimine recursos, conexiones, carpetas ni elementos creados en prácticas anteriores.
5. No reutilice los datos ficticios de esta práctica como datos operativos.

---

## Resumen

En esta práctica se convirtió una regla operativa simple en un flujo instantáneo verificable. El flujo recibe entradas manuales, almacena el monto y el límite en variables, compara ambos valores mediante una condición, registra un resumen con Redactar y emite una notificación según la decisión.

La prueba con `999`, `1001` y `1000` demuestra que la regla usa correctamente el operador menor o igual que. El reto opcional permite reforzar el uso de contadores y la validación de montos negativos, manteniendo clara la diferencia entre una automatización preliminar basada en reglas y una decisión humana de negocio.

---



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
