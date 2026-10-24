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
| Administrador del sistema | Interno | Configurar usuarios, permisos, parámetros del sistema y mantenimiento general. | Gestiona accesos, seguridad y configuración del sistema. |
| Gerente general | Interno | Definir objetivos, supervisar el desempeño general y apoyar la toma de decisiones estratégicas. | Consulta indicadores, avances, costos y reportes consolidados. |
| Responsable de proyectos y obras | Interno | Coordinar la ejecución de proyectos y actividades, y asegurar cumplimiento de metas, tiempos y recursos. | Gestiona proyectos, actividades, avances y coordinación operativa. |
| Responsable de almacén | Interno | Administrar materiales, entradas, salidas e inventario del almacén. | Registra movimientos, consulta stock y controla disponibilidad de materiales. |
| Responsable de personal | Interno | Administrar trabajadores y sus asignaciones a proyectos y actividades. | Registra personal y gestiona asignaciones y disponibilidad del recurso humano. |
| Responsable financiero | Interno | Registrar presupuestos, gastos y consultar información financiera de los proyectos. | Registra y revisa costos, presupuestos y reportes financieros. |

## Descripción de los actores

### 1. Administrador del sistema
El administrador del sistema es responsable de la configuración técnica y
organizacional del software. Su función principal es administrar usuarios,
roles, permisos y parámetros generales del sistema. También supervisa la
integridad de la información y coordina la resolución de incidentes relacionados
con la operación del sistema.

Este actor es clave para la seguridad del sistema, ya que define qué usuarios
pueden consultar, registrar, modificar o aprobar información en cada módulo.

### 2. Gerente general
El gerente general representa la alta dirección de la empresa y requiere una
visión global del estado de la organización. Debe contar con indicadores que le
permitan evaluar la ejecución de varios proyectos simultáneamente y apoyar la
toma de decisiones estratégicas con base en información actualizada.

Su interés se centra en la rentabilidad, el avance de obras, la utilización de
recursos y la detección temprana de desviaciones o riesgos.

### 3. Responsable de proyectos y obras
El responsable de proyectos y obras coordina la ejecución de las obras y la
asignación de recursos necesarios para cumplir cronogramas y objetivos. Este
actor requiere información detallada sobre el progreso general de cada proyecto,
los indicadores de cumplimiento, los costos y las actividades críticas.

Es responsable de asegurar la alineación entre la programación, la ejecución y
la disponibilidad de recursos humanos, materiales y maquinaria.

### 4. Responsable de almacén
El responsable de almacén administra los materiales y recursos físicos
disponibles para la obra. Este actor requiere información precisa sobre stock,
entradas, salidas, pérdidas y consumo de materiales por cada proyecto.

Su trabajo es crítico porque influye directamente en la continuidad de la obra,
la planificación de compras y la reducción de desperdicios o faltantes.

### 5. Responsable de personal
El responsable de personal gestiona la información del recurso humano de la
empresa y sus asignaciones a los proyectos y actividades.

Su relación con el sistema se centra en la administración de trabajadores, su
asignación a proyectos o actividades y la consulta de disponibilidad del personal.

### 6. Responsable financiero
El responsable financiero registra y consulta los presupuestos y gastos
asociados a los proyectos. Su trabajo es clave para mantener visibilidad sobre
el estado económico de cada obra.

El sistema debe permitirle consultar el estado financiero por obra y generar
reportes para la toma de decisiones.

## Relación entre actores y módulos del sistema

Los actores internos descritos interactúan con distintos módulos del sistema de
gestión:

- Gestión de proyectos: gerente general, responsable de proyectos y obras.
- Gestión de actividades: responsable de proyectos y obras.
- Gestión de materiales y almacén: responsable de almacén, responsable de proyectos y obras.
- Gestión de personal: responsable de personal, responsable de proyectos y obras.
- Gestión de maquinaria: responsable de proyectos y obras.
- Gestión financiera: responsable financiero, gerente general.
- Gestión de usuarios y roles: administrador del sistema.
- Generación de reportes: gerente general, responsable de proyectos y obras, responsable financiero y responsable de almacén.

## Conclusión

Los seis actores definidos representan los roles principales de la empresa
constructora y reflejan las responsabilidades reales de gestión de proyectos,
recursos e información. La correcta identificación de estos actores permite
diseñar un sistema con permisos adecuados, procesos bien definidos y reportes
útiles para cada nivel de la organización.

En este contexto, la arquitectura del sistema debe facilitar la colaboración
entre áreas, asegurar la trazabilidad de la información y apoyar la toma de
decisiones con datos confiables y oportunos.
