# Necesidad del negocio

## Contexto

La empresa constructora debe coordinar varios proyectos y relacionar con cada
obra sus actividades, materiales, trabajadores, maquinaria, presupuestos y
gastos. Gerencia y responsables de área necesitan consultar información
consistente para dar seguimiento a la ejecución y a los recursos.

## Necesidad identificada

El caso de estudio plantea centralizar la gestión de la empresa para reducir
la dispersión de registros y facilitar la consulta de información relacionada
con cada proyecto. La propuesta no parte de mediciones cuantitativas de la
operación actual; el volumen de registros, los tiempos de gestión y el impacto
de la situación deben confirmarse con la empresa.

## Problema que se busca resolver

Cuando la información de proyectos y recursos se administra en registros
separados, resulta difícil obtener una visión conjunta del avance de obra, las
existencias de materiales, las asignaciones de personal y maquinaria y los
gastos asociados. El sistema propuesto busca proporcionar un punto común de
registro y consulta, manteniendo la relación de esos datos con sus proyectos.

Esta formulación expresa el problema del caso académico y no afirma que se
haya realizado un diagnóstico de campo ni que se hayan medido pérdidas,
retrasos o errores.

## Objetivo del sistema

Proponer un sistema web de gestión que permita centralizar y relacionar la
información operativa y administrativa de la constructora, aplicar permisos
según las responsabilidades de sus usuarios y ofrecer consultas y reportes
basados en los datos registrados.

## Alcance inicial

- Gestión de proyectos, actividades y avance.
- Registro de materiales, movimientos de almacén y consulta de existencias.
- Gestión de trabajadores y asignaciones.
- Gestión de maquinaria, estado y asignación.
- Registro de presupuestos y gastos por proyecto.
- Panel, reportes y administración de usuarios y roles.

El alcance se detalla en [03-requisitos-funcionales.md](./03-requisitos-funcionales.md)
y sus límites en [05-restricciones.md](./05-restricciones.md).

## Interesados principales

Gerencia general, dirección de proyectos, personal de obra, almacén, recursos
humanos, responsables de maquinaria y finanzas, además del administrador del
sistema. Sus responsabilidades se describen en [01-actores.md](./01-actores.md).

## Supuestos pendientes de validación

- Los responsables confirmarán los procesos actuales y las reglas de negocio
  de cada área.
- Las metas de calidad, el volumen de usuarios y el despliegue se definirán
  con datos del entorno previsto.
- Java, Spring Boot, Spring Security, las tecnologías web propuestas y MySQL
  son opciones del caso que deben confirmarse.
- La solución no incluye inicialmente contabilidad externa, telemetría de
  maquinaria ni acceso directo de clientes.
