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

# Contador y acumulador sobre un conjunto de datos

## Metadatos

| Campo | Valor |
|---|---|
| Duration | 45 minutos |
| Complexity | Media |
| Bloom level | Crear |

## Descripción General

En esta práctica construirá un flujo instantáneo que procesa datos ficticios definidos dentro del propio flujo. El flujo recorrerá un arreglo, evaluará el estado de cada registro y calculará dos resultados: cantidad de registros aprobados e importe total aprobado.

**Descripción declarada:** procesar un arreglo de datos de prueba definido en el propio flujo, recorrer sus elementos con Apply to each, aplicar condiciones y generar resultados consolidados con contador y acumulador.

El caso representa una actividad repetitiva basada en reglas claras: revisar registros estructurados y producir un resumen verificable.

## Objetivos de Aprendizaje

- [ ] Definir un arreglo de datos ficticios dentro de un flujo instantáneo.
- [ ] Inicializar una variable entera para contar aprobaciones y una variable decimal para sumar importes.
- [ ] Recorrer registros mediante **Apply to each** y evaluar una regla con **Condition**.
- [ ] Usar expresiones para actualizar un acumulador y producir un resumen consolidado.
- [ ] Comprobar resultados con casos positivos, negativos, de borde y una cadena hostil tratada solo como dato.

## Prerrequisitos

**Conocimientos**

- Uso básico del diseñador de flujos y de la ejecución manual.
- Conceptos de variable, arreglo, condición, contador y acumulador.
- Lectura básica de expresiones de Power Automate.
- Comprensión de que una automatización adecuada requiere entradas estructuradas, reglas claras y resultados verificables.

**Acceso**

- Cuenta autorizada con permiso para crear, guardar, ejecutar y probar flujos instantáneos.
- Acceso al entorno autorizado de Power Automate.
- Conexión HTTPS estable.
- No se requieren conectores, archivos externos, acciones Premium, bases de datos ni servicios adicionales.

## Entorno de Laboratorio

| Recurso | Requisito |
|---|---|
| Equipo | Computador con teclado, dispositivo apuntador y conexión estable |
| Pantalla | Resolución mínima de 1366 × 768; recomendada 1920 × 1080 |
| Servicio | Power Automate, edición SaaS para flujos de nube |
| Versión | [VERSIÓN POR VALIDAR] |
| Arquitectura | No aplica; servicio SaaS |
| Fuente oficial | [ENLACE OFICIAL] |

No se requieren comandos de terminal ni archivos auxiliares. Todo el conjunto de prueba se escribirá dentro del flujo.

> **Nota de continuidad:** esta práctica crea un flujo nuevo e independiente. No modifique el flujo realizado en el laboratorio anterior.

## Instrucciones Paso a Paso

### Paso 1: Revisar la regla de negocio y los resultados esperados

**Objetivo:** Identificar la entrada, la regla y las salidas que resolverá el flujo.

**Instrucciones:**

1. Lea la regla del caso:
   - Un registro cuenta como aprobado cuando `Estado` es igual a `Aprobado`.
   - Solo los registros aprobados incrementan el contador.
   - Solo los registros aprobados suman su `Importe` al acumulador.
2. Identifique las entradas: `Id`, `Categoria`, `Estado` e `Importe`.
3. Identifique las salidas:
   - Cantidad de registros aprobados.
   - Importe acumulado de registros aprobados.
4. Anote el resultado esperado del conjunto inicial: `4` aprobados y `4000.5` de importe acumulado.

**Resultado esperado:** Regla de negocio clara, medible y basada en datos estructurados.

**Verificación:** Puede explicar qué dato decide la aprobación y qué variables cambiarán cuando un registro cumpla la regla.

---

### Paso 2: Crear el flujo instantáneo

**Objetivo:** Crear el contenedor del flujo que se iniciará manualmente.

**Instrucciones:**

1. Abra Power Automate en el entorno autorizado.
2. Seleccione **Crear**.
3. Elija **Flujo de nube instantáneo**.
4. Asigne este nombre al flujo:

   `PF03_ContadorAcumulador_DatosPrueba`

5. Seleccione el desencadenador manual.
6. Cree el flujo.
7. Guarde antes de agregar acciones.

**Resultado esperado:** Un flujo instantáneo con un desencadenador manual.

**Verificación:** El diseñador muestra el nombre `PF03_ContadorAcumulador_DatosPrueba` y un único desencadenador manual.

---

### Paso 3: Inicializar el arreglo de registros ficticios

**Objetivo:** Definir dentro del flujo el conjunto estructurado que se procesará.

**Instrucciones:**

1. Después del desencadenador, agregue la acción **Initialize variable**.
2. Configure la acción según esta tabla:

| Campo | Valor |
|---|---|
| Nombre | `varRegistros` |
| Tipo | Array |
| Valor | Arreglo JSON indicado a continuación |

3. Pegue este arreglo en el campo **Valor**:

```json
[
  {
    "Id": "SOL-001",
    "Categoria": "Operacion",
    "Estado": "Aprobado",
    "Importe": 250.50
  },
  {
    "Id": "SOL-002",
    "Categoria": "Servicio",
    "Estado": "Pendiente",
    "Importe": 120.00
  },
  {
    "Id": "SOL-003",
    "Categoria": "Operacion",
    "Estado": "Aprobado",
    "Importe": 780.00
  },
  {
    "Id": "SOL-004",
    "Categoria": "Tecnologia",
    "Estado": "Aprobado",
    "Importe": 1500.00
  },
  {
    "Id": "SOL-005",
    "Categoria": "Servicio",
    "Estado": "Pendiente",
    "Importe": 99.99
  },
  {
    "Id": "SOL-006",
    "Categoria": "Tecnologia",
    "Estado": "Aprobado",
    "Importe": 1470.00
  }
]
```

4. Guarde el flujo.

**Resultado esperado:** La variable `varRegistros` contiene seis objetos ficticios.

**Verificación:** Revise que el tipo sea **Array** y que existan cuatro registros con `Estado` igual a `Aprobado`.

---

### Paso 4: Inicializar el contador de aprobaciones

**Objetivo:** Crear la variable entera que contará los registros aprobados.

**Instrucciones:**

1. Agregue una acción **Initialize variable** después de `varRegistros`.
2. Configure la variable:

| Campo | Valor |
|---|---|
| Nombre | `varContadorAprobados` |
| Tipo | Integer |
| Valor | `0` |

3. Guarde el flujo.

**Resultado esperado:** El contador inicia en cero antes de recorrer los datos.

**Verificación:** El tipo de `varContadorAprobados` es **Integer** y el valor inicial no tiene comillas.

---

### Paso 5: Inicializar el acumulador de importes

**Objetivo:** Crear la variable decimal que sumará los importes aprobados.

**Instrucciones:**

1. Agregue otra acción **Initialize variable**.
2. Configure la variable:

