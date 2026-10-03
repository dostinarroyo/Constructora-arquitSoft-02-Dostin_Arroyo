# 01. Actores del sistema

## Introducción

El sistema de gestión para una empresa constructora debe soportar la operación
integral de una organización que administra proyectos, recursos, tiempos,
materiales y personal en distintos frentes de obra. Por esta razón, los actores
que intervienen en el sistema no son únicamente usuarios de una plataforma, sino
responsables funcionales con necesidades específicas de información, control y
seguimiento.

La identificación de los actores es necesaria para definir los permisos de acceso,
las funcionalidades del sistema y la estructura de la información. Cada rol
cumple responsabilidades distintas dentro del ciclo de vida del proyecto, desde
la planificación hasta la entrega final y la supervisión financiera.

## Actores del sistema

| Actor | Tipo | Responsabilidad principal | Relación con el sistema |
|---|---|---|---|
| Administrador del sistema | Interno | Configurar usuarios, permisos, parámetros del sistema y mantenimiento general. | Gestiona accesos y seguridad del sistema. |
| Gerente general | Interno | Definir objetivos, supervisar desempeño general y tomar decisiones estratégicas. | Consulta indicadores, avances, costos y reportes consolidados. |
| Director de proyectos | Interno | Coordinar la ejecución de los proyectos y asegurar cumplimiento de metas, tiempos y presupuestos. | Revisa proyectos, actividades, avances y reportes operativos. |
| Residente / jefe de obra | Interno | Supervisar la ejecución física de la obra, coordinar actividades y controlar recursos en campo. | Registra avances, asigna tareas y gestiona recursos de obra. |
| Ingeniero de obra | Interno | Planificar, controlar y verificar la ejecución técnica de las actividades. | Actualiza avances, revisa especificaciones, coordina cambios y controla calidad. |
| Encargado de almacén | Interno | Controlar materiales, entradas, salidas, inventario y disponibilidad en almacén. | Registra movimientos, realiza consultas de stock y gestiona materiales por proyecto. |
| Supervisor de actividades | Interno | Asegurar cumplimiento de las tareas programadas y el seguimiento de ejecuciones. | Consulta cronogramas, actualiza estados y reporta retrasos. |
| Personal administrativo | Interno | Dar soporte operativo y registrar información documental y de gestión. | Gestiona registros de proyectos, reportes y coordinación entre áreas. |
| Personal de obra / operarios | Interno | Ejecutar tareas específicas según la programación de obra y su asignación por proyecto. | Puede aportar información sobre las actividades ejecutadas, según los permisos definidos por la empresa. |
| Recursos humanos | Interno | Administrar la información de los trabajadores y sus asignaciones. | Gestiona los datos del personal y su relación con los proyectos. |
| Encargado de maquinaria | Interno | Administrar la disponibilidad y asignación de maquinaria y equipos. | Registra equipos y controla su estado y asignación. |
| Analista o encargado de finanzas | Interno | Controlar presupuestos y gastos asociados a cada obra. | Registra y consulta información financiera de los proyectos. |
| Cliente o propietario del proyecto | Interesado externo | Conocer el estado y cumplimiento general de la obra contratada. | No se considera usuario directo en el alcance inicial; puede recibir información mediante los responsables de la empresa. |
| Auditor o revisor | Interesado interno o externo | Revisar la información y los reportes de gestión cuando corresponda. | No se define acceso directo en el alcance inicial. |

## Descripción de los actores más relevantes

### 1. Administrador del sistema
El administrador del sistema es el responsable de la configuración técnica y
organizacional del software. Su función principal es administrar usuarios,
roles, permisos y parámetros generales del sistema. Además, supervisa la
integridad de la información y coordina la resolución de incidentes relacionados
con la operación del sistema.

Este actor es clave para la seguridad del sistema, ya que define qué usuarios
pueden consultar, registrar, modificar o aprobar información en cada módulo.

### 2. Gerente general
El gerente general representa la alta dirección de la empresa y requiere una
visión global del estado de la organización. Debe contar con indicadores que le
permitan evaluar la ejecución de varios proyectos simultáneamente y tomar
decisiones estratégicas con base en información actualizada.

Su interés se centra en la rentabilidad, el avance de obras, la utilización de
recursos y la identificación temprana de desviaciones o riesgos.

