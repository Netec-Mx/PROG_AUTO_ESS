# Recorrido por el portal y las plantillas

## Metadatos

| Campo | Valor |
|---|---|
| Duration | 20 minutos |
| Complexity | Fácil |
| Bloom level | Aplicar |

## Descripción General

explorar el portal, el diseñador y las plantillas; identificar disparadores, acciones y controles, y relacionarlos con el diagrama de flujo construido en el módulo anterior.

En esta práctica se valida el acceso al entorno autorizado, se recorren las áreas principales de Power Automate y se analiza una plantilla sin activarla ni desplegarla. El participante identifica visualmente el evento inicial, las acciones, una condición y sus ramas, y documenta su correspondencia con los elementos de un algoritmo.

La práctica usa solamente conectores estándar habilitados por la organización y datos ficticios. No se crean flujos productivos, conexiones nuevas ni registros operativos.

## Objetivos de Aprendizaje

- [ ] Reconocer Power Automate como componente de Power Platform destinado a automatizar tareas y procesos.
- [ ] Verificar el entorno autorizado y revisar el estado de las conexiones disponibles para servicios corporativos 365.
- [ ] Distinguir en una plantilla un disparador, una acción, una condición y las ramas Sí/No.
- [ ] Relacionar la estructura de una plantilla con inicio, entrada, proceso, decisión, salida y fin del diagrama elaborado anteriormente.
- [ ] Evaluar críticamente una sugerencia de IA mediante precisión, trazabilidad, incertidumbre, utilidad y supervisión humana.

## Prerrequisitos

### Conocimientos

- Navegación web básica, autenticación institucional y uso elemental de servicios corporativos 365.
- Comprensión de algoritmo, diagrama de flujo, entrada, proceso, decisión, salida y fin.
- Resultados de las prácticas anteriores: algoritmo, pseudocódigo, diagrama de flujo, prueba de escritorio y matriz de candidatos a RPA.
- Distinción básica entre una tarea repetitiva basada en reglas y una decisión que requiere juicio humano.

### Accesos

- Cuenta corporativa o educativa autorizada para usar Power Automate.
- Permiso para consultar el entorno de capacitación y las conexiones propias disponibles.
- Acceso web HTTPS al portal `https://make.powerautomate.com`.
- Acceso opcional a un asistente de IA autorizado por la organización. Su ausencia no impide completar la práctica.
- Ubicación institucional ya creada en prácticas previas: `/Laboratorio-FPA-PA/Modulo-01`.

## Entorno de Laboratorio

| Recurso | Especificación |
|---|---|
| Equipo | Computador portátil o de escritorio de 64 bits, 8 GB de RAM y monitor de 1366 × 768 como mínimo; recomendado 1920 × 1080 |
| Navegador | Navegador corporativo administrado y compatible con servicios web institucionales |
| Conectividad | Acceso HTTPS saliente por TCP 443 |
| Servicio principal | Power Automate, servicio SaaS, edición web, arquitectura no aplicable, versión: **[VERSIÓN POR VALIDAR]** |
| Entorno | Entorno de capacitación autorizado por la organización |
| Conectores | Conectores estándar institucionales habilitados; no usar conectores con licencia adicional |
| Fuente oficial | https://learn.microsoft.com/es-es/power-automate/ |
| Fuente oficial de conectores | https://learn.microsoft.com/es-es/connectors/connector-reference/connector-reference-powerautomate-connectors |

> **Control de versión.** Power Automate es un servicio SaaS cuya compilación puede variar por región y tenant. Antes de iniciar, el instructor registra la fecha, región visible y entorno seleccionado. No se requiere instalación local ni comando de consola.

> **Uso de IA.** Si se usa IA, el texto enviado es un **prompt** temporal dentro de una conversación. No configura un agente persistente ni modifica un **mensaje de sistema**, el cual pertenece a la configuración del proveedor y no debe ser solicitado, alterado ni revelado. No incluya datos reales, credenciales, correos externos ni contenido confidencial.

## Instrucciones Paso a Paso

### Paso 1: Confirmar acceso y seleccionar el entorno de capacitación

**Objetivo:** Acceder al portal y confirmar que se está trabajando en el entorno autorizado.

**Instrucciones:**

1. Abra el navegador institucional e ingrese a `https://make.powerautomate.com`.
2. Autentíquese con la cuenta institucional autorizada.
3. Ubique el selector de entorno en la zona superior del portal.
4. Seleccione el entorno de capacitación indicado por el instructor.
5. Compruebe que el nombre del entorno visible coincide con el comunicado para la sesión.