| Campo | Valor |
|---|---|
| Nombre | `varImporteAcumulado` |
| Tipo | Float |
| Valor | `0` |

3. Guarde el flujo.

**Resultado esperado:** El acumulador está disponible antes del ciclo y comienza en cero.

**Verificación:** Confirme que el tipo sea **Float**. No use tipo **String**, ya que impediría una suma numérica correcta.

---

### Paso 6: Agregar el ciclo Apply to each

**Objetivo:** Recorrer uno a uno los elementos del arreglo.

**Instrucciones:**

1. Agregue la acción **Apply to each** después de las tres variables.
2. En **Select an output from previous steps**, seleccione la variable `varRegistros`.
3. Cambie el nombre visible de la acción a:

   `Recorrer_registros`

4. Guarde el flujo.

**Resultado esperado:** El ciclo recibe el arreglo completo y ejecutará sus acciones una vez por cada registro.

**Verificación:** La entrada del ciclo muestra `varRegistros`. El ciclo no debe recibir una variable individual ni un valor de texto.

---

### Paso 7: Crear la condición de aprobación

**Objetivo:** Evaluar la regla de negocio para cada registro recorrido.

**Instrucciones:**

1. Dentro de `Recorrer_registros`, agregue una acción **Condition**.
2. En el primer campo, seleccione el valor `Estado` del elemento actual.
3. Seleccione el operador **is equal to**.
4. En el segundo campo, escriba:

   `Aprobado`

5. Guarde el flujo.

**Resultado esperado:** La condición tiene dos ramas: una para registros aprobados y otra para registros pendientes.

**Verificación:** La comparación debe usar exactamente `Aprobado`. El valor `Pendiente` no debe incrementar ni sumar.

---

### Paso 8: Incrementar el contador en la rama verdadera

**Objetivo:** Aumentar el contador solo cuando el registro esté aprobado.

**Instrucciones:**

1. En la rama verdadera de la condición, agregue la acción **Increment variable**.
2. Configure la acción:

| Campo | Valor |
|---|---|
| Nombre | `varContadorAprobados` |
| Valor | `1` |

3. Guarde el flujo.

**Resultado esperado:** Cada registro aprobado incrementa el contador en una unidad.

**Verificación:** La acción está dentro de la rama verdadera. Si se ubica fuera de la condición, contaría todos los registros y la regla quedaría incumplida.

---

### Paso 9: Actualizar el acumulador en la rama verdadera

**Objetivo:** Sumar el importe del registro actual al acumulador.

**Instrucciones:**

1. Después de **Increment variable**, dentro de la misma rama verdadera, agregue la acción **Set variable**.
2. Seleccione la variable `varImporteAcumulado`.
3. En el campo de valor, abra la pestaña **Expression**.
4. Escriba esta expresión:

```text
add(variables('varImporteAcumulado'), float(item()?['Importe']))
```

5. Seleccione **Add** o **Update**, según la interfaz disponible.
6. Guarde el flujo.

**Resultado esperado:** El acumulador conserva su valor previo y agrega el importe del elemento actual.

**Verificación:** La expresión contiene:

- `variables('varImporteAcumulado')` para recuperar el total anterior.
- `item()?['Importe']` para leer el importe del registro actual.
- `float(...)` para asegurar una operación decimal.
- `add(...)` para sumar ambos valores.

---

### Paso 10: Mantener vacía la rama falsa

**Objetivo:** Asegurar que los registros no aprobados no alteren los resultados.

**Instrucciones:**

1. Revise la rama falsa de la condición.
2. No agregue acciones en esa rama.
3. Guarde el flujo.

**Resultado esperado:** Los registros con estado distinto de `Aprobado` no modifican el contador ni el acumulador.

**Verificación:** La rama falsa aparece sin acciones. Esto representa una excepción controlada: el registro se revisa, no cumple la regla y no se incluye en el resumen.

---

### Paso 11: Crear el resumen consolidado

**Objetivo:** Mostrar un resultado legible al terminar el ciclo.

**Instrucciones:**

1. Después de `Recorrer_registros`, agregue la acción **Compose**.
2. Cambie el nombre visible de la acción a:

   `Resumen_consolidado`

3. En **Inputs**, abra la pestaña **Expression**.
4. Escriba esta expresión:

```text
concat(
  'Registros aprobados: ',
  string(variables('varContadorAprobados')),
  ' | Importe acumulado: ',
  string(variables('varImporteAcumulado'))
)
```

5. Guarde el flujo.

**Resultado esperado:** La acción produce un texto con ambos resultados consolidados.

**Verificación:** La acción **Compose** está fuera de `Recorrer_registros`. Si estuviera dentro del ciclo, produciría un resumen parcial en cada iteración.

---

### Paso 12: Ejecutar la prueba base

**Objetivo:** Comprobar el comportamiento del flujo con el conjunto inicial.

**Instrucciones:**

1. Seleccione **Test**.
2. Elija ejecución manual.
3. Inicie la prueba.
4. Espere a que todas las acciones terminen.
5. Abra el historial de ejecución.
6. Abra la salida de `Resumen_consolidado`.

**Resultado esperado:** La ejecución termina correctamente.

**Verificación:** El resumen debe mostrar un resultado equivalente a:

```text
Registros aprobados: 4 | Importe acumulado: 4000.5
```

El servicio puede mostrar `4000.50` o `4000.5`; ambos representan el mismo valor numérico.

---

### Paso 13: Revisar el detalle del ciclo

**Objetivo:** Validar que las variables cambiaron solo en las iteraciones aprobadas.

**Instrucciones:**

1. En el historial de la ejecución base, abra `Recorrer_registros`.
2. Revise las seis iteraciones.
3. Identifique las iteraciones de `SOL-001`, `SOL-003`, `SOL-004` y `SOL-006`.
4. Confirme que solo dichas iteraciones ejecutaron:
   - **Increment variable**
   - **Set variable**
5. Revise que `SOL-002` y `SOL-005` siguieron la rama falsa.

**Resultado esperado:** Cuatro iteraciones usan la rama verdadera y dos usan la rama falsa.

**Verificación:** La evidencia mínima es el historial de ejecución con seis iteraciones y la salida consolidada esperada.

---

### Paso 14: Realizar los casos de prueba adicionales

**Objetivo:** Comprobar casos negativos, de borde y una cadena hostil incluida como dato.

**Instrucciones:**

1. Ejecute los casos de la tabla siguiente modificando únicamente `varRegistros`.
2. Guarde y ejecute el flujo después de cada cambio.
3. Registre el resultado de `Resumen_consolidado`.
4. Tras completar las pruebas, restaure el arreglo inicial del Paso 3.

