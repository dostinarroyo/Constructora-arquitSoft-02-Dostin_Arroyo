# 05. Restricciones del proyecto y de arquitectura

## Propósito

Las restricciones delimitan las opciones disponibles para construir la
solución. A diferencia de los requisitos funcionales, no describen una
operación que el sistema deba ofrecer; establecen condiciones, límites o
decisiones tecnológicas para el diseño. Cuando una tecnología aparece como
prevista en la propuesta, se identifica como tal y no como una decisión
contractual irrevocable.

## Restricciones identificadas

| ID | Restricción | Clasificación | Fundamento e implicación |
|---|---|---|---|
| RE01 | La solución se plantea como una plataforma web para centralizar la información de la empresa constructora. | Contexto del proyecto | La interacción de los distintos responsables se realizará mediante una aplicación accesible desde un navegador; la propuesta no especifica aún el entorno de despliegue. |
| RE02 | La información de los módulos deberá mantenerse centralizada en una base de datos. | Restricción de datos | La propuesta del caso busca reducir la dispersión de registros y relacionar proyectos, actividades, recursos y gastos. |
| RE03 | La arquitectura propuesta separará presentación, lógica de negocio, acceso a datos y persistencia. | Decisión arquitectónica prevista | La separación en capas aparece en la propuesta inicial y busca facilitar la organización y el mantenimiento. |
| RE04 | Se prevé Java con Spring Boot para el backend. | Tecnología prevista | La propuesta del proyecto menciona este conjunto para implementar servicios y lógica de negocio; su confirmación final depende de las condiciones del curso y del equipo. |
| RE05 | Se prevé HTML, CSS, JavaScript y Bootstrap para la interfaz web. | Tecnología prevista | Estas tecnologías se plantean para construir la presentación web y sus componentes de interfaz. |
| RE06 | Se prevé Spring Security para autenticación y control de acceso por roles. | Tecnología prevista | La necesidad de controlar el acceso está definida en el caso; esta tecnología es la opción propuesta para implementarla. |
| RE07 | Se prevé MySQL para la persistencia de datos. | Tecnología prevista | La propuesta identifica MySQL como base de datos para centralizar la información de los módulos. |
| RE08 | El alcance inicial no incluye control de maquinaria mediante IoT, GPS o sensores físicos. | Límite de alcance | El sistema gestionará registros de maquinaria y su estado y asignación, pero no telemetría de equipos. |
| RE09 | El alcance inicial no incluye diseño arquitectónico ni cálculo estructural de obras. | Límite de alcance | El sistema se orienta a la gestión administrativa y operativa, no al diseño técnico de edificaciones. |
| RE10 | El alcance inicial no incluye emisión de comprobantes electrónicos ante SUNAT ni integración con sistemas contables externos. | Límite de alcance | La gestión financiera prevista se limita al registro y consulta de presupuestos y gastos dentro del sistema. |

## Aspectos aún no definidos

La propuesta del caso no establece condiciones obligatorias sobre proveedor de
alojamiento, sistema operativo, presupuesto de infraestructura, licencias,
navegadores compatibles, política legal de conservación de datos ni
herramientas de integración y despliegue. Estos aspectos no se asumen como
restricciones y deberán acordarse si resultan necesarios para la implementación.

## Diferencia respecto de los requisitos funcionales

Las restricciones RE04–RE07 expresan tecnologías propuestas, mientras que los
requisitos funcionales describen capacidades observables del sistema, como
registrar proyectos o consultar existencias. El uso de una tecnología concreta
no sustituye el cumplimiento de dichas capacidades. De igual forma, las
exclusiones de alcance RE08–RE10 evitan interpretar el sistema como una
plataforma de telemetría, diseño estructural o contabilidad externa.
