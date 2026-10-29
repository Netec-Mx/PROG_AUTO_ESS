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



---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