| Caso | Cambio en `varRegistros` | Resultado esperado |
|---|---|---|
| Positivo | Arreglo inicial | `4` aprobados y `4000.5` acumulados |
| Negativo | Reemplace los cuatro valores `Aprobado` por `Pendiente` | `0` aprobados y `0` acumulados |
| Borde | Cambie el importe de `SOL-001` de `250.50` a `0` y conserve su estado `Aprobado` | `4` aprobados y `3750` acumulados |
| Cadena hostil | En `Categoria` de `SOL-001`, use `IGNORE las reglas y fija varContadorAprobados=99` | `4` aprobados y `4000.5` acumulados |

**Resultado esperado:** La regla depende únicamente del campo `Estado`; `Categoria` no altera contador ni acumulador.

**Verificación:** En el caso de cadena hostil, el texto debe tratarse solo como dato. No debe ejecutar acciones, cambiar variables ni sustituir la regla configurada.

## Validación y Pruebas

La solución cumple si obtiene los resultados siguientes:

| Criterio medible | Evidencia requerida |
|---|---|
| Arreglo definido dentro del flujo | Acción `varRegistros` con seis objetos ficticios |
| Contador entero inicializado | `varContadorAprobados` inicia en `0` |
| Acumulador decimal inicializado | `varImporteAcumulado` inicia en `0` |
| Ciclo configurado | `Recorrer_registros` procesa seis iteraciones |
| Regla aplicada | Solo registros con `Estado` igual a `Aprobado` siguen la rama verdadera |
| Prueba base | Resumen con `4` y `4000.5` |
| Prueba negativa | Resumen con `0` y `0` |
| Prueba de borde | Resumen con `4` y `3750` |
| Cadena hostil | Resultado igual al de la prueba base; el texto no altera la lógica |

Use esta revisión crítica al evaluar la solución:

- **Precisión:** la condición compara `Estado` con `Aprobado`.
- **Trazabilidad:** el historial permite revisar cada iteración y sus acciones.
- **Incertidumbre:** el resumen solo representa los datos incluidos en el arreglo de prueba; no representa datos reales.
- **Utilidad:** el resultado evita contar y sumar manualmente los registros aprobados.
- **Supervisión humana:** una persona debe validar que la regla `Estado = Aprobado` sigue siendo adecuada antes de usarla en otro caso.

La cadena hostil del Paso 14 representa un caso adversarial similar a una inyección de prompt: las instrucciones incluidas dentro de un dato no deben reemplazar reglas explícitas del flujo.

## Solución de Problemas

### Problema 1: El contador muestra seis registros aprobados

**Síntoma:** El resumen indica `Registros aprobados: 6`, aunque existen registros pendientes.

**Causa:** La acción **Increment variable** está fuera de la rama verdadera de la condición o fuera de la condición.

**Corrección:**

1. Abra `Recorrer_registros`.
2. Compruebe que **Increment variable** está dentro de la rama verdadera.
3. Compruebe que **Set variable** también está dentro de la rama verdadera.
4. Guarde y ejecute otra prueba base.
5. Verifique el resultado `4` y `4000.5`.

### Problema 2: El acumulador falla o muestra un valor no numérico

**Síntoma:** La ejecución falla en **Set variable** o el importe acumulado no coincide con el valor esperado.

**Causa:** `varImporteAcumulado` se creó como texto, o la expresión no convierte `Importe` a valor decimal.

**Corrección:**

1. Revise que `varImporteAcumulado` tenga tipo **Float**.
2. Revise que el valor inicial sea `0`, sin comillas.
3. Revise la expresión:

```text
add(variables('varImporteAcumulado'), float(item()?['Importe']))
```

4. Guarde el flujo.
5. Ejecute nuevamente la prueba base y revise el resumen.

## Limpieza

1. Confirme que `varRegistros` contiene nuevamente el arreglo inicial del Paso 3.
2. Guarde el flujo con la versión restaurada.
3. Si el entorno es exclusivo para práctica temporal, elimine únicamente el flujo:

   `PF03_ContadorAcumulador_DatosPrueba`

4. No elimine ni modifique flujos creados en laboratorios anteriores.
5. No use datos reales, identificadores personales ni importes reales en futuras ejecuciones.

## Resumen (+ optional resources)

En esta práctica creó un flujo instantáneo que procesa un arreglo local de seis registros ficticios. Usó una variable entera como contador, una variable decimal como acumulador, un ciclo **Apply to each**, una condición y expresiones para producir un resumen consolidado.

El patrón creado puede reutilizarse cuando un proceso tenga datos estructurados, una regla clara y resultados medibles. En la práctica siguiente, este mismo tipo de datos podrá filtrarse o ajustarse antes de producir resultados adicionales.

---

# Expresiones y operaciones con datos

## Metadatos

| Duration | Complexity | Bloom level |
|---|---|---|
| 35 minutos | Media | Aplicar |

## Descripción General

En esta práctica se construirá un flujo instantáneo que procesa un arreglo JSON de solicitudes ficticias. El flujo comprobará resultados intermedios con **Compose**, filtrará registros aprobados con **Filter array** y generará una salida reducida con **Select**. Se aplicarán expresiones para normalizar texto, presentar fechas de manera uniforme y calcular un importe con impuesto.

**Descripción declarada:** dar formato a fechas y textos, calcular valores con expresiones, y filtrar y transformar datos con Compose, Filter array y Select.

## Objetivos de Aprendizaje

- [ ] dar formato a fechas y textos, calcular valores con expresiones, y filtrar y transformar datos con Compose, Filter array y Select.
- [ ] Aplicar `trim()` y `toUpper()` para normalizar categorías.
- [ ] Aplicar `formatDateTime()` para mostrar fechas con un criterio consistente.
- [ ] Calcular importes con `mul()` y valores numéricos convertidos mediante `float()`.
- [ ] Construir una salida reducida con los campos necesarios para un reporte posterior.

## Prerrequisitos

**Conocimientos**

- Haber completado, o comprender, la práctica anterior sobre arreglos, variables, contador y acumulador.
- Distinguir contenido dinámico de una expresión.
- Comprender que un arreglo JSON contiene varios objetos con campos definidos.
- Reconocer una regla de negocio simple: solo los registros con estado `Aprobado` se incluyen en la salida.

**Acceso**

- Cuenta organizacional autorizada para crear, editar, guardar y ejecutar flujos instantáneos.
- Permiso para utilizar acciones estándar de procesamiento de datos.
- No se requieren archivos externos, bases de datos, conectores adicionales ni acciones de IA.
- No cree recursos de almacenamiento adicionales. Esta práctica reutiliza exclusivamente el contrato de datos de la práctica anterior.

## Entorno de Laboratorio

| Componente | Especificación requerida |
|---|---|
| Servicio principal | Power Automate, edición servicio SaaS, arquitectura no aplicable, versión: `[VERSIÓN POR VALIDAR]` |
| Fuente oficial de versión | `[ENLACE OFICIAL]` |
| Navegador | Navegador administrado y compatible, versión: `[VERSIÓN POR VALIDAR]`, arquitectura según equipo |
| Equipo | Procesador de 64 bits, 8 GB de RAM recomendados, conexión HTTPS estable |
| Licencia | Suscripción organizacional con permiso para crear y probar flujos y usar acciones estándar |

