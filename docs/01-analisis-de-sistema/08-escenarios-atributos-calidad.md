# Escenarios de atributos de calidad

## Propósito

Estos escenarios convierten los atributos de calidad de
[04-atributos-de-calidad.md](./04-atributos-de-calidad.md) en situaciones
observables y verificables. Las metas cuantitativas son propuestas iniciales;
deben validarse con la empresa y con el entorno de prueba antes de tratarlas
como compromisos.

## EQ-01. Seguridad: operaciones según rol

| Elemento | Descripción |
|---|---|
| Atributo | Seguridad |
| Fuente del estímulo | Usuario autenticado o usuario sin sesión. |
| Estímulo | El usuario intenta consultar o modificar información de un módulo para el que no tiene permiso. |
| Artefacto | Operación protegida del servidor y datos del módulo solicitado. |
| Entorno | Pruebas de acceso con cada rol definido y solicitudes autorizadas y no autorizadas. |
| Respuesta esperada | El servidor permite la operación autorizada; rechaza las demás sin modificar datos ni revelar información restringida. |
| Medida | 100 % de los intentos no autorizados incluidos en la matriz de pruebas son rechazados y no producen cambios. |
| Verificación | Ejecutar pruebas por rol sobre endpoints/casos de uso, comprobar códigos de respuesta y verificar que los datos no cambiaron. |
| Estado | Propuesta; falta validar la matriz final de roles y permisos. |

## EQ-02. Rendimiento: consultas de operación

| Elemento | Descripción |
|---|---|
| Atributo | Rendimiento |
| Fuente del estímulo | Gerente general, responsable de proyectos y obras y responsables funcionales del sistema. |
| Estímulo | Consultan proyectos, avance, stock o asignaciones. |
| Artefacto | Casos de uso de consulta, repositorios y base de datos central. |
| Entorno | Carga inicial de hasta 50 usuarios concurrentes y datos representativos de proyectos y recursos. |
| Respuesta esperada | El sistema devuelve resultados correctos sin bloquear otras operaciones ni generar errores técnicos inesperados. |
| Medida | Propuesta: al menos el 95 % de las consultas habituales responde en 3 segundos o menos; reportes consolidados, en 5 segundos o menos. |
| Verificación | Ejecutar una prueba de carga sobre consultas definidas, registrar latencias por percentil, errores y datos usados. |
| Estado | Propuesta por validar; el entorno y volumen de datos de prueba están pendientes. |

## EQ-03. Disponibilidad: continuidad y recuperación

| Elemento | Descripción |
|---|---|
| Atributo | Disponibilidad |
| Fuente del estímulo | Usuario autorizado durante el horario operativo acordado. |
| Estímulo | El usuario necesita consultar o registrar información; también puede ocurrir una falla que requiera recuperar datos. |
| Artefacto | Aplicación web, persistencia centralizada y copias de seguridad. |
| Entorno | Operación mensual, excluyendo mantenimientos planificados acordados. |
| Respuesta esperada | El sistema permite las operaciones disponibles y, ante pérdida de datos, puede restaurar una copia consistente. |
| Medida | Propuesta: 99 % de disponibilidad mensual durante el horario operativo; cada respaldo programado debe poder restaurarse en una prueba documentada. |
| Verificación | Calcular disponibilidad desde registros de monitoreo y ejecutar restauraciones periódicas en un entorno separado, comprobando integridad. |
| Estado | Propuesta por validar; horario, frecuencia de respaldos y objetivos de recuperación no están definidos. |

## EQ-04. Integridad: salida de material

| Elemento | Descripción |
|---|---|
| Atributo | Integridad de la información |
| Fuente del estímulo | Responsable de almacén. |
| Estímulo | Registra la salida de una cantidad de material para un proyecto. |
| Artefacto | Caso de uso de salida, existencias, movimiento de almacén y proyecto relacionado. |
| Entorno | Operación normal con material y proyecto previamente registrados; puede haber solicitudes inválidas o concurrentes. |
| Respuesta esperada | Se valida la cantidad y la relación con el proyecto; existencias y movimiento se guardan juntos. Si la operación no es válida, no se modifica ninguno. |
| Medida | Ninguna salida confirmada deja stock negativo ni queda sin movimiento asociado; una operación rechazada no altera los datos. |
| Verificación | Probar salida válida, cantidad no positiva, stock insuficiente y fallo durante la persistencia; consultar stock e historial después de cada caso. |
| Estado | Regla propuesta a detallar con la política real de almacén y transacciones de la base de datos. |

