# 06. Drivers arquitectónicos

## Propósito

Los drivers arquitectónicos son las necesidades y restricciones que más
condicionan la estructura del sistema y las decisiones de diseño. Se derivan de
las historias de usuario, los requisitos funcionales, los atributos de calidad
y las restricciones ya documentadas. La arquitectura inicial deberá darles
respuesta explícita.

## Drivers identificados

| ID | Driver y prioridad | Necesidad que lo origina | Referencias | Implicación arquitectónica |
|---|---|---|---|---|
| DA01 | Integrar la gestión de proyectos y recursos — Alta | La empresa necesita relacionar proyectos con actividades, materiales, personal, maquinaria, presupuestos y gastos, y consultar su avance. | RF01–RF13; HU03–HU15 | Organizar la solución en módulos de dominio relacionados y definir identificadores y relaciones consistentes entre los datos del proyecto y sus recursos. |
| DA02 | Proteger el acceso según responsabilidades — Alta | Los usuarios cumplen roles diferentes y no todos deben consultar o modificar la misma información. | RF16; HU01; AC01; RE06 | Incorporar autenticación y autorización centralizadas, aplicar permisos en las operaciones de negocio y mantener los roles separados de la presentación. |
| DA03 | Preservar integridad y trazabilidad de los registros — Alta | Los movimientos de almacén, avances, asignaciones y gastos deben corresponder a entidades existentes y reflejarse coherentemente en las consultas. | RF04–RF13; AC04 | Definir validaciones de dominio y relaciones persistentes; manejar operaciones relacionadas de forma consistente para evitar estados parciales o referencias inválidas. |
| DA04 | Proporcionar información oportuna para el seguimiento — Alta | Gerencia y responsables necesitan consultar avance, disponibilidad de materiales, estado de recursos y reportes para tomar decisiones. | RF02, RF07, RF11, RF14, RF15; AC02 | Favorecer consultas eficientes y consolidación de datos para paneles y reportes, cuidando que reflejen los registros de origen. |
| DA05 | Facilitar mantenimiento y comprensión — Media | El sistema abarca varias áreas de negocio y deberá ser entendible para realizar correcciones y cambios sin propagar efectos innecesarios. | AC06; RE03 | Separar responsabilidades por capas y mantener límites claros entre presentación, lógica de negocio, acceso a datos y persistencia. |
| DA06 | Centralizar y recuperar la información — Alta | El caso busca reducir registros dispersos; la pérdida de datos afectaría la continuidad del seguimiento de las obras. | RE02; AC03 | Utilizar persistencia centralizada, establecer respaldos periódicos y verificar que los datos puedan restaurarse. |
| DA07 | Permitir crecimiento funcional y de datos — Media | La empresa podría incorporar proyectos, usuarios y necesidades adicionales con el tiempo. | AC07; RF01–RF16 | Mantener módulos cohesionados e interfaces estables entre capas para ampliar la solución sin reorganizarla por completo. |
| DA08 | Respetar el contexto tecnológico propuesto — Media | La propuesta plantea una aplicación web con Java y Spring Boot, tecnologías web, Spring Security y MySQL. | RE01–RE07 | Diseñar componentes compatibles con el enfoque web y las tecnologías previstas; confirmar su disponibilidad y adecuación antes de implementarlas. |

## Prioridad y trade-offs

La seguridad, la integridad de los datos y la continuidad de la información se
consideran prioritarias porque los módulos comparten datos operativos y
financieros. Las consultas ágiles también son importantes para el seguimiento,
pero cualquier optimización deberá conservar la consistencia de la información.

La separación por capas responde a mantenibilidad y crecimiento, aunque exige
definir interfaces claras y evitar duplicar reglas entre componentes. Las
tecnologías indicadas son propuestas del caso y no deben prevalecer sobre una
validación de viabilidad o sobre las condiciones académicas y técnicas del
proyecto.

## Uso en la arquitectura inicial

El documento de [arquitectura inicial](./arquitectura/arquitectura-inicial.md)
mostrará cómo los componentes, las capas y la persistencia propuesta atienden
estos drivers. Cualquier decisión que no responda a una necesidad o restricción
identificada deberá considerarse una hipótesis pendiente, no una obligación del
caso.
