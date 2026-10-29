# Setup Guide General

## Fundamentos de Programación, Automatización y Power Automate

| Control documental | Valor |
|---|---|
| Repositorio | [Netec-Mx/PROG_AUTO_ESS](https://github.com/Netec-Mx/PROG_AUTO_ESS) |
| Rama y revisión analizada | `main` — `4a7f519d07e2276489edc6ac6d5b79f94e5770da` |
| Alcance | Cinco capítulos, 19 README de prácticas, README principal, SETUP_GUIDE.md, CODEOWNERS e inventario de recursos |
| Fecha de revisión | 29 de octubre de 2026 |
| Versión documental | 1.0 |
| Modalidad | Servicios web de Microsoft 365 y flujos de nube de Power Automate |

# Objetivo

Preparar un único entorno para todo el repositorio: cuentas organizacionales, aplicaciones web de Microsoft 365, entorno de Power Automate, conectores estándar, almacenamiento, listas de SharePoint, buzones y aprobaciones funcionales.

La guía consolida únicamente preparación, configuración y validación. Los flujos, formularios y documentos que constituyen actividades del curso se construyen durante la secuencia. No es necesario desarrollarlos todos antes de iniciar.

El repositorio contiene documentación y un logotipo. No distribuye paquetes de importación de flujos, soluciones, instaladores, programas ejecutables ni plantillas Office descargables. Los ejemplos JSON y las expresiones se introducen en el diseñador; no requieren instalar un lenguaje de programación.

# Requisitos de Hardware

| Recurso | Requisito consolidado |
|---|---|
| Equipo | Computadora portátil o de escritorio con procesador de 64 bits |
| Memoria | 8 GB de RAM como mínimo de preparación |
| Espacio libre | 2 GB para archivos, descargas y evidencias |
| Pantalla | Mínimo 1366 × 768; recomendado 1920 × 1080 |
| Periféricos | Teclado y dispositivo apuntador |
| Conexión | Internet estable y HTTPS saliente por TCP 443 durante toda la sesión |

El repositorio no especifica un número mínimo de núcleos ni una velocidad de Internet en Mbps; no se asignan valores inventados. No se requiere GPU ni virtualización de hardware.

# Sistemas Operativos Compatibles

| Sistema | Condición de uso |
|---|---|
| Windows | Sistema con soporte vigente y Microsoft Edge de 64 bits administrado, como configuración común recomendada. |
| macOS | Admitido por el material al referirse a PC o Mac; utilizar navegador compatible actualizado y validar las aplicaciones web del tenant. |

El repositorio no fija versiones de Windows o macOS. La ejecución es web y no utiliza características exclusivas de Power Automate Desktop. Chrome, Firefox y Safari son alternativas admitidas por Microsoft para Power Automate; confirmar su autorización institucional y funcionamiento con los demás servicios antes de sustituir Edge.

# Software Requerido

## Plataforma común

| Componente | Edición o versión requerida | Condición de preparación |
|---|---|---|
| Microsoft Edge | Versión estable vigente, 64 bits, administrada | Registrar versión y comprobar diseñador, ventanas de autenticación y descargas. |
| Power Automate | Servicio web para flujos de nube | Acceso a [make.powerautomate.com](https://make.powerautomate.com/) y al entorno asignado. |
| Microsoft Word para la Web | Servicio organizacional de Microsoft 365 | Crear, editar y guardar DOCX en la ubicación del curso. |
| Microsoft Excel para la Web | Servicio organizacional de Microsoft 365 | Crear y editar XLSX, hojas y tablas. |
| Microsoft PowerPoint para la Web | Servicio organizacional de Microsoft 365 | Elaborar y guardar diagramas y presentaciones. Word o Whiteboard son alternativas autorizables de diagramación en el material. |
| SharePoint Online | Servicio organizacional | Sitio de práctica, listas y permisos de creación/edición. Sigue siendo necesario aunque los documentos estén en OneDrive. |
| OneDrive para la Empresa o biblioteca SharePoint | Servicio organizacional | Almacenamiento de archivos y carpeta destino de adjuntos. Seleccionar una ruta común. |
| Office 365 Outlook / Exchange Online | Buzón organizacional de pruebas activo | Envío, recepción, desencadenadores de correo y notificaciones. Outlook web es suficiente. |
| Approvals | Conector estándar de Power Automate | Solicitudes y respuesta de aprobación operativas en el entorno. |
| Dataverse para Approvals | Servicio administrado asociado al entorno | Dependencia interna de aprobaciones; verificar aprovisionamiento previamente. |

No hay versiones instalables de estos servicios SaaS que puedan fijarse en la estación. Sustituir los marcadores de versión del material por un registro de fecha, tenant, entorno, región visible y experiencia del diseñador. Registrar una compilación solo si el servicio la muestra; no inventarla.

Las etiquetas `V2` o `V3` de las acciones identifican operaciones del conector, no versiones de Office o del sistema operativo. Para el correo, el material utiliza la recepción **When a new email arrives (V3)** y el envío **Send an email (V2)**. Seleccionar sus equivalentes localizados vigentes y evitar operaciones marcadas como obsoletas.

## Componentes opcionales

| Componente | Cuándo aplica |
|---|---|
| Copilot Chat o asistente de IA institucional autorizado | Apoyo opcional para revisar texto y propuestas. Su ausencia no debe bloquear el recorrido; el material incluye alternativas controladas. |
| Copilot integrado en Power Automate | Solo si ya está disponible y autorizado. No se necesita para crear manualmente los flujos. |
| Microsoft Teams | Solo si se elige una notificación alternativa. La ruta común utiliza correo. |
| Whiteboard | Solo si se autoriza como alternativa de diagramación. |

La guía no exige Microsoft 365 Copilot Premium, Power Automate Premium, AI Builder, agentes persistentes, Designer, Planner, automatización de escritorio, extensiones RPA, máquinas virtuales, Docker, Kubernetes ni gateway local. Tampoco requiere Python, Java, .NET, Node.js, SDK, IDE o herramientas CLI de Power Platform.

# Herramientas y Dependencias

## Licencias y cuentas

Antes del curso, TI debe confirmar para cada participante:

- Cuenta organizacional Microsoft Entra ID en el tenant de capacitación.
- Suscripción con derechos para crear y ejecutar flujos de nube con conectores estándar. Confirmar que el plan de servicio de Power Automate esté habilitado; poder iniciar sesión en Microsoft 365 no basta.
- Acceso a Word, Excel, PowerPoint, Forms, SharePoint y almacenamiento empresarial utilizados en la ruta común.
- Buzón Exchange Online de laboratorio activo y conexiones autenticadas.
- Derecho de uso de aprobaciones y acceso del aprobador al entorno y al centro de aprobaciones.
- MFA y requisitos de dispositivo satisfechos, si los exige el tenant.

Los conectores de la ruta común son estándar; no se requiere contratar Premium por su sola utilización. Esta condición no concede automáticamente los servicios de destino: una conexión estándar de Outlook necesita un buzón válido y una de SharePoint necesita permisos en el sitio. El administrador debe verificar el conjunto real de licencias, no solo el nombre comercial de una suscripción.

## Matriz de permisos

| Ámbito | Permiso necesario |
|---|---|
| Entorno Power Platform | Acceso al entorno autorizado y capacidad de creador —Environment Maker o asignación equivalente según su configuración— para crear conexiones y flujos propios. |
| Flujos | Crear, editar, guardar, activar/desactivar, ejecutar y consultar historial de los flujos propios. |
| SharePoint | Crear/administrar listas y columnas si lo hace el participante; si TI las preaprovisiona, al menos agregar, consultar y actualizar elementos. |
| Biblioteca o OneDrive | Crear carpetas, leer, escribir y abrir archivos del curso. |
| Microsoft Forms | Crear/editar formularios propios, consultar respuestas y usar su conexión. |
| Exchange Online | Enviar y recibir correo interno de prueba; acceder a la carpeta del buzón seleccionada. |
| Aprobaciones | Recibir y responder solicitudes con las cuentas internas de laboratorio. |

Los permisos de creador de entorno no sustituyen los de SharePoint, Forms o correo. El participante no necesita ser administrador global. TI conserva la administración de licencias, políticas y aprovisionamiento inicial de Approvals.

## Conectores comunes

| Conector o capacidad | Preparación |
|---|---|
| Office 365 Outlook | Conexión organizacional válida al buzón de pruebas. |
| SharePoint | Conexión con acceso al sitio y listas asignados. |
| OneDrive for Business | Necesario si se elige OneDrive como destino de archivos; aprovisionar el espacio y autenticar la conexión. |
| Microsoft Forms | Cuenta organizacional y acceso de propietario al formulario que se construya. |
| Approvals | Servicio aprovisionado y conexión válida, si la experiencia la solicita. |
| Operaciones integradas de Power Automate | Desencadenador manual, Recurrence, variables, Condition, Switch, Apply to each, Compose, Filter array, Select, Scope y terminación. No requieren instalar paquetes. |

Confirmar que las políticas de datos permiten combinar estos conectores en los flujos del curso. Una clasificación incompatible o un bloqueo de acción puede impedir guardar o ejecutar aun cuando las licencias sean correctas. TI debe resolverlo dentro del entorno autorizado, sin desactivar políticas generales del tenant.

Aunque un título menciona registrar datos en «una lista o tabla», los pasos desarrollados utilizan SharePoint. Esta guía adopta esa ruta completa; Excel para la Web se utiliza como editor de evidencias, no exige añadir el conector Excel Online (Business). La edición manual de documentos tampoco exige el conector Word Online (Business).

# Instalación y Configuración

## 1. Preparar el acceso web

1. Actualizar el navegador mediante el mecanismo institucional y registrar su versión.
2. Utilizar un perfil con la cuenta organizacional del laboratorio.
3. Abrir [Power Automate](https://make.powerautomate.com/), autenticarse y seleccionar el entorno indicado por TI.
4. Confirmar nombre y, cuando esté disponible, identificador del entorno y región. Mantener ese mismo entorno durante todo el curso.
5. Abrir las aplicaciones de Office desde el iniciador de Microsoft 365 y comprobar edición y guardado.
6. Abrir [Outlook web](https://outlook.office.com/), [Forms](https://forms.office.com/) y el sitio SharePoint asignado.

No crear un entorno nuevo con la cuenta del participante como parte del setup. Utilizar uno institucional ya habilitado. La licencia para utilizar conectores estándar no equivale a capacidad para crear cualquier tipo de entorno.

## 2. Aprovisionar el entorno de capacitación

Esta preparación corresponde a TI o al administrador antes de la sesión:

1. Seleccionar un entorno activo, con licenciamiento y capacidad adecuados, separado de procesos productivos.
2. Asignar a los participantes o al grupo de capacitación los accesos de creador necesarios.
3. Validar políticas de datos y las conexiones de la ruta común.
4. Confirmar que pueden guardarse y ejecutarse flujos instantáneos, automatizados y programados.
5. Preparar el servicio Approvals y probarlo con una cuenta equivalente a la del participante.
6. Comunicar el entorno y los recursos asignados mediante un registro sin secretos.

No se exige un tipo concreto de entorno —Sandbox, Production o Default— porque el repositorio no lo fija. No cambiar al entorno Default únicamente para evitar un error de permisos; utilizar el autorizado por el cliente.

## 3. Preparar Approvals y Dataverse

Approvals guarda sus datos en Dataverse. En un entorno no predeterminado, el primer aprovisionamiento necesita un administrador del entorno; los usuarios posteriores no requieren esa elevación. En el entorno predeterminado el servicio puede crear la base automáticamente. Completar este proceso y una aprobación de prueba antes del curso.

No se instala un motor SQL local ni se crean tablas empresariales en Dataverse para estas prácticas. La ruta de datos del curso utiliza listas de SharePoint; el almacenamiento de aprobaciones es una dependencia interna diferente. Usar Approvals como conector estándar no obliga por sí solo a añadir un conector Dataverse Premium al flujo.

La prueba debe confirmar que una cuenta interna recibe una aprobación, puede responderla y la ejecución continúa. Si falla el aprovisionamiento, TI debe revisar base, aplicaciones de servicio y permisos del entorno con la documentación oficial; no elevar a todos los participantes ni activar pruebas Premium para ocultar el problema.

## 4. Establecer cuentas y destinatarios de laboratorio

Preparar los siguientes roles con identidades internas habilitadas:

| Rol | Necesidad |
|---|---|
| Creador del flujo | Usuario que diseña y ejecuta; propietario de sus conexiones. |
| Solicitante | Cuenta que recibe confirmaciones y resultados. |
| Aprobador de ruta baja | Usuario capaz de responder aprobaciones. |
| Aprobador de ruta alta | Usuario capaz de responder aprobaciones. |
| Responsable del flujo | Recibe alertas técnicas. |
| Interesados de prueba | Destinatarios internos opcionales para comprobar notificaciones múltiples. |

Los roles pueden compartir una misma cuenta en una prueba controlada, cuando lo permita el instructor; no se exige una cuenta distinta por cada rol. Para distinguir rutas y colaboración es preferible disponer de cuentas de prueba separadas.

**Corregir las direcciones de muestra antes de ejecutar:** valores como `AprobadorArea-Prueba@contoso.example`, `ResponsableFlujo-Prueba@contoso.example` o `destinatario-pruebas@contoso.example` son marcadores didácticos. No son buzones entregables ni usuarios Entra válidos. Sustituirlos por cuentas internas de laboratorio realmente aprovisionadas, manteniendo ficticios los datos del negocio. No utilizar clientes, correos externos o cuentas personales.

## 5. Crear las conexiones autorizadas

Desde el área de conexiones del entorno seleccionado, crear o reparar únicamente las conexiones de la matriz común utilizando la cuenta organizacional asignada. Confirmar que no existen solicitudes de autenticación pendientes.

Registrar conector, propietario y entorno. No guardar contraseñas, cookies o tokens en los documentos del curso. Las conexiones de otro entorno o de un compañero no se vuelven utilizables por compartir un vínculo a un flujo.

Las instrucciones que prohíben crear o reparar conexiones durante un recorrido introductorio se conservan para esa actividad. Esta guía adelanta su preparación al administrador o a la sesión de setup autorizada, de modo que la secuencia posterior encuentre conexiones disponibles.

# Configuración Base para los Laboratorios

## Ubicación única de archivos

Preparar en OneDrive para la Empresa o en una biblioteca SharePoint autorizada:

```text
/Laboratorio-FPA-PA/
└── Modulo-01/
    └── AdjuntosCorreo/
```

`Modulo-01` es la carpeta global reutilizada por todo el repositorio, aunque existan cinco capítulos. No crear una raíz distinta por capítulo.

Si se usa SharePoint, registrar por separado URL del sitio, biblioteca y carpeta; la ruta lógica anterior no incluye necesariamente el nombre de la biblioteca. En OneDrive, registrar la carpeta respecto de su raíz. Seleccionar la carpeta con el explorador del conector para evitar asumir que la misma cadena es válida en ambos servicios.

Una carpeta local homónima no sustituye al destino cloud de una acción Crear archivo. No se necesita instalar el cliente de sincronización de OneDrive.

Crear un archivo de texto inocuo, por ejemplo `evidencia_p13.txt`, con una línea de prueba, para validar adjuntos. El resto de documentos de algoritmo, presentaciones y hojas se crea en la secuencia o lo entrega el instructor. No generar un DOCX, XLSX o PPTX vacío renombrando un archivo de texto.

## Aislamiento de los recursos

Asignar un sitio de práctica separado por participante o equipo cuando varias personas construyan flujos con los mismos nombres de lista. Así pueden conservarse los nombres indicados sin que todos los flujos procesen todos los elementos.

Si el cliente utiliza un sitio compartido, debe definir previamente la separación y filtros equivalentes. Una carpeta de evidencias por usuario no aísla los desencadenadores de listas. Evitar activar simultáneamente varias versiones del mismo flujo sobre la misma lista sin una regla explícita de aislamiento.

## Listas de SharePoint

Hay **tres listas diferentes**. No asumir que la lista creada para capturar Forms satisface el prerrequisito de las aprobaciones. Preparar `SolicitudesOperacion` y `SolicitudesAbastecimiento` antes de que se necesiten; el material las asume existentes. `SolicitudesPA_B3` se crea durante la secuencia, por lo que en el setup basta con comprobar permisos y tener su contrato preparado. Si TI preaprovisiona alguna, reutilizarla sin duplicarla.

### Contrato de captura: SolicitudesPA_B3

| Columna | Tipo | Configuración |
|---|---|---|
| Título | Texto de una línea; columna predeterminada | Almacena el tipo de solicitud. Nombre interno habitual: `Title`. |
| Descripcion | Varias líneas de texto | Obligatoria. |
| AreaSolicitante | Texto de una línea | Obligatoria. |
| Prioridad | Elección | `Baja`, `Media`, `Alta`. |
| ValorEstimado | Número | Obligatoria; admite cero y valores positivos. |
| FechaRegistro | Fecha y hora | Incluir hora. |
| CorreoSolicitante | Texto de una línea | Opcional. |
| EstadoRegistro | Elección | `Registrado`, `Rechazado`. |
| ObservacionesValidacion | Varias líneas de texto | Opcional. |

No añadir una restricción de lista que sustituya inadvertidamente las validaciones que el flujo debe observar. Si se necesita probar un rechazo en el flujo por valor negativo, una validación de columna que impida cualquier inserción negativa puede cambiar el comportamiento de la prueba. Coordinar la prueba sin relajar datos productivos.

### Contratos de aprobación e integración

La tabla consolida campos compartidos sin convertir las listas en un solo recurso. Los tipos de `SolicitudesOperacion` se normalizan aquí porque el repositorio enumera sus columnas sin fijar tipos.

| Columna visible | Tipo consolidado | SolicitudesOperacion | SolicitudesAbastecimiento |
|---|---|---|---|
| TituloSolicitud | Texto de una línea | Sí; entrada principal | Sí; obligatoria |
| SolicitanteCorreo | Texto de una línea | Sí | Sí; obligatoria |
| Area | Texto de una línea | Sí | Sí; obligatoria |
| Monto | Número, con decimales si se necesitan | Sí | Sí; obligatoria |
| Justificacion | Varias líneas de texto, sin formato enriquecido | Sí | Sí; obligatoria en el contrato original |
| InteresadosCorreo | Varias líneas de texto | No se requiere | Sí; opcional, separador `;` |
| Estado | Texto de una línea | Sí | Sí; obligatoria, con valor inicial de borrador si se necesita crear elementos manualmente |
| AprobadorAsignado | Texto de una línea | Sí | Sí; opcional al crear |
| ComentarioAprobador | Varias líneas de texto | Sí | Sí; opcional |
| FechaDecision | Fecha y hora | Sí | Sí; opcional |
| DetalleError | Varias líneas de texto | No se requiere | Sí; opcional |

En las dos listas, puede renombrarse la columna predeterminada Título como `TituloSolicitud` para evitar otra columna obligatoria sin mapear. Su nombre interno continúa siendo `Title`; verificar el campo real del contenido dinámico. Si se crea una columna nueva en vez de renombrar, resolver expresamente la obligatoriedad de la columna predeterminada.

Conservar `Monto` como dato numérico, no como texto, y correos como cadenas porque así los consumen las instrucciones. No cambiar esos campos a Persona sin adaptar y probar los mapeos correspondientes. El `ID` del elemento lo genera SharePoint; no crear otra columna manual con ese nombre.

El contrato original impide dejar vacía una `Justificacion` marcada obligatoria, aunque después se propone una prueba con ese campo vacío. Para ese caso, usar la prueba de `Monto = 0` que también contempla el material, o una copia de lista de pruebas con la restricción ajustada por el instructor. No exigir una prueba que la interfaz de origen impide enviar.

## Forms y captura de identidad

Confirmar permiso para crear un formulario propio y recuperar sus detalles mediante el conector Microsoft Forms. El formulario del curso se construye después; no se necesita prellenarlo ni crear sus respuestas durante el setup.

La confirmación al respondedor requiere respuestas autenticadas de la organización y el registro de identidad permitido por TI. Si el correo del respondedor no está disponible, el flujo puede omitir esa notificación según el material. No activar respuestas públicas para resolverlo.

En Power Automate, seleccionar los campos desde el contenido dinámico de Obtener detalles de la respuesta. Los identificadores internos de Forms no deben suponerse iguales a los títulos visibles `Descripción` o `Valor estimado`. Las expresiones de ejemplo deben adaptarse a los identificadores reales que genere el formulario.

## Parámetros y archivos de configuración

No se requiere `.env`, variables de entorno del sistema, archivo de conexión local, token de API, aplicación Entra registrada ni certificado para programar. Las conexiones se autentican en el servicio.

Guardar en un registro institucional de preparación los valores reales de entorno, sitio, biblioteca, carpeta, listas y cuentas de prueba. Son parámetros de selección de las acciones, no variables de entorno de soluciones Power Platform que el repositorio obligue a crear.

Las variables `ResponsableFlujo`, `varMonto` y otras del material son variables o valores internos de los flujos; se configuran en el diseñador cuando corresponda. No exportarlas a Windows o macOS.

## Continuidad y nombres

Aplicar estas normalizaciones en las copias de trabajo antes de impartir:

| Inconsistencia | Configuración coherente |
|---|---|
| Nombre del flujo de aprobación: los pasos crean `PA15_DecisionSolicitud`, pero otros apartados lo llaman `SolicitudOperacion-Aprobacion-v1` | Usar `PA15_DecisionSolicitud` como nombre de origen y sustituir por ese nombre las referencias al flujo base en el material de continuidad. No crear dos flujos idénticos para satisfacer nombres diferentes. |
| Estados de la misma lista alternan `Aprobado`/`Rechazado` y `Aprobada`/`Rechazada`, con errores de distinto nombre | Mantener `Estado` como texto. Conservar los valores literales de la versión de flujo que se ejecuta; no imponer una lista cerrada que rechace la otra versión. Si se normalizan los valores, hacerlo conjuntamente en acciones y comprobaciones de esa copia. |
| Versiones base y robusta apuntan a la misma lista | Desactivar la versión anterior al probar su sustituta y desactivar las copias de error al terminar. Conservarlas para revisión sin provocar aprobaciones duplicadas. |
| SETUP_GUIDE.md usa `Netec-Mx/261029-PROG-AUTO-ESS` | Consultar el repositorio real `Netec-Mx/PROG_AUTO_ESS`. |
| El inventario inicial nombra el formulario `PA-B3-SolicitudServicio`, pero los pasos lo crean como `PA-B3-SolicitudesServicio` | Conservar el nombre de los pasos, `PA-B3-SolicitudesServicio`, y seleccionar el mismo formulario por su identificador real en disparador y acción. |
| El README enlaza una demostración en `Capitulo01/Demostracion01/README.md` | Esa carpeta no existe en el commit revisado. El instructor debe proporcionar la demostración o acceso a un flujo propio ya preparado; no hay paquete de demo que importar del repositorio. |
| Enlaces de regreso esperan README de capítulo que no existen | Abrir las rutas reales `CapituloXX/PracticaXX/README.md` desde el README principal o el árbol del repositorio. No usar los antiguos enlaces por anclas del SETUP_GUIDE. |

El flujo robusto y el caso integrador se crean en el recorrido académico; no son prerrequisitos de instalación de la primera sesión. No se requiere cargar flujos terminados para cubrir artificialmente esta continuidad.

# Servicios Externos Requeridos

| Servicio | Acceso |
|---|---|
| Microsoft Entra ID | Autenticación, MFA y acceso al tenant. |
| Power Automate y Power Platform | Portal, diseñador, ejecución, historial y conexiones. |
| Exchange Online / Outlook | Buzón de pruebas, notificaciones y recepción de adjuntos. |
| SharePoint Online y OneDrive para la Empresa | Listas y almacenamiento cloud elegido. |
| Microsoft Forms | Formularios organizacionales y consulta de respuestas. |
| Microsoft 365 web | Edición de documentos, hojas y presentaciones. |
| Dataverse / Approvals | Persistencia y gestión interna de aprobaciones. |
| GitHub | Consulta o descarga de la documentación pública. |

TI debe revisar los [endpoints de Power Automate](https://learn.microsoft.com/en-us/power-automate/ip-address-configuration) y los [endpoints de Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges), junto con proxy, DNS, cookies y políticas de acceso. No abrir puertos entrantes en las computadoras ni instalar un servidor HTTP local.

No se necesita una suscripción Azure o AWS del participante, facturación por consumo ni acceso a sistemas bancarios. El uso de servicios cloud de Microsoft 365 no equivale a desplegar recursos propios en Azure.

# Validación del Entorno

Completar la siguiente validación con una cuenta de participante antes de iniciar el curso. Una cuenta administradora por sí sola no demuestra que el grupo tendrá acceso.

| Comprobación | Resultado esperado |
|---|---|
| Identidad y entorno | Cuenta correcta y entorno asignado visible. |
| Derechos de creación | Puede guardar, ejecutar y consultar el historial de un flujo temporal de validación. |
| Conectores y políticas | Conexiones de la ruta común autenticadas y combinación permitida. |
| Office web | Crea, guarda y vuelve a abrir DOCX, PPTX y XLSX en la carpeta autorizada. |
| Almacenamiento | Carpeta global y `AdjuntosCorreo` accesibles con escritura. |
| SharePoint | Listas preexistentes preparadas, tipos revisados y permiso para crear la lista de captura. |
| Correo | Buzón recibe un mensaje de prueba y permite enviar uno a una cuenta interna autorizada. |
| Forms | Puede crear un formulario temporal, enviar una respuesta interna y consultar sus detalles. |
| Approvals | Crea una solicitud de prueba, el aprobador responde y la ejecución continúa. |
| Dataverse interno | Aprovisionamiento de aprobaciones terminado en el mismo entorno. |
| Aislamiento | Un recurso de un equipo no dispara flujos de otro ni versiones duplicadas. |
| IA opcional | Se documenta su disponibilidad o el uso de la alternativa sin IA. |

## Pruebas mínimas de preparación

1. **Edición:** crear documentos temporales desde las aplicaciones web, introducir texto, una tabla o una forma según el editor, guardar y reabrir. No es necesario producir los entregables del curso.
2. **Datos:** antes de activar flujos del curso, agregar, editar y retirar únicamente un elemento temporal propio en cada lista preaprovisionada. Proporcionar sus campos obligatorios.
3. **Ejecución:** guardar y ejecutar un flujo instantáneo temporal con una acción Compose y el texto `SETUP_OK`. Comprobar el resultado en el historial.
4. **Conectores:** en recursos temporales aislados de setup, validar recepción de correo con adjunto inocuo, creación del archivo en el destino autorizado, captura de una respuesta Forms y recuperación de sus detalles.
5. **Aprobaciones:** TI valida una solicitud asignada a la cuenta interna de prueba y su respuesta. No iniciar una aprobación contra los buzones de usuarios de producción.
6. **Cierre:** desactivar los flujos temporales y conservar el registro del resultado. Retirar solo los recursos temporales propios según las reglas del aula.

Estas son verificaciones técnicas del entorno, no sustituyen las pruebas de lógica de las prácticas. Registrar fecha, usuario de laboratorio, entorno, recurso probado y resultado, sin secretos.

Las ejecuciones por recurrencia y algunos desencadenadores pueden presentar demora según el plan. No garantizar una activación de correo en dos minutos para todas las suscripciones. Mantener el intervalo de prueba de cinco minutos indicado por el material y comprobar las características del plan; no comprar Premium para acelerar una demostración.

# Comandos de Verificación

El recorrido funciona en navegador y no necesita instalar CLI. Los comandos siguientes son diagnósticos opcionales del puesto; no crean recursos cloud ni acreditan permisos de Power Automate.

## Windows PowerShell

```powershell
$PSVersionTable.PSVersion
Get-CimInstance Win32_OperatingSystem |
    Select-Object Caption, Version, OSArchitecture
Get-CimInstance Win32_ComputerSystem |
    Select-Object @{Name='RAM_GB';Expression={[math]::Round($_.TotalPhysicalMemory / 1GB, 1)}}
Get-PSDrive -PSProvider FileSystem |
    Select-Object Name, Root, @{Name='Libre_GB';Expression={[math]::Round($_.Free / 1GB, 1)}}

$serviceHosts = @(
    'make.powerautomate.com',
    'login.microsoftonline.com',
    'outlook.office.com',
    'forms.office.com',
    'github.com'
)
foreach ($serviceHost in $serviceHosts) {
    Resolve-DnsName -Name $serviceHost -ErrorAction Continue
    Test-NetConnection -ComputerName $serviceHost -Port 443 -InformationLevel Detailed
}
```

Resultados esperados: sistema de 64 bits, aproximadamente 8 GB de RAM instalada o más, 2 GB libres en la unidad de trabajo, resolución DNS correcta y `TcpTestSucceeded : True` si la red permite salida directa. En redes con proxy obligatorio, contrastar la prueba directa con el acceso real del navegador.

Registrar la versión de Edge desde `edge://settings/help`. Los dominios de ejemplo no sustituyen la lista completa de endpoints ni el host SharePoint real del cliente.

## macOS, terminal

```bash
sw_vers
uname -m
sysctl -n hw.memsize
df -h "$HOME"
curl --version
curl -L -sS -o /dev/null -w 'HTTP final: %{http_code}\n' \
  --connect-timeout 10 --max-time 30 https://make.powerautomate.com/
```

Resultados esperados: sistema y arquitectura identificados, memoria física de al menos 8 GB —el comando devuelve bytes— y 2 GB libres en el volumen elegido. Un código HTTP `000` indica que no se recibió respuesta HTTP. Una página de autenticación o una respuesta HTTP correcta no demuestra acceso al entorno ni a los conectores.

## Verificación autenticada obligatoria

Abrir las aplicaciones con la cuenta asignada y completar las comprobaciones de la sección anterior. No hay wrappers `gradlew` o `mvnw`, proyectos compilables ni un script del repositorio para validar automáticamente el tenant.

No instalar módulos de administración, registrar aplicaciones Entra ni solicitar tokens solo para completar esta validación. La versión del navegador, los derechos de servicio y la prueba funcional en la interfaz aportan la evidencia pertinente.

# Troubleshooting

| Problema | Comprobación y corrección |
|---|---|
| No aparece el entorno | Confirmar tenant, cuenta, grupo y permisos asignados. No cambiar a otro entorno para continuar sin autorización. |
| Puede abrir el portal pero no guardar flujos | Revisar licencia, plan de servicio, rol de creador y políticas de datos. |
| Conector con autenticación pendiente | Reparar la conexión con la cuenta institucional del entorno correcto. No usar credenciales personales o de otro participante. |
| Aparece una solicitud Premium | Revisar el conector o acción seleccionado. Mantener la ruta estándar prevista; no activar pruebas de pago como solución general. |
| Aprovisionamiento de Approvals falla | TI debe revisar Dataverse y los permisos de primera inicialización en ese entorno. No necesita una base SQL local. |
| La aprobación no llega | Verificar que el destinatario sea una cuenta interna activa, no una dirección `.example`, y que pueda responder desde el portal. |
| Correos o aprobaciones duplicados | Revisar versiones activas y aislamiento de listas. Desactivar el flujo anterior y las copias de prueba que no deban escuchar. |
| El conector no muestra sitio, lista o archivo | Confirmar permisos de la identidad de conexión y la selección de sitio/biblioteca. Un enlace compartido no garantiza acceso de la conexión. |
| No existe `SolicitudesOperacion` | Prepararla con su contrato. No reemplazarla por `SolicitudesPA_B3`, cuyos campos son diferentes. |
| Falla un estado al actualizar | Revisar si `Estado` se creó como Elección con un catálogo incompleto. Usar texto conforme a esta guía o normalizar todo el contrato de la versión utilizada. |
| Falta un campo obligatorio al actualizar | Verificar Título/`Title`, columnas renombradas y conservación de campos requeridos. No crear otro ID. |
| Forms devuelve campos vacíos | Seleccionar contenido dinámico real; no usar el texto de la pregunta como identificador interno supuesto. |
| Forms no devuelve correo del respondedor | Revisar respuestas internas y registro de identidad permitido. Mantener la omisión de confirmación prevista si no hay correo. |
| El disparador tarda más de lo indicado | Revisar flujo activo, filtros y frecuencia efectiva según plan. La demora de polling no se corrige aumentando hardware local. |
| Un archivo existe localmente pero Crear archivo falla | Confirmar carpeta cloud, biblioteca, conexión y permiso de escritura; la carpeta local no es el destino del conector. |
| Copilot no aparece | Utilizar la alternativa sin IA del material. Copilot Chat y Copilot del diseñador tienen habilitación independiente. |
| No se encuentra la demostración inicial o un README de capítulo | Consultar las rutas reales del repositorio y solicitar al instructor el recurso de demostración que falta. |

# Checklist Final

- [ ] Equipo de 64 bits, 8 GB de RAM, 2 GB libres y pantalla suficiente.
- [ ] Navegador actualizado y acceso HTTPS a los servicios del curso.
- [ ] Cuenta organizacional y licencias de los servicios comunes verificadas.
- [ ] Entorno autorizado identificado y permisos de creador operativos.
- [ ] Conectores estándar y políticas de combinación validados.
- [ ] Buzón de laboratorio activo y destinatarios internos aprovisionados.
- [ ] Direcciones `.example` sustituidas en la configuración ejecutable.
- [ ] Word, Excel y PowerPoint web guardan y reabren archivos.
- [ ] Carpeta cloud `/Laboratorio-FPA-PA/Modulo-01/AdjuntosCorreo` preparada.
- [ ] Sitio de práctica, biblioteca y separación por equipo definidos.
- [ ] Listas `SolicitudesOperacion` y `SolicitudesAbastecimiento` preparadas con tipos correctos.
- [ ] Permisos y contrato listos para crear `SolicitudesPA_B3` y el formulario durante la secuencia.
- [ ] Dataverse/Approvals aprovisionado y aprobación respondida en el entorno real.
- [ ] Normalización de nombre del flujo base y estados documentada para las copias de trabajo.
- [ ] Materiales o plantillas del instructor y demostración inicial disponibles.
- [ ] IA opcional validada o alternativa sin IA comunicada.
- [ ] Pruebas de preparación registradas y flujos temporales desactivados.

# Resumen

La plataforma común utiliza Microsoft 365 web, SharePoint, Exchange Online, Forms y Power Automate con conectores estándar. Dataverse participa como almacenamiento interno de Approvals. El entorno queda listo al demostrar permisos de creación, conexiones, almacenamiento, edición documental y una aprobación funcional con cuentas de laboratorio.

## Alcance de la revisión y pendientes del cliente

Se inspeccionaron los archivos documentales de los cinco capítulos y las 19 prácticas, además del README, SETUP_GUIDE, CODEOWNERS e inventario del commit indicado. Se revisaron sus prerrequisitos, configuraciones, instrucciones, recursos, expresiones, validaciones y continuidad para consolidar las dependencias.

No se tuvo acceso al tenant ni a cuentas del cliente. La disponibilidad de licencias, políticas, listas, buzones, entorno y aprobaciones debe validarse allí antes de impartir. Los comandos se proporcionan para la estación de destino; no se afirma haber ejecutado pruebas autenticadas de los 19 laboratorios.

El instructor debe proporcionar las plantillas de matriz, diseño y rúbrica que el material menciona y no distribuye como archivos. Los documentos y flujos producidos durante el recorrido son resultados académicos posteriores, no archivos ausentes que deban inventarse durante el setup.

## Referencias oficiales

- [Repositorio en la revisión analizada](https://github.com/Netec-Mx/PROG_AUTO_ESS/tree/4a7f519d07e2276489edc6ac6d5b79f94e5770da).
- [Power Automate: navegadores y preguntas frecuentes](https://learn.microsoft.com/en-us/power-automate/frequently-asked-questions).
- [Licenciamiento de Power Automate](https://learn.microsoft.com/en-us/power-platform/admin/power-automate-licensing/faqs).
- [Entornos y roles de Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/environments-overview).
- [Políticas de datos](https://learn.microsoft.com/en-us/power-platform/admin/wp-data-loss-prevention).
- [Inicio y requisitos de Approvals](https://learn.microsoft.com/en-us/power-automate/get-started-approvals).
- [Office 365 Outlook](https://learn.microsoft.com/en-us/connectors/office365/).
- [SharePoint](https://learn.microsoft.com/en-us/connectors/sharepointonline/).
- [OneDrive for Business](https://learn.microsoft.com/en-us/connectors/onedriveforbusiness/).
- [Microsoft Forms](https://learn.microsoft.com/en-us/connectors/microsoftforms/).
- [Approvals](https://learn.microsoft.com/en-us/connectors/approvals/).
- [Límites y configuración de flujos](https://learn.microsoft.com/en-us/power-automate/limits-and-config).
- [Resolve-DnsName](https://learn.microsoft.com/en-us/powershell/module/dnsclient/resolve-dnsname).
- [Test-NetConnection](https://learn.microsoft.com/en-us/powershell/module/nettcpip/test-netconnection).
- [Opciones de cURL](https://curl.se/docs/manpage.html).