## EQ-05. Usabilidad: registro de avance de actividad

| Elemento | Descripción |
|---|---|
| Atributo | Usabilidad |
| Fuente del estímulo | Responsable de proyectos y obras. |
| Estímulo | Registra el avance de una actividad asociada a una obra. |
| Artefacto | Formulario de avance y flujo de validación de la actividad. |
| Entorno | Prueba de tareas frecuentes con usuarios representativos y datos de capacitación. |
| Respuesta esperada | El usuario identifica el proyecto y la actividad, registra el avance y recibe una confirmación o errores accionables. |
| Medida | Propuesta: al menos el 90 % de participantes completa la tarea sin asistencia y sin errores que alteren datos. |
| Verificación | Observar una prueba de usabilidad, registrar éxito, asistencia, errores y tiempo por participante. |
| Estado | Propuesta por validar; deben seleccionarse participantes y tareas representativas. |

## EQ-06. Mantenibilidad: cambio aislado en un módulo

| Elemento | Descripción |
|---|---|
| Atributo | Mantenibilidad |
| Fuente del estímulo | Equipo de desarrollo. |
| Estímulo | Se modifica una regla de negocio del módulo de almacén. |
| Artefacto | Dominio, caso de uso y adaptador de persistencia del módulo. |
| Entorno | Código organizado por módulos y capas, con pruebas automatizadas. |
| Respuesta esperada | El cambio se realiza en la responsabilidad correspondiente y los demás módulos no dependen de detalles nuevos de almacén. |
| Medida | Todas las pruebas del módulo y de regresión definidas para el cambio pasan; la regla de dependencias entre capas se conserva. |
| Verificación | Revisar el cambio, ejecutar pruebas y analizar las dependencias de los módulos afectados. |
| Estado | Propuesta; falta definir la estrategia y cobertura objetivo de pruebas. |

## EQ-07. Escalabilidad: crecimiento de usuarios y registros

| Elemento | Descripción |
|---|---|
| Atributo | Escalabilidad |
| Fuente del estímulo | Incremento del uso del sistema a medida que se incorporan obras y usuarios. |
| Estímulo | Aumentan las solicitudes concurrentes y el volumen de proyectos, movimientos y asignaciones. |
| Artefacto | Aplicación modular, consultas y base de datos centralizada. |
| Entorno | Prueba con un conjunto de datos representativo y carga superior a la carga inicial acordada. |
| Respuesta esperada | El sistema conserva la integridad y los umbrales de respuesta acordados; los cuellos de botella pueden identificarse sin reescribir todos los módulos. |
| Medida | Propuesta: comparar 50 y 100 usuarios concurrentes; mantener el p95 de consultas habituales en 3 segundos o menos y errores técnicos por debajo del 1 %. Volumen de datos por definir. |
| Verificación | Aumentar la carga gradualmente, registrar latencia, errores y consumo de recursos; documentar el punto en que deja de cumplir los umbrales. |
| Estado | Propuesta exploratoria, no compromiso; validar usuarios y volumen de datos con la empresa. |

## Trazabilidad

| Escenario | Atributo | Requisitos relacionados | Driver |
|---|---|---|---|
| EQ-01 | Seguridad | RF16 | DA02 |
| EQ-02 | Rendimiento | RF02, RF07, RF09, RF14, RF15 | DA04 |
| EQ-03 | Disponibilidad | RF01–RF16 | DA06 |
| EQ-04 | Integridad | RF04–RF07, RF09, RF11–RF13 | DA03 |
| EQ-05 | Usabilidad | RF03–RF09 | DA01 |
| EQ-06 | Mantenibilidad | RF01–RF16 | DA05 |
| EQ-07 | Escalabilidad | RF01–RF16 | DA07 |