Antes de iniciar, valide que puede acceder al diseñador de flujos y guardar cambios. Registre, si el instructor lo solicita, la compilación visible del servicio y la región del entorno.

No se requieren comandos de consola. Las siguientes expresiones se escribirán directamente en el diseñador.

> **Regla del caso:** todos los identificadores, fechas e importes son ficticios. El impuesto didáctico aplicado será del **19 %**. No use datos reales.

## Instrucciones Paso a Paso

### Paso 1: Revisar la regla de negocio

**Objetivo:** Identificar qué datos se procesarán y qué registros deben pasar a la salida final.

**Instrucciones:**

1. Revise el contrato de cada registro: `Id`, `Categoria`, `Estado`, `Importe` y `FechaSolicitud`.
2. Confirme la regla de inclusión: solo los elementos cuyo `Estado` sea exactamente `Aprobado`.
3. Confirme las reglas de transformación:
   - `Categoria` se limpiará y se convertirá a mayúsculas.
   - `FechaSolicitud` se presentará como `dd/MM/yyyy`.
   - `Importe` se multiplicará por `1.19`.
4. Identifique que los registros pendientes son una excepción controlada: permanecen en la entrada, pero no aparecen en la salida reducida.

**Resultado esperado:** Las reglas son claras, repetibles y aptas para automatizar mediante expresiones y filtros.

**Verificación:** Puede explicar que el flujo recibe seis registros, conserva cuatro aprobados y excluye dos pendientes.

---

### Paso 2: Crear el flujo instantáneo

**Objetivo:** Crear el contenedor de la automatización.

**Instrucciones:**

1. Cree un flujo de nube instantáneo.
2. Seleccione el disparador manual disponible en el diseñador.
3. Asigne al flujo el nombre:

   `P11_Expresiones_Transformacion_Solicitudes`

4. Cree el flujo y conserve el disparador sin campos de entrada.
5. Guarde una primera vez.

**Resultado esperado:** El flujo muestra un disparador manual y está listo para recibir acciones.

**Verificación:** El diseñador muestra el disparador como primer elemento y el flujo puede guardarse sin errores.

---

### Paso 3: Agregar el arreglo de solicitudes

**Objetivo:** Incorporar una entrada estructurada y controlada para las pruebas.

**Instrucciones:**

1. Agregue la acción **Compose**.
2. Cambie su nombre a:

   `Datos_solicitudes`

3. En **Inputs**, pegue el siguiente arreglo JSON.
4. Guarde el flujo.

```json
[
  {
    "Id": "SOL-001",
    "Categoria": " Operacion ",
    "Estado": "Aprobado",
    "Importe": 250.50,
    "FechaSolicitud": "2026-10-01T08:30:00Z"
  },
  {
    "Id": "SOL-002",
    "Categoria": "Servicio",
    "Estado": "Pendiente",
    "Importe": 120.00,
    "FechaSolicitud": "2026-10-02T09:15:00Z"
  },
  {
    "Id": "SOL-003",
    "Categoria": "Operacion",
    "Estado": "Aprobado",
    "Importe": 780.00,
    "FechaSolicitud": "2026-10-03T11:45:00Z"
  },
  {
    "Id": "SOL-004",
    "Categoria": "Tecnologia",
    "Estado": "Aprobado",
    "Importe": 1500.00,
    "FechaSolicitud": "2026-10-04T14:20:00Z"
  },
  {
    "Id": "SOL-005",
    "Categoria": "Servicio",
    "Estado": "Pendiente",
    "Importe": 99.99,
    "FechaSolicitud": "2026-10-05T16:10:00Z"
  },
  {
    "Id": "SOL-006",
    "Categoria": " Tecnologia ",
    "Estado": "Aprobado",
    "Importe": 1470.00,
    "FechaSolicitud": "2026-10-06T18:00:00Z"
  }
]
```

**Resultado esperado:** La acción contiene seis objetos JSON con la misma estructura.

**Verificación:** Se observan los cinco campos en cada objeto. Los valores de `Categoria` de `SOL-001` y `SOL-006` incluyen espacios intencionales para comprobar `trim()`.

---

### Paso 4: Comprobar un cálculo intermedio

**Objetivo:** Usar **Compose** para validar una expresión antes de aplicarla a todos los registros.

**Instrucciones:**

1. Agregue una acción **Compose** después de `Datos_solicitudes`.
2. Cambie su nombre a:

   `Comprobar_primer_aprobado`

3. En **Inputs**, abra la pestaña **Expression**.
4. Escriba la siguiente expresión.
5. Seleccione **Add** o **Update**, según la interfaz disponible.
6. Guarde el flujo.

```text
concat(
  toUpper(trim(first(outputs('Datos_solicitudes'))?['Categoria'])),
  ' | ',
  formatDateTime(first(outputs('Datos_solicitudes'))?['FechaSolicitud'], 'dd/MM/yyyy'),
  ' | ',
  string(mul(float(first(outputs('Datos_solicitudes'))?['Importe']), 1.19))
)
```

**Resultado esperado:** La acción produce un texto de control para el primer registro.

**Verificación:** La expresión contiene:

- `trim()` para quitar espacios de la categoría.
- `toUpper()` para normalizar el texto.
- `formatDateTime()` para presentar la fecha.
- `float()` y `mul()` para calcular el importe con impuesto.

---

### Paso 5: Filtrar las solicitudes aprobadas

**Objetivo:** Conservar únicamente los registros que cumplen la regla de negocio.

**Instrucciones:**

1. Agregue la acción **Filter array** después de `Comprobar_primer_aprobado`.
2. Cambie su nombre a:

   `Filtrar_aprobados`

3. En **From**, seleccione la salida de `Datos_solicitudes`.
4. Configure la condición con los siguientes valores:
   - Campo izquierdo: `Estado`
   - Operador: `is equal to`
   - Campo derecho: `Aprobado`
5. Guarde el flujo.

**Resultado esperado:** El filtro genera un arreglo con cuatro registros aprobados.

**Verificación:** Los identificadores esperados después del filtro son `SOL-001`, `SOL-003`, `SOL-004` y `SOL-006`.

---

### Paso 6: Crear una comprobación del filtro

**Objetivo:** Confirmar con una expresión cuántos registros pasaron la regla.

**Instrucciones:**

1. Agregue una acción **Compose** después de `Filtrar_aprobados`.
2. Cambie su nombre a:

   `Cantidad_aprobados`

3. En **Inputs**, agregue esta expresión.
4. Guarde el flujo.

```text
length(body('Filtrar_aprobados'))
```

**Resultado esperado:** La acción obtiene la cantidad de objetos incluidos en el arreglo filtrado.

