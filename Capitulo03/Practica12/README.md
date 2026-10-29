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


---

[Volver al capítulo](../README.md) · [Volver al inicio](../../README.md)