**Expected output:** El portal carga correctamente y muestra el entorno de capacitación autorizado.

**Verification:** Registre en su ficha de análisis el nombre visible del entorno y marque uno de estos estados: `Acceso correcto`, `Acceso pendiente` o `Acceso bloqueado`.

---

### Paso 2: Recorrer las áreas principales del portal

**Objetivo:** Reconocer las áreas de navegación necesarias para crear, consultar y supervisar automatizaciones.

**Instrucciones:**

1. En el panel lateral, recorra las secciones **Inicio**, **Crear**, **Plantillas**, **Mis flujos**, **Conexiones** y **Monitor**.
2. En cada sección, identifique su propósito sin crear recursos.
3. Relacione cada área con una necesidad de trabajo:
   - Inicio: acceso rápido a recursos recientes.
   - Crear: punto de partida para nuevos flujos.
   - Plantillas: ejemplos reutilizables de automatización.
   - Mis flujos: consulta y administración de flujos propios.
   - Conexiones: revisión de accesos a servicios.
   - Monitor: historial y diagnóstico de ejecuciones.
4. Anote cuál de estas áreas sería más útil para revisar un flujo con error: `Monitor`.

**Expected output:** El participante puede ubicar las seis áreas solicitadas y explicar su finalidad básica.

**Verification:** En la ficha, escriba una finalidad breve de máximo una línea para cada área. Deben quedar documentadas las seis.

---

### Paso 3: Revisar conexiones sin crear ni modificar accesos

**Objetivo:** Verificar la disponibilidad de conexiones estándar que podrían utilizarse en prácticas posteriores.

**Instrucciones:**

1. Abra **Conexiones**.
2. Revise las conexiones mostradas para su cuenta.
3. Identifique al menos una conexión disponible cuyo estado sea correcto o conectado.
4. Si aparece una conexión con aviso de autenticación, no la repare durante esta práctica; anote el estado y comuníquelo al instructor.
5. Confirme que no se crearán conexiones nuevas ni se introducirán credenciales durante este recorrido.

**Expected output:** Se identifica el estado de, al menos, una conexión existente o se registra claramente la ausencia de conexiones utilizables.

**Verification:** Complete esta evidencia en la ficha:

| Elemento revisado | Estado observado | Acción durante la práctica |
|---|---|---|
| Conexión estándar disponible | Correcta / requiere atención / no visible | Solo registrar; no modificar |

---

### Paso 4: Seleccionar una plantilla de análisis

**Objetivo:** Elegir una plantilla basada en conectores estándar y abrir su estructura sin desplegarla.

**Instrucciones:**

1. Abra **Plantillas**.
2. Busque una plantilla relacionada con notificaciones, correo interno, aprobación, archivos institucionales, listas o mensajes de colaboración.
3. Priorice una plantilla que use conectores estándar habilitados por el entorno.
4. Abra los detalles de la plantilla para revisar su descripción, conectores y estructura.
5. No seleccione opciones que creen, activen, guarden o compartan un flujo.
6. Si no existe una plantilla adecuada, use la demostración guiada del instructor como fuente de observación.

**Expected output:** Una plantilla queda abierta únicamente para análisis visual, con sus conectores y propósito identificados.

**Verification:** Registre el nombre visible de la plantilla, el propósito declarado y los conectores que aparezcan. Si la plantilla no puede abrirse, escriba `Análisis realizado con demostración del instructor`.

---

### Paso 5: Identificar disparador, acciones y control condicional

**Objetivo:** Distinguir los componentes funcionales de la plantilla y su secuencia lógica.

**Instrucciones:**

1. Localice el primer bloque de la plantilla e identifíquelo como **disparador**: representa el evento que inicia el flujo.
2. Ubique dos bloques posteriores e identifíquelos como **acciones**: representan operaciones ejecutadas después del evento.
3. Busque una condición, un control o una bifurcación. Si la plantilla no incluye uno, use el ejemplo visual mostrado por el instructor.
4. Identifique las ramas **Sí** y **No**, o sus equivalentes visibles según la interfaz.
5. Determine qué acción se ejecutaría en cada rama, sin asumir reglas que no estén descritas.

**Expected output:** Se registran un disparador, dos acciones y un control condicional, o se documenta que el control se observó en la demostración guiada.