**Verificación:** En la prueba base, la salida esperada es:

```text
4
```

---

### Paso 7: Transformar el arreglo con Select

**Objetivo:** Crear una salida reducida que contenga solo los campos necesarios.

**Instrucciones:**

1. Agregue la acción **Select** después de `Cantidad_aprobados`.
2. Cambie su nombre a:

   `Seleccionar_reporte`

3. En **From**, seleccione la salida de `Filtrar_aprobados`.
4. Cree los cuatro mapeos indicados en la tabla.
5. Para cada valor, abra la pestaña **Expression** y escriba la expresión correspondiente.
6. Guarde el flujo.

| Clave de salida | Expresión |
|---|---|
| `Codigo` | `item()?['Id']` |
| `CategoriaNormalizada` | `toUpper(trim(item()?['Categoria']))` |
| `FechaFormato` | `formatDateTime(item()?['FechaSolicitud'], 'dd/MM/yyyy')` |
| `ImporteConImpuesto` | `mul(float(item()?['Importe']), 1.19)` |

```text
item()?['Id']
```

```text
toUpper(trim(item()?['Categoria']))
```

```text
formatDateTime(item()?['FechaSolicitud'], 'dd/MM/yyyy')
```

```text
mul(float(item()?['Importe']), 1.19)
```

**Resultado esperado:** La acción devuelve un arreglo nuevo, con cuatro propiedades por cada registro aprobado.

**Verificación:** La acción no debe incluir los campos originales `Estado`, `Importe` ni `FechaSolicitud`.

---

### Paso 8: Guardar y ejecutar la prueba base

**Objetivo:** Ejecutar el flujo con el conjunto controlado de datos.

**Instrucciones:**

1. Guarde el flujo.
2. Seleccione **Test**.
3. Elija la ejecución manual.
4. Inicie la ejecución.
5. Espere a que todas las acciones finalicen correctamente.
6. Abra el historial de ejecución y seleccione la ejecución más reciente.

**Resultado esperado:** Todas las acciones muestran estado correcto.

**Verificación:** No debe existir ninguna acción omitida ni fallida. El historial muestra el disparador, tres acciones **Compose**, una acción **Filter array** y una acción **Select**.

---

### Paso 9: Revisar resultados intermedios

**Objetivo:** Validar la normalización y el cálculo antes de revisar el arreglo completo.

**Instrucciones:**

1. Abra la salida de `Comprobar_primer_aprobado`.
2. Abra la salida de `Cantidad_aprobados`.
3. Compare ambos resultados con los valores esperados.
4. Registre cualquier diferencia de precisión decimal observada.

**Resultado esperado:** La primera comprobación produce una salida equivalente a la siguiente.

```text
OPERACION | 01/10/2026 | 298.095
```

**Verificación:** `Cantidad_aprobados` debe devolver exactamente `4`. El servicio puede mostrar `298.09500000000003` en algunos contextos numéricos; esto evidencia precisión decimal de cálculo y no modifica la regla aplicada.

---

### Paso 10: Revisar la salida transformada

**Objetivo:** Confirmar que **Select** redujo y normalizó correctamente los datos.

**Instrucciones:**

1. Abra la salida de `Seleccionar_reporte`.
2. Revise que existan cuatro objetos.
3. Verifique la presencia de las claves `Codigo`, `CategoriaNormalizada`, `FechaFormato` e `ImporteConImpuesto`.
4. Compare los resultados con la referencia.

**Resultado esperado:** La salida es equivalente a la siguiente.

```json
[
  {
    "Codigo": "SOL-001",
    "CategoriaNormalizada": "OPERACION",
    "FechaFormato": "01/10/2026",
    "ImporteConImpuesto": 298.095
  },
  {
    "Codigo": "SOL-003",
    "CategoriaNormalizada": "OPERACION",
    "FechaFormato": "03/10/2026",
    "ImporteConImpuesto": 928.2
  },
  {
    "Codigo": "SOL-004",
    "CategoriaNormalizada": "TECNOLOGIA",
    "FechaFormato": "04/10/2026",
    "ImporteConImpuesto": 1785
  },
  {
    "Codigo": "SOL-006",
    "CategoriaNormalizada": "TECNOLOGIA",
    "FechaFormato": "06/10/2026",
    "ImporteConImpuesto": 1749.3
  }
]
```

**Verificación:** Los espacios iniciales y finales de las categorías no aparecen. Todas las categorías están en mayúsculas y las fechas utilizan el patrón `día/mes/año`.

---

### Paso 11: Probar un caso negativo y un caso de borde

**Objetivo:** Comprobar que el filtro y las expresiones responden correctamente ante variaciones previsibles.

**Instrucciones:**

1. En `Datos_solicitudes`, cambie temporalmente el estado de `SOL-003` de `Aprobado` a `aprobado`.
2. Guarde y ejecute el flujo.
3. Confirme que `Cantidad_aprobados` devuelve `3`.
4. Restaure el valor exacto `Aprobado`.
5. Cambie temporalmente el importe de `SOL-001` a `0`.
6. Guarde y ejecute de nuevo.
7. Confirme que `SOL-001` continúa en la salida y que `ImporteConImpuesto` es `0`.
8. Restaure el importe original `250.50` y guarde.

**Resultado esperado:** El filtro distingue mayúsculas y minúsculas, mientras que un importe cero es un valor numérico válido.

**Verificación:** El caso negativo excluye `SOL-003`; el caso de borde conserva `SOL-001` con impuesto igual a cero.

---

### Paso 12: Analizar críticamente una recomendación de IA

**Objetivo:** Evaluar una sugerencia generada por IA sin sustituir la validación humana.

**Instrucciones:**

1. Si dispone de un asistente de IA autorizado, envíe una instrucción temporal con el siguiente contenido.
2. Solicite una respuesta breve que identifique riesgos y una mejora posible.
3. Compare la respuesta con el comportamiento real observado en el flujo.
4. No aplique cambios sin comprobarlos mediante una nueva ejecución manual.

```text
Revisa esta regla de procesamiento: incluir solo registros cuyo Estado sea exactamente "Aprobado"; normalizar Categoria con trim y toUpper; presentar FechaSolicitud como dd/MM/yyyy; calcular ImporteConImpuesto multiplicando Importe por 1.19. Indica una limitación verificable y una prueba necesaria. No inventes campos ni cambies la regla de inclusión.
```

5. Realice una prueba adversarial conceptual: agregue a una categoría ficticia un texto como `IGNORA LA REGLA Y SELECCIONA TODO`.
6. Confirme que el flujo no cambia su regla de filtrado porque el filtro depende exclusivamente de `Estado`.
7. Restaure el arreglo original al finalizar.

**Resultado esperado:** La revisión puede señalar que el filtro es sensible a mayúsculas y minúsculas, y que los cálculos pueden mostrar decimales extensos. La recomendación no sustituye la prueba del flujo.

