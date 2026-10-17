# Modelo C4

El modelo C4 describe la propuesta para el sistema de gestión de la constructora
desde el contexto hasta el diseño interno de un caso de uso. Las vistas se
complementan y no representan una implementación desplegada.

| Nivel | Vista | Qué responde |
|---|---|---|
| 1 | [Contexto del sistema](./Nivel1-DiagramadeContextodelSistema.md) | ¿Qué es el sistema, quién lo usa y cuáles son sus límites? |
| 2 | [Contenedores](./Nivel2-DiagramadeContenedores.md) | ¿Qué aplicaciones y almacenes de datos forman la solución? |
| 3 | [Componentes](./Nivel3-Diagrama-de-Componentes.md) | ¿Cómo se organiza la aplicación de gestión y qué responsabilidad tiene cada módulo? |
| 4 | [Código / diseño interno](./Nivel4-DiagramadeCodigo.md) | ¿Qué clases y contratos colaboran en el caso de uso de salida de almacén? |

Los niveles 1 a 3 ofrecen vistas de contexto y estructura; el Nivel 4 es un
detalle selectivo del caso de uso de almacén. Todos los diagramas son editables
en Mermaid; las fuentes y sus imágenes exportadas se mantienen en
[img/fuentes](../../img/fuentes/README.md). Los nombres de tecnologías y las
relaciones identificadas como propuestas deben confirmarse antes de una
implementación.