### 3. Director de proyectos
El director de proyectos supervisa la ejecución de las obras y coordina los
recursos necesarios para cumplir cronogramas y objetivos. Este actor requiere
información detallada sobre el progreso general de cada proyecto, los indicadores
de cumplimiento, los costos y las actividades críticas.

Es responsable de asegurar la alineación entre la programación, la ejecución y
la disponibilidad de recursos humanos, materiales y maquinaria.

### 4. Residente o jefe de obra
El residente de obra es el responsable directo de la ejecución física de la obra.
Su papel es fundamental porque debe coordinar la operación diaria del proyecto,
registrar el avance real de las actividades y detectar retrasos o anomalías.

Este actor interactúa directamente con el sistema para registrar avances de
actividades, controlar el uso de materiales y reportar incidencias que afecten
la programación del proyecto.

### 5. Ingeniero de obra
El ingeniero de obra apoya la planificación técnica y la verificación de la
calidad constructiva. Mantiene relación con el avance físico, la coordinación de
actividades y la revisión de cumplimiento de especificaciones técnicas.

Usa el sistema para registrar avances, conocer la programación del proyecto,
identificar problemas técnicos y apoyar la toma de decisiones relacionadas con
la ejecución de la obra.

### 6. Encargado de almacén
El encargado de almacén administra los materiales y recursos físicos
disponibles para la obra. Este actor requiere información precisa sobre stock,
entradas y salidas, pérdidas y consumo de materiales por cada proyecto.

Su trabajo es crítico porque influye directamente en la continuidad de la obra,
la planificación de compras y la reducción de desperdicios o faltantes.

### 7. Personal de obra y operarios
El personal de obra ejecuta las tareas asignadas en cada proyecto. Puede aportar
información sobre las actividades realizadas si la empresa habilita su
participación directa en el sistema; el alcance inicial no define el registro de
asistencia.

Aunque no siempre tiene responsabilidades administrativas, su participación es
importante para mantener la trazabilidad del trabajo realizado en el campo.

### 8. Recursos humanos
El área de recursos humanos gestiona la información del personal de la empresa
y las asignaciones relacionadas con los proyectos.

Su relación con el sistema se centra en la administración de trabajadores y su
asignación a proyectos o actividades.

### 9. Encargado de maquinaria
Este actor administra la maquinaria y los equipos de la empresa, manteniendo
registrada su disponibilidad y asignación a las obras.

Debe mantener actualizado el estado de los equipos y su asignación según las
necesidades de los proyectos.

### 10. Responsable de finanzas
El responsable financiero registra y consulta los presupuestos y gastos
asociados a los proyectos. Su trabajo es clave para mantener visibilidad sobre
el estado económico de cada obra.

El sistema debe permitirle consultar el estado financiero por obra y generar
reportes para la toma de decisiones.

## Relación entre actores y módulos del sistema

Los actores internos descritos interactúan con distintos módulos del sistema de
gestión. Los clientes y auditores se consideran interesados, pero el alcance
inicial no establece cuentas ni acceso directo para ellos:

- Gestión de proyectos: gerente general, director de proyectos, residente de
  obra, ingeniero de obra.
- Gestión de actividades: residente de obra, ingeniero de obra, supervisor,
  personal de obra.
- Gestión de materiales y almacén: encargado de almacén, residente, director de
  proyectos.
- Gestión de personal: recursos humanos, residente, director de proyectos.
- Gestión de maquinaria: encargado de maquinaria, residente de obra, director de
  proyectos.
- Gestión financiera: analista de finanzas, gerente general, director de
  proyectos.
- Gestión de usuarios y roles: administrador del sistema.
- Generación de reportes: todas las áreas, especialmente gerencia, finanzas y
  dirección de proyectos.

## Conclusión

Los actores del sistema corresponden a los distintos roles presentes en una
empresa constructora y representan las necesidades reales de gestión de
proyectos, recursos e información. La correcta identificación de estos actores
permite diseñar un sistema con permisos adecuados, procesos bien definidos y
reportes útiles para cada nivel de la organización.

En este contexto, la arquitectura del sistema debe facilitar la colaboración
entre áreas, asegurar la trazabilidad de la información y apoyar la toma de
decisiones con datos confiables y oportunos.