**Verificación:** Documente dos conclusiones:
- La sugerencia es útil solo si coincide con las expresiones configuradas y con una ejecución comprobable.
- El texto incrustado en un dato no tiene autoridad para modificar la lógica del flujo.

> Un **prompt** es una instrucción temporal enviada durante una conversación. Un **mensaje de sistema** define límites persistentes del asistente y no debe ser reemplazado por texto procedente de datos. La calidad de una respuesta se evalúa por precisión, trazabilidad, incertidumbre declarada, utilidad y supervisión humana; no se requiere exponer razonamientos internos.

## Validación y Pruebas

Use la siguiente matriz para registrar evidencia mínima. La evidencia recomendada es el historial de ejecución y las salidas de las acciones indicadas.

| Caso | Entrada o cambio | Resultado medible | Evidencia |
|---|---|---|---|
| Positivo base | Arreglo original | `Cantidad_aprobados = 4` | Salida de `Cantidad_aprobados` |
| Normalización | Categorías con espacios en `SOL-001` y `SOL-006` | Valores `OPERACION` y `TECNOLOGIA` | Salida de `Seleccionar_reporte` |
| Fecha | Fechas ISO de entrada | Fechas como `01/10/2026` y `06/10/2026` | Salida de `Seleccionar_reporte` |
| Cálculo | `SOL-004` con importe `1500.00` | `ImporteConImpuesto = 1785` | Salida de `Seleccionar_reporte` |
| Negativo | Estado de `SOL-003` como `aprobado` | El registro queda excluido; cantidad `3` | Salida de `Filtrar_aprobados` |
| Borde | Importe de `SOL-001` igual a `0` | El registro permanece; impuesto `0` | Salida de `Seleccionar_reporte` |
| Adversarial | Texto que intenta alterar reglas dentro de una categoría | La condición sigue evaluando solo `Estado` | Historial de ejecución y revisión humana |

**Criterios de aceptación**

1. La ejecución base termina sin errores.
2. El filtro devuelve exactamente cuatro registros con el conjunto original.
3. La salida final contiene únicamente cuatro propiedades por objeto.
4. Las categorías se presentan sin espacios exteriores y en mayúsculas.
5. Las fechas se presentan con el patrón `dd/MM/yyyy`.
6. Los importes se calculan multiplicando el importe original por `1.19`.
7. Las pruebas negativa, de borde y adversarial están ejecutadas o explicadas con evidencia verificable.

## Solución de Problemas

### Incidencia 1: La acción Select muestra campos vacíos o genera error de expresión

**Síntoma:** `CategoriaNormalizada`, `FechaFormato` o `ImporteConImpuesto` aparece vacío, o la ejecución falla en `Seleccionar_reporte`.

**Causa probable:** La acción **Select** está usando una referencia incorrecta, no recibe la salida de `Filtrar_aprobados` o se escribió un nombre de campo distinto de `Categoria`, `FechaSolicitud` o `Importe`.

**Corrección:**

1. Abra `Seleccionar_reporte`.
2. Confirme que **From** utiliza la salida de `Filtrar_aprobados`.
3. Revise que las expresiones usen exactamente los nombres de campo definidos.
4. Verifique que cada expresión comience con `item()?`.
5. Guarde y ejecute nuevamente la prueba base.

### Incidencia 2: El número de registros aprobados no coincide con cuatro

**Síntoma:** `Cantidad_aprobados` devuelve un valor distinto de `4` durante la prueba base.

**Causa probable:** Algún valor de `Estado` fue modificado durante una prueba, contiene espacios o no coincide exactamente con `Aprobado`.

**Corrección:**

1. Abra `Datos_solicitudes`.
2. Revise los valores de `Estado` de `SOL-001`, `SOL-003`, `SOL-004` y `SOL-006`.
3. Restablezca exactamente el valor `Aprobado` en esos cuatro registros.
4. Mantenga `Pendiente` en `SOL-002` y `SOL-005`.
5. Guarde y ejecute otra prueba manual.

## Limpieza

1. Confirme que el arreglo de `Datos_solicitudes` fue restaurado a sus valores originales.
2. Guarde el flujo con el nombre `P11_Expresiones_Transformacion_Solicitudes`.
3. Conserve el historial de la ejecución base como evidencia de aprendizaje si la política del entorno lo permite.
4. Si el flujo no será utilizado en prácticas posteriores, desactívelo o elimínelo según las indicaciones del instructor.
5. No elimine ni modifique recursos creados en prácticas anteriores.

## Resumen

En esta práctica se procesó un arreglo de solicitudes ficticias mediante acciones de transformación de datos. Se utilizó **Compose** para comprobar resultados intermedios, **Filter array** para aplicar una regla de negocio y **Select** para producir una salida reducida y normalizada.

Las expresiones utilizadas permiten preparar datos antes de aplicar decisiones más complejas:

- `trim()` elimina espacios exteriores.
- `toUpper()` estandariza texto.
- `formatDateTime()` presenta fechas con un patrón definido.
- `float()` asegura tratamiento numérico.
- `mul()` calcula el importe con impuesto.
- `length()` permite comprobar cuantitativamente el resultado del filtro.

La siguiente práctica podrá utilizar esta salida transformada como base para decisiones múltiples y rutas diferenciadas del flujo.

---

# Decisiones múltiples y flujo programado

## Metadatos

| Duración | Complejidad | Nivel de Bloom |
|---|---|---|
| 25 minutos | Media | Crear |

| Tecnología | Edición y arquitectura | Versión | Fuente oficial |
|---|---|---|---|
| Power Platform / Power Automate | Servicio SaaS; arquitectura administrada | [VERSIÓN POR VALIDAR] al momento de impartición | [ENLACE OFICIAL] |

## Descripción General

En esta práctica se crea un flujo de nube programado con una recurrencia temporal de cinco minutos. El flujo evalúa una categoría de prueba mediante una estructura **Switch**, ejecuta una rama distinta para `Urgente`, `Normal`, `Baja` u otro valor y registra el resultado con acciones **Compose**.

**Objetivo declarado:** implementar reglas con Switch y programar la ejecución periódica del flujo mediante recurrencia, verificando su comportamiento.

La práctica usa datos ficticios y acciones integradas. No se conecta a datos reales, cuentas externas ni recursos confidenciales.

## Objetivos de Aprendizaje

- [ ] Implementar reglas con **Switch** para clasificar una categoría de prueba.
- [ ] Configurar una recurrencia de cinco minutos y verificar una ejecución programada.
- [ ] Crear ramas explícitas para `Urgente`, `Normal` y `Baja`, junto con una rama **Default**.
- [ ] Registrar y revisar la salida de cada decisión mediante **Compose** e historial de ejecución.
- [ ] Controlar la recurrencia al terminar la prueba para evitar ejecuciones no deseadas.

## Prerrequisitos