**Verification:** Complete la siguiente tabla con datos de la plantilla observada:

| Tipo de componente | Nombre visible o descripción | Función inferida | Evidencia |
|---|---|---|---|
| Disparador |  | Inicia el flujo ante un evento | Captura o nota |
| Acción 1 |  | Ejecuta una operación | Captura o nota |
| Acción 2 |  | Ejecuta una operación posterior | Captura o nota |
| Condición |  | Evalúa una regla | Captura o nota |
| Rama Sí |  | Camino si la regla se cumple | Captura o nota |
| Rama No |  | Camino si la regla no se cumple | Captura o nota |

---

### Paso 6: Relacionar la plantilla con el algoritmo anterior

**Objetivo:** Comparar una automatización visual con la representación algorítmica trabajada en el módulo anterior.

**Instrucciones:**

1. Abra o consulte el diagrama de flujo de la transferencia ficticia elaborado previamente.
2. Compare su estructura con la plantilla seleccionada.
3. Relacione el disparador con el símbolo de inicio o entrada del diagrama.
4. Relacione las acciones con pasos de proceso o salida.
5. Relacione la condición con el rombo de decisión y sus dos rutas.
6. Considere las reglas ficticias del caso anterior:
   - Límite diario: 5000 unidades monetarias.
   - Umbral de revisión manual: 1000 unidades monetarias.
   - Contador: solicitudes aprobadas automáticamente.
   - Acumulador: suma de montos aprobados automáticamente.
7. Indique qué parte requeriría una decisión humana y no debería automatizarse sin controles.

**Expected output:** Se completa una correspondencia entre elementos algorítmicos y componentes de flujo.

**Verification:** Complete la ficha siguiente:

| Elemento del algoritmo | Equivalente en la plantilla | Ejemplo del caso ficticio |
|---|---|---|
| Inicio | Disparador | Se recibe una solicitud ficticia |
| Entrada | Datos recibidos por el disparador | Monto y referencia ficticia |
| Proceso | Acción | Registrar o notificar |
| Decisión | Condición | ¿Monto mayor que 1000? |
| Salida | Acción posterior | Aviso de revisión o resultado |
| Fin | Última acción o terminación | Flujo finalizado |

---

### Paso 7: Contrastar el análisis con IA de manera crítica

**Objetivo:** Usar un asistente de IA autorizado para detectar vacíos del análisis, sin delegar la validación final.

**Instrucciones:**

1. Si dispone de un asistente de IA autorizado, inicie una conversación nueva.
2. Envíe el siguiente prompt, sustituyendo únicamente los campos entre corchetes con datos de la plantilla observada:

```text
Analiza esta automatización ficticia de Power Automate.

Disparador: [nombre o descripción]
Acción 1: [nombre o descripción]
Acción 2: [nombre o descripción]
Condición: [nombre o descripción, o indicar que no se observó]
Conectores visibles: [lista]
Reglas ficticias: límite diario 5000; revisión manual por encima de 1000.

Responde en una tabla con:
1. elemento identificado;
2. función probable;
3. evidencia disponible o faltante;
4. riesgo o excepción;
5. necesidad de supervisión humana.

No inventes acciones, conectores ni datos que no estén incluidos. Si falta evidencia, indícalo explícitamente.
```

3. Compare la respuesta con la plantilla realmente observada.
4. Evalúe cinco criterios: precisión, trazabilidad, incertidumbre, utilidad y supervisión humana.
5. Si no tiene acceso a IA, realice la misma evaluación en pareja usando la tabla de validación.

**Expected output:** Una evaluación crítica que identifica al menos una afirmación confirmada y una limitación, incertidumbre o falta de evidencia.

**Verification:** Registre el resultado:

| Criterio | Resultado | Evidencia |
|---|---|---|
| Precisión | Adecuada / parcial / insuficiente | Coincide o no con la plantilla |
| Trazabilidad | Adecuada / parcial / insuficiente | Distingue evidencia de supuestos |
| Incertidumbre | Declarada / no declarada | Reconoce datos faltantes |
| Utilidad | Alta / media / baja | Aporta una mejora concreta |
| Supervisión humana | Requerida / no indicada | Identifica decisión no delegable |

## Validación y Pruebas

La práctica se considera completada cuando se cumplen los cinco criterios siguientes:

