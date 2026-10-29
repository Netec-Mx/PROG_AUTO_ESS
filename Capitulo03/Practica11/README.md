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



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