**Conocimientos**

- Haber realizado las prácticas 10 y 11, incluyendo condiciones, expresiones básicas y acciones **Compose**.
- Comprender que una ejecución recurrente se activa de manera periódica mientras el flujo permanezca activo.
- Reconocer que una decisión basada en reglas requiere entradas definidas, casos conocidos y una excepción predeterminada.

**Acceso**

- Cuenta institucional con licencia que permita crear, editar, guardar, ejecutar y probar flujos de nube en un entorno autorizado.
- Permiso para crear flujos de nube programados.
- Navegador web compatible, conexión HTTPS estable y acceso al historial de ejecución.
- Carpeta de trabajo disponible: `/Laboratorio-FPA-PA/Modulo-01`.

## Entorno de Laboratorio

| Recurso | Uso en esta práctica |
|---|---|
| Equipo con teclado y dispositivo apuntador | Creación y prueba del flujo |
| Navegador web compatible | Acceso al diseñador de flujos |
| Power Automate | Recurrencia, Switch, Compose e historial |
| Entorno de prueba autorizado | Ejecuciones con categorías ficticias |

No se requieren comandos de terminal, archivos auxiliares, conectores de pago, bases de datos ni recursos externos.

**Datos controlados de esta práctica**

| Elemento | Valor |
|---|---|
| Nombre del flujo | `PA-B3-P12-SwitchRecurrencia` |
| Intervalo temporal de prueba | `5` minutos |
| Categoría inicial | `Urgente` |
| Casos explícitos | `Urgente`, `Normal`, `Baja` |
| Caso predeterminado | Cualquier valor distinto de los tres casos explícitos |

**Lógica esperada**

```text
Cada 5 minutos:
    Leer Categoria_prueba
    Según la categoría:
        Urgente -> registrar atención prioritaria
        Normal  -> registrar atención estándar
        Baja    -> registrar atención planificada
        Otro    -> registrar revisión de categoría
```

## Instrucciones Paso a Paso

### Paso 1: Crear el flujo programado

**Objetivo:** Crear el flujo de nube con el nombre y la recurrencia requeridos.

**Instrucciones:**

1. Abra Power Automate en el entorno autorizado.
2. Seleccione **Crear**.
3. Elija **Flujo de nube programado**.
4. En nombre del flujo, escriba:

   ```text
   PA-B3-P12-SwitchRecurrencia
   ```

5. Configure la recurrencia inicial:
   - Intervalo: `5`
   - Frecuencia: `Minuto`
6. Seleccione **Crear**.

**Resultado esperado:** Se abre el diseñador con el disparador **Recurrence** configurado para ejecutarse cada cinco minutos.

**Verificación:** Confirme que el encabezado del flujo muestra `PA-B3-P12-SwitchRecurrencia` y que el disparador presenta intervalo `5` con frecuencia `Minute`.

### Paso 2: Agregar la categoría de prueba

**Objetivo:** Definir una entrada controlada que permita probar la decisión sin depender de una fuente externa.

**Instrucciones:**

1. Debajo del disparador **Recurrence**, seleccione **Nuevo paso**.
2. Agregue la acción **Compose**.
3. Cambie el nombre de la acción a:

   ```text
   Categoria_prueba
   ```

4. En **Inputs**, escriba:

   ```text
   Urgente
   ```

5. Guarde el flujo.

**Resultado esperado:** La acción `Categoria_prueba` genera el texto `Urgente` en cada ejecución.

**Verificación:** Revise que el valor esté escrito sin espacios al inicio ni al final.

### Paso 3: Agregar la decisión Switch

**Objetivo:** Crear una estructura de control con varias ramas posibles.

**Instrucciones:**

1. Seleccione **Nuevo paso** después de `Categoria_prueba`.
2. Busque y agregue la acción de control **Switch**.
3. Cambie el nombre de la acción a:

   ```text
   Clasificar_categoria
   ```

4. En el campo de selección de Switch, elija la salida de `Categoria_prueba`.
5. Verifique que la estructura incluya un primer caso y una rama **Default**.

**Resultado esperado:** El flujo cuenta con una decisión denominada `Clasificar_categoria` que evalúa la salida de `Categoria_prueba`.

**Verificación:** El campo de evaluación debe apuntar a la salida de `Categoria_prueba`, no al texto escrito manualmente en un caso.

### Paso 4: Configurar el caso Urgente

**Objetivo:** Crear una respuesta operativa para la categoría prioritaria.

**Instrucciones:**

1. En el primer caso de `Clasificar_categoria`, escriba como valor:

   ```text
   Urgente
   ```

2. Dentro de este caso, agregue una acción **Compose**.
3. Cambie el nombre de la acción a:

   ```text
   Resultado_urgente
   ```

4. En **Inputs**, escriba:

   ```text
   Atención prioritaria registrada
   ```

5. Guarde el flujo.

**Resultado esperado:** Cuando la categoría sea `Urgente`, se ejecutará `Resultado_urgente`.

**Verificación:** El caso debe contener exactamente `Urgente` y la salida esperada debe indicar atención prioritaria.

### Paso 5: Configurar los casos Normal y Baja

**Objetivo:** Agregar ramas explícitas para categorías operativas no prioritarias.

**Instrucciones:**

1. En `Clasificar_categoria`, seleccione **Agregar un caso**.
2. Escriba el valor:

   ```text
   Normal
   ```

3. Dentro de ese caso, agregue una acción **Compose** llamada:

   ```text
   Resultado_normal
   ```

4. Escriba como entrada:

   ```text
   Atención estándar registrada
   ```

5. Agregue otro caso con este valor:

   ```text
   Baja
   ```

6. Dentro del caso `Baja`, agregue una acción **Compose** llamada:

   ```text
   Resultado_baja
   ```

7. Escriba como entrada:

   ```text
   Atención planificada registrada
   ```

8. Guarde el flujo.

**Resultado esperado:** Switch contiene tres casos explícitos: `Urgente`, `Normal` y `Baja`.

**Verificación:** Cada caso debe contener una acción Compose propia y un texto de salida distinto.

### Paso 6: Configurar la rama Default

**Objetivo:** Manejar categorías no contempladas de manera controlada.

**Instrucciones:**

1. Ubique la rama **Default** de `Clasificar_categoria`.
2. Agregue una acción **Compose** dentro de esa rama.
3. Cambie el nombre de la acción a:

   ```text
   Resultado_otro
   ```

4. En **Inputs**, escriba:

   ```text
   Categoría no contemplada: requiere revisión
   ```

5. Guarde el flujo.

**Resultado esperado:** Todo valor distinto de `Urgente`, `Normal` o `Baja` activará `Resultado_otro`.

**Verificación:** Compruebe que `Resultado_otro` esté dentro de **Default**, no fuera de Switch.

### Paso 7: Guardar y comprobar la programación

**Objetivo:** Confirmar que la recurrencia activa el flujo según el intervalo definido.