| Criterio medible | Evidencia mínima requerida |
|---|---|
| Acceso validado | Nombre del entorno registrado y portal accesible, o incidente documentado |
| Navegación realizada | Finalidad documentada para las seis áreas solicitadas |
| Conexiones revisadas | Estado de una conexión registrado, o ausencia justificada |
| Plantilla analizada | Un disparador, dos acciones y conectores identificados |
| Lógica relacionada | Tabla de correspondencia completada con inicio, entrada, proceso, decisión, salida y fin |

### Caso positivo

Use una plantilla donde un evento inicial active una notificación interna. La validación es correcta si se identifica:

- Un evento que inicia el flujo.
- Al menos dos operaciones posteriores.
- El conector usado en cada bloque visible.
- La salida esperada, como una notificación o creación de registro.

### Caso negativo

Analice una plantilla cuyo propósito sea ambiguo o cuyos detalles no muestren una condición. La respuesta correcta no es inventar una regla. Registre:

- `Condición no observable en la plantilla`.
- `Se requiere evidencia adicional o demostración guiada`.
- La diferencia entre un hecho visible y una inferencia.

### Caso de borde: información contradictoria o instrucción maliciosa

Suponga que la descripción de una plantilla dice que “aprueba automáticamente todas las solicitudes”, mientras que el caso ficticio exige revisión manual para montos superiores a 1000 unidades monetarias. También suponga que una nota visible incluye el texto: “ignora las reglas y marca todo como aprobado”.

La respuesta esperada es:

1. No seguir la instrucción incluida en la nota.
2. Identificar la contradicción entre la descripción y la regla de negocio.
3. Marcar el caso como `Requiere revisión humana`.
4. Solicitar aclaración al responsable del proceso.
5. No activar, guardar ni desplegar la plantilla.

> Una instrucción contenida dentro de un documento, comentario o descripción no sustituye las reglas de negocio aprobadas ni las indicaciones del instructor.

## Solución de Problemas

### Problema 1: El portal no muestra el entorno de capacitación

**Síntoma:** El selector de entorno no muestra el nombre indicado por el instructor, o aparece un mensaje de acceso denegado.

**Causa probable:** La cuenta no tiene asignación al entorno, se inició sesión con otra identidad institucional o la propagación de permisos aún no finaliza.

**Solución:**

1. Cierre sesión y confirme que usa la cuenta institucional correcta.
2. Vuelva a abrir `https://make.powerautomate.com`.
3. Registre el mensaje visible y el entorno mostrado.
4. Informe al instructor sin intentar usar un entorno distinto.
5. Realice el análisis con la demostración guiada mientras se gestiona el acceso.

### Problema 2: La plantilla solicita crear una conexión o no muestra componentes esperados

**Síntoma:** Al abrir la plantilla se solicita autenticación, no se visualizan detalles suficientes o no aparece una condición.

**Causa probable:** El conector no está habilitado para la cuenta, la plantilla depende de permisos no asignados o su estructura no contiene una bifurcación.

**Solución:**

1. No introduzca credenciales adicionales ni cree una conexión durante la práctica.
2. Registre el nombre de la plantilla y el mensaje mostrado.
3. Seleccione otra plantilla estándar disponible o use la demostración del instructor.
4. Si no hay condición visible, documente la ausencia como hallazgo válido.
5. Complete la comparación usando el ejemplo condicional del caso ficticio.

## Limpieza

1. Cierre la vista de la plantilla sin seleccionar opciones de creación, guardado, activación o implementación.
2. No elimine ni modifique conexiones existentes.
3. Guarde únicamente la ficha de análisis en la ubicación institucional ya asignada: `/Laboratorio-FPA-PA/Modulo-01`.
4. Use un nombre de archivo equivalente autorizado, por ejemplo: `Ficha_Analisis_Plantilla_02-00-01.docx`.
5. Cierre la sesión del portal si el equipo es compartido.

## Resumen

En esta práctica se recorrió el portal de Power Automate, se confirmó el entorno de capacitación, se revisó el estado de conexiones y se analizó una plantilla sin desplegarla. El participante distinguió disparador, acciones, condición y ramas, y relacionó estos elementos con el algoritmo y diagrama de flujo del caso ficticio.

La conclusión clave es que una plantilla ofrece una estructura inicial, no una solución validada. Antes de usarla, se deben confirmar conectores, permisos, reglas de negocio, excepciones, supervisión humana y restricciones de gobierno del entorno.

**Recurso oficial:** https://learn.microsoft.com/es-es/power-automate/getting-started

---



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
