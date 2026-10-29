<p align="center">
  <img src="https://raw.githubusercontent.com/Netec-Mx/261029-PROG-AUTO-ESS/main/assets/LogoNetec.png" alt="NETEC" width="180" />
</p>

# Fundamentos de Programación, Automatización y Power Automate

Este curso desarrolla, desde cero y con un enfoque eminentemente práctico, las habilidades necesarias para automatizar tareas y flujos de trabajo con Microsoft Power Automate. Los participantes parten de los fundamentos de programación (algoritmos, pseudocódigo, diagramas de flujo, variables, condicionales, contadores y acumuladores) y de los principios de RPA para después trasladar esa lógica a Power Automate, apoyándose en la inteligencia artificial como asistente. El curso avanza de forma progresiva hasta un nivel intermedio: variables, condiciones, bucles, expresiones, conectores estándar de Microsoft 365, aprobaciones y manejo de errores, con énfasis en identificar qué procesos conviene automatizar y cómo hacerlo de forma estructurada, segura y responsable. Todas las prácticas se realizan con funcionalidades básicas (estándar), sin conectores Premium.

## Accesos rápidos

- [**Setup Guide del curso**](https://github.com/Netec-Mx/261029-PROG-AUTO-ESS/blob/main/SETUP_GUIDE.md)
- [Laboratorios por capítulo](#lista-de-laboratorios)

## Estructura

- `SETUP_GUIDE.md`: guía de instalación y preparación del entorno.
- `CapituloXX/README.md`: guía de laboratorio por capítulo.

## Lista de laboratorios

### Capítulo 1

- [De un problema a un algoritmo con apoyo de Copilot Chat](Capitulo01/README.md#de-un-problema-a-un-algoritmo-con-apoyo-de-copilot-chat)
  - Descripción: caso práctico de algoritmos con un proceso bancario ficticio: definir objetivo, entradas, salidas y restricciones, redactar los pasos de la solución y usar Microsoft 365 Copilot Chat (o un asistente de IA autorizado) para detectar vacíos y excepciones, validando críticamente sus sugerencias.
  - Duración estimada: 25 min
- [Pseudocódigo y diagrama de flujo con apoyo de Copilot Chat](Capitulo01/README.md#pseudocódigo-y-diagrama-de-flujo-con-apoyo-de-copilot-chat)
  - Descripción: transformar el algoritmo en pseudocódigo y representarlo como un diagrama de flujo estructurado con apoyo de Copilot Chat, incluyendo decisiones y rutas alternativas; contrastar el resultado con la propuesta de Copilot Chat.
  - Duración estimada: 35 min
- [Prueba de escritorio en Excel: variables, decisiones, contador y acumulador](Capitulo01/README.md#prueba-de-escritorio-en-excel-variables-decisiones-contador-y-acumulador)
  - Descripción: recorrer distintos casos de prueba en una tabla de Excel Online registrando el estado de las variables, aplicando condicionales y utilizando un contador y un acumulador, y verificar el resultado esperado.
  - Duración estimada: 20 min
- [Identificación de candidatos a RPA](Capitulo01/README.md#identificación-de-candidatos-a-rpa)
  - Descripción: clasificar en una matriz digital las tareas de un proceso según su potencial de automatización, la intervención humana requerida y las excepciones a contemplar, apoyándose en Copilot Chat para contrastar criterios.
  - Duración estimada: 15 min
- [De un problema a un algoritmo con apoyo de Copilot Chat](Capitulo01/README.md#de-un-problema-a-un-algoritmo-con-apoyo-de-copilot-chat)
  - Descripción: caso práctico de algoritmos con un proceso bancario ficticio: definir objetivo, entradas, salidas y restricciones, redactar los pasos de la solución y usar Microsoft 365 Copilot Chat (o un asistente de IA autorizado) para detectar vacíos y excepciones, validando críticamente sus sugerencias.
  - Duración estimada: 25 min
  - [Ver capítulo completo](Capitulo01/README.md)

### Capítulo 2

- [Recorrido por el portal y las plantillas](Capitulo02/README.md#recorrido-por-el-portal-y-las-plantillas)
  - Descripción: explorar el portal, el diseñador y las plantillas; identificar disparadores, acciones y controles, y relacionarlos con el diagrama de flujo construido en el módulo anterior.
  - Duración estimada: 20 min
- [Del algoritmo al primer flujo](Capitulo02/README.md#del-algoritmo-al-primer-flujo)
  - Descripción: crear un flujo instantáneo con entrada manual, una acción de procesamiento, una condición y resultados alternativos (por ejemplo, notificación por correo o Teams); incluye la verificación de accesos y conexiones; ejecutarlo y comprobar su comportamiento.
  - Duración estimada: 55 min
- [Construir y revisar un flujo con apoyo de IA](Capitulo02/README.md#construir-y-revisar-un-flujo-con-apoyo-de-ia)
  - Descripción: redactar un prompt claro para generar o mejorar un flujo con Copilot en Power Automate (o con Microsoft 365 Copilot Chat si el entorno no lo permite), validar el resultado, corregir errores y documentar lo aprendido.
  - Duración estimada: 30 min
- [Ejecución, historial y depuración](Capitulo02/README.md#ejecución-historial-y-depuración)
  - Descripción: ejecutar el flujo con distintos datos, revisar el historial de ejecuciones, interpretar entradas y salidas de cada acción y corregir un error guiado.
  - Duración estimada: 22 min
  - [Ver capítulo completo](Capitulo02/README.md)

### Capítulo 3

- [Automatización de una tarea con variables y condición de negocio](Capitulo03/README.md#automatización-de-una-tarea-con-variables-y-condición-de-negocio)
  - Descripción: construir un flujo instantáneo con entradas manuales, variables y una condición de negocio con resultados diferentes según la decisión; ejecutar casos de prueba y corregir la lógica.
  - Duración estimada: 35 min
- [Contador y acumulador sobre un conjunto de datos](Capitulo03/README.md#contador-y-acumulador-sobre-un-conjunto-de-datos)
  - Descripción: procesar un arreglo de datos de prueba definido en el propio flujo, recorrer sus elementos con Apply to each, aplicar condiciones y generar resultados consolidados con contador y acumulador.
  - Duración estimada: 45 min
- [Expresiones y operaciones con datos](Capitulo03/README.md#expresiones-y-operaciones-con-datos)
  - Descripción: dar formato a fechas y textos, calcular valores con expresiones, y filtrar y transformar datos con Compose, Filter array y Select.
  - Duración estimada: 35 min
- [Decisiones múltiples y flujo programado](Capitulo03/README.md#decisiones-múltiples-y-flujo-programado)
  - Descripción: implementar reglas con Switch y programar la ejecución periódica del flujo mediante recurrencia, verificando su comportamiento.
  - Duración estimada: 25 min
  - [Ver capítulo completo](Capitulo03/README.md)

### Capítulo 4

- [Procesamiento de correos y archivos adjuntos](Capitulo04/README.md#procesamiento-de-correos-y-archivos-adjuntos)
  - Descripción: automatizar la recepción de correos con adjuntos, guardarlos en OneDrive o SharePoint con un nombre estandarizado y notificar el resultado.
  - Duración estimada: 55 min
- [Registro de respuestas de Forms en una lista o tabla](Capitulo04/README.md#registro-de-respuestas-de-forms-en-una-lista-o-tabla)
  - Descripción: crear un formulario, capturar sus respuestas, validar los datos y registrarlos en una lista de SharePoint o tabla de Excel, enviando una confirmación al solicitante.
  - Duración estimada: 60 min
- [Flujo de aprobación](Capitulo04/README.md#flujo-de-aprobación)
  - Descripción: implementar un proceso de solicitud con aprobación (Aprobaciones y Teams u Outlook), con rutas distintas para aprobado y rechazado y actualización del registro.
  - Duración estimada: 40 min
- [Manejo de errores y alertas](Capitulo04/README.md#manejo-de-errores-y-alertas)
  - Descripción: agregar un bloque try/catch con Scope, configurar ejecución posterior y reintentos, y notificar al responsable cuando el flujo falle.
  - Duración estimada: 35 min
  - [Ver capítulo completo](Capitulo04/README.md)

### Capítulo 5

- [Diseño del caso integrador](Capitulo05/README.md#diseño-del-caso-integrador)
  - Descripción: a partir de un proceso de negocio ficticio, definir entradas, salidas, reglas y excepciones, y representar la solución con algoritmo y diagrama de flujo con apoyo de Copilot Chat.
  - Duración estimada: 20 min
- [Implementación y prueba del caso integrador](Capitulo05/README.md#implementación-y-prueba-del-caso-integrador)
  - Descripción: construir el flujo completo con variables, decisiones, iteración, conectores estándar, aprobación y manejo de errores; ejecutar casos de prueba y corregir.
  - Duración estimada: 75 min
- [Presentación y evaluación del caso integrador](Capitulo05/README.md#presentación-y-evaluación-del-caso-integrador)
  - Descripción: presentar la solución y evaluarla con una rúbrica de criterios: lógica y diseño, funcionamiento, validaciones y manejo de errores, y documentación; recibir retroalimentación e identificar qué partes podrían evolucionar hacia RPA.
  - Duración estimada: 25 min
  - [Ver capítulo completo](Capitulo05/README.md)

## Flujo de colaboración

- Trabajar en `changes_course`.
- Crear Pull Request hacia `main`.
- Merge por `Squash and merge`.

---

*Material didáctico preparado por Global K, S.A. de C.V.*
