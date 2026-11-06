# 04. Atributos de calidad

## Propósito

Los atributos de calidad expresan condiciones importantes para que el sistema
sea útil y confiable durante la gestión de proyectos y recursos de la empresa
constructora. Se describen mediante escenarios y criterios iniciales de
verificación. Los valores numéricos propuestos son objetivos de diseño sujetos
a validación con los responsables de la empresa; no representan acuerdos de
nivel de servicio ya establecidos.

## Atributos y escenarios de calidad

| ID | Atributo | Escenario y respuesta esperada | Criterio inicial de verificación | Relación |
|---|---|---|---|---|
| AC01 | Seguridad | Un usuario intenta consultar o modificar información fuera de las funciones de su rol; el sistema restringe la operación y conserva el control de acceso. | El 100 % de las operaciones protegidas debe validar la autorización del usuario; las pruebas deben comprobar accesos permitidos y denegados para cada rol definido. | RF16, HU01 |
| AC02 | Rendimiento | Un usuario consulta proyectos, stock o asignaciones durante la operación habitual; el sistema presenta resultados oportunamente. | Para una carga inicial de hasta 50 usuarios concurrentes, al menos el 95 % de las consultas habituales debería responder en 3 segundos o menos; reportes consolidados, en 5 segundos o menos. | RF02, RF07, RF09, RF14, RF15 |
| AC03 | Disponibilidad | Un usuario autorizado necesita consultar o registrar información durante el horario operativo; el sistema está disponible y puede recuperar datos respaldados ante una falla. | Objetivo inicial de disponibilidad mensual de 99 % durante el horario acordado, excluyendo mantenimientos planificados; verificar la ejecución y restauración de copias de seguridad periódicas. | RF01–RF16 |
| AC04 | Integridad de la información | Se registra un movimiento de almacén, avance o gasto; los datos relacionados permanecen consistentes y asociados al proyecto correcto. | Las operaciones deben validar campos obligatorios, relaciones con registros existentes y reglas de dominio; el stock no debe quedar negativo por un movimiento inválido. | RF04–RF07, RF09, RF11–RF13 |
| AC05 | Usabilidad | Un usuario de un área operativa realiza una tarea frecuente, como registrar un avance o una salida de almacén; puede completarla con información clara sobre el resultado. | En una prueba con usuarios representativos, al menos el 90 % debe completar las tareas frecuentes sin asistencia y sin errores que alteren los datos. | RF03–RF09, HU05–HU11 |
| AC06 | Mantenibilidad | El equipo de desarrollo necesita modificar una regla de un módulo; puede localizar y cambiar su responsabilidad sin afectar innecesariamente a módulos no relacionados. | Las responsabilidades de presentación, negocio y persistencia deben estar separadas; las reglas principales deben contar con pruebas que permitan verificar regresiones. | RF01–RF16 |
| AC07 | Escalabilidad | La empresa incorpora más proyectos, trabajadores y movimientos; el sistema admite el aumento de datos y la incorporación de módulos sin reorganizar por completo la solución. | El diseño debe permitir ampliar la capacidad de persistencia y agregar funciones conservando las interfaces entre capas; validar el comportamiento con un conjunto de datos representativo. | RF01–RF16 |

## Herramientas, aplicación y medición

Las siguientes herramientas y procedimientos se proponen para verificar los
criterios de la tabla anterior. Los resultados deben registrarse como evidencia
de prueba; las metas numéricas siguen sujetas a validación con la empresa.

| ID | Herramienta | Cómo se usará | Qué se medirá y qué evidencia registrar |
|---|---|---|---|
| AC01 | Spring Security y pruebas con JUnit | Preparar casos para cada rol definido e intentar operaciones permitidas y restringidas, tanto en las rutas como en las operaciones protegidas del sistema. | Porcentaje de operaciones protegidas probadas que aplican la autorización esperada; registrar casos aprobados, rechazados y fallidos por rol. |
| AC02 | k6 | Ejecutar una prueba de carga con hasta 50 usuarios concurrentes que consulten proyectos, stock y asignaciones, y generen reportes. | Porcentaje de consultas que responden en 3 segundos o menos, tiempo de respuesta del percentil 95, tiempo de los reportes y cantidad de errores. Comparar con las metas iniciales de la tabla. |
| AC03 | Uptime Kuma y prueba de restauración | Configurar Uptime Kuma para consultar periódicamente la aplicación durante el horario operativo acordado. Realizar por separado una restauración de una copia de seguridad siguiendo el procedimiento definido. | Calcular disponibilidad como el tiempo disponible dividido entre el tiempo monitoreado acordado, excluyendo mantenimientos planificados. Registrar el historial mensual y el resultado de la restauración; Uptime Kuma no sustituye la prueba de respaldo. |
| AC04 | JUnit y MySQL | Crear pruebas de integración que registren movimientos válidos e inválidos y comprueben las validaciones y relaciones de los datos. | Casos aprobados y fallidos; confirmar que los datos inválidos se rechazan, que las relaciones apuntan a registros existentes y que el stock no queda negativo. |
| AC05 | Pruebas con usuarios y cuestionario SUS | Pedir a usuarios representativos que completen tareas frecuentes, como registrar un avance o una salida de almacén, sin asistencia; al finalizar, aplicar el cuestionario SUS. | Porcentaje de usuarios que completan cada tarea sin ayuda ni errores que alteren datos, comparado con la meta inicial del 90 %. Registrar también el puntaje SUS de 0 a 100 como medida complementaria de percepción de usabilidad. |
| AC06 | SonarQube y JUnit | Analizar el código con SonarQube y ejecutar las pruebas de regresión después de modificar una regla o módulo. | Registrar los hallazgos del análisis, las pruebas ejecutadas y sus resultados; revisar separación por capas y que las pruebas principales continúen aprobando. No fijar un umbral de calidad hasta acordarlo con el equipo. |
| AC07 | k6 | Ejecutar escenarios comparables con 10, 50 y 100 usuarios concurrentes usando datos representativos del sistema. | Comparar tiempos de respuesta, especialmente el percentil 95, y porcentaje de errores entre niveles de carga. Acordar previamente los límites aceptables para interpretar si el sistema escala adecuadamente. |

## Consideraciones para la validación

- Las metas de concurrencia, tiempos de respuesta y disponibilidad son
  referencias iniciales. Antes de considerarlas compromisos, deben confirmarse
  con la empresa y medirse en el entorno previsto.
- La selección de herramientas y la forma de aplicación descritas arriba son
  propuestas; deben confirmarse según el entorno técnico y los recursos
  disponibles para ejecutar las pruebas.
- La disponibilidad requiere definir horario operativo, ventanas de
  mantenimiento, frecuencia de respaldos y tiempo objetivo de recuperación.
- La integridad depende de validaciones funcionales y de que las operaciones
  relacionadas se guarden de forma consistente.
- La seguridad debe aplicarse tanto a la interfaz como a las operaciones de
  negocio y al acceso a los datos, de acuerdo con los roles definidos.
