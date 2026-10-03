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

## Consideraciones para la validación

- Las metas de concurrencia, tiempos de respuesta y disponibilidad son
  referencias iniciales. Antes de considerarlas compromisos, deben confirmarse
  con la empresa y medirse en el entorno previsto.
- La disponibilidad requiere definir horario operativo, ventanas de
  mantenimiento, frecuencia de respaldos y tiempo objetivo de recuperación.
- La integridad depende de validaciones funcionales y de que las operaciones
  relacionadas se guarden de forma consistente.
- La seguridad debe aplicarse tanto a la interfaz como a las operaciones de
  negocio y al acceso a los datos, de acuerdo con los roles definidos.