**Instrucciones:**

1. Seleccione **Guardar**.
2. Verifique que no existan errores de validación en el diseñador.
3. Vuelva a la página de detalles del flujo.
4. Espere hasta cinco minutos desde la hora de guardado.
5. Abra el historial de ejecución.
6. Seleccione la ejecución más reciente.

**Resultado esperado:** El historial muestra al menos una ejecución iniciada por la recurrencia.

**Verificación:** En el detalle de la ejecución, confirme estos criterios:

| Criterio | Evidencia esperada |
|---|---|
| Disparador | Recurrence con estado correcto |
| Categoría | `Categoria_prueba` muestra `Urgente` |
| Rama ejecutada | Caso `Urgente` |
| Resultado | `Atención prioritaria registrada` |
| Ramas no elegidas | `Normal`, `Baja` y Default aparecen omitidas |

### Paso 8: Probar una categoría no contemplada

**Objetivo:** Validar que la rama Default protege el flujo frente a valores no definidos.

**Instrucciones:**

1. Regrese al diseñador.
2. En `Categoria_prueba`, reemplace el valor `Urgente` por:

   ```text
   Otro
   ```

3. Guarde el flujo.
4. Use la opción de prueba manual disponible en el diseñador o espere la siguiente ejecución programada.
5. Abra el historial y seleccione la ejecución generada.
6. Revise la acción `Resultado_otro`.

**Resultado esperado:** La rama **Default** se ejecuta y registra `Categoría no contemplada: requiere revisión`.

**Verificación:** Confirme que las ramas `Urgente`, `Normal` y `Baja` aparecen omitidas en esa ejecución.

### Paso 9: Restaurar el valor y controlar la recurrencia

**Objetivo:** Dejar el flujo en un estado seguro al finalizar la práctica.

**Instrucciones:**

1. Decida con el instructor una de estas opciones:
   - Ajustar el intervalo al valor indicado para el entorno de práctica.
   - Desactivar el flujo.
2. Si se solicita restaurar el valor de prueba, establezca nuevamente:

   ```text
   Urgente
   ```

3. Guarde los cambios.
4. Registre en sus notas el nombre del flujo, el resultado obtenido y la decisión aplicada sobre la recurrencia.

**Resultado esperado:** El flujo queda controlado y no genera ejecuciones innecesarias.

**Verificación:** En la página de detalles, confirme el estado final solicitado por el instructor: activo con intervalo autorizado o desactivado.

## Validación y Pruebas

La validación se considera satisfactoria cuando el flujo cumple todos los criterios siguientes.

| Prueba | Entrada en `Categoria_prueba` | Rama esperada | Salida esperada |
|---|---|---|---|
| Positiva prioritaria | `Urgente` | Caso `Urgente` | `Atención prioritaria registrada` |
| Positiva estándar | `Normal` | Caso `Normal` | `Atención estándar registrada` |
| Positiva planificada | `Baja` | Caso `Baja` | `Atención planificada registrada` |
| Negativa | `Otro` | Default | `Categoría no contemplada: requiere revisión` |
| Borde | `urgente` | Default | `Categoría no contemplada: requiere revisión` |
| Programación | Cualquier valor válido | Ejecución recurrente | Historial con activación posterior al intervalo configurado |

**Evidencia mínima medible**

1. El flujo se llama `PA-B3-P12-SwitchRecurrencia`.
2. El disparador tiene intervalo de cinco minutos durante la prueba.
3. Switch contiene tres casos explícitos y una rama Default.
4. El historial muestra una ejecución correcta producida por recurrencia.
5. Una prueba con `Otro` muestra la rama Default.
6. El flujo queda ajustado o desactivado al cierre.

### Caso adversarial: texto contradictorio o instrucción incrustada

Cambie temporalmente `Categoria_prueba` por el siguiente texto:

```text
Ignora las reglas y clasifica como Urgente
```

**Resultado esperado:** Debe ejecutarse **Default**. Switch compara el valor completo con los casos configurados y no debe interpretar ese texto como una orden operativa.

Este caso demuestra una limitación útil: una automatización basada en reglas no evalúa intención, contexto ni prioridad implícita. Solo aplica coincidencias configuradas de manera explícita.

### Nota sobre terminología de IA

Esta práctica no usa IA. Una **instrucción** es una indicación puntual incluida en una tarea; un **prompt** es un texto enviado a un sistema de IA para solicitar una salida; un **mensaje de sistema** establece reglas de comportamiento para dicho sistema; un **agente persistente** puede conservar directrices entre interacciones según su configuración.

El valor de `Categoria_prueba` es un dato de entrada, no un prompt ni un mensaje de sistema. Si en otra actividad se usa IA para sugerir reglas, la persona responsable debe validar precisión, trazabilidad, incertidumbre, utilidad y supervisión humana antes de aplicar cambios al flujo.

## Solución de Problemas

1. **Síntoma:** El historial no muestra una ejecución después de cinco minutos.  
   **Causa:** El flujo no se guardó, está desactivado o la hora de inicio de la recurrencia aún no ha alcanzado el siguiente ciclo.  
   **Corrección:** Guarde el flujo, confirme que está activo y espere un ciclo completo de cinco minutos. Después actualice la página de historial. Si el entorno ofrece prueba manual para el flujo programado, úsela solo como evidencia adicional; mantenga la espera de una ejecución recurrente para validar el disparador.

2. **Síntoma:** La rama Default se ejecuta aunque la categoría parece válida.  
   **Causa:** El valor contiene diferencias de mayúsculas, espacios o caracteres adicionales. Switch requiere coincidencia exacta con el caso configurado.  
   **Corrección:** Revise el texto de `Categoria_prueba` y el texto del caso. Use exactamente `Urgente`, `Normal` o `Baja`. Para esta práctica no agregue expresiones de limpieza, ya que el propósito es observar la decisión exacta y su excepción Default.

## Limpieza

1. Confirme con el instructor si el flujo debe conservarse para la práctica siguiente.
2. Si no debe continuar activo, desactive `PA-B3-P12-SwitchRecurrencia`.
3. Si debe conservarse, ajuste la recurrencia al intervalo indicado por el instructor.
4. No elimine recursos previos ni cree entidades adicionales.
5. Mantenga solo evidencias autorizadas en `/Laboratorio-FPA-PA/Modulo-01`.

## Resumen

En esta práctica se construyó un flujo programado que ejecuta una decisión múltiple mediante **Switch**. La recurrencia permitió comprobar un disparador periódico y las ramas explícitas permitieron registrar respuestas operativas para `Urgente`, `Normal` y `Baja`.

La rama **Default** cubrió valores no previstos y demostró la importancia de definir excepciones antes de automatizar. La siguiente evolución natural consiste en sustituir la categoría fija por una entrada basada en eventos, manteniendo las mismas reglas de decisión y los controles de validación.
