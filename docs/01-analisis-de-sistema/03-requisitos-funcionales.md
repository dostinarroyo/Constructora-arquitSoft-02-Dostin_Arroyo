# 03. Requisitos funcionales

## Propósito y alcance

Los requisitos funcionales describen las capacidades que debe ofrecer el
sistema de gestión para la empresa constructora. Se derivan de las historias de
usuario de [02. Historias de usuario](./02-historias-de-usuario.md) y se
mantienen dentro del alcance del caso: proyectos, actividades, almacén,
personal, maquinaria, finanzas, reportes, panel informativo y usuarios con
roles.

## Requisitos

| Código | Módulo | Requisito funcional | Actor principal | Historia relacionada |
|---|---|---|---|---|
| RF01 | Proyectos | El sistema deberá permitir registrar, modificar y consultar proyectos de construcción. | Responsable de proyectos y obras | HU03 |
| RF02 | Proyectos | El sistema deberá permitir consultar el estado y el porcentaje de avance de cada proyecto. | Gerente general, responsable de proyectos y obras | HU04 |
| RF03 | Actividades | El sistema deberá permitir registrar y consultar las actividades asociadas a cada proyecto. | Responsable de proyectos y obras | HU05 |
| RF04 | Actividades | El sistema deberá permitir registrar y actualizar el avance de las actividades de una obra. | Responsable de proyectos y obras | HU06 |
| RF05 | Materiales y almacén | El sistema deberá permitir registrar materiales y relacionarlos con los proyectos en que se utilizan. | Responsable de almacén | HU07 |
| RF06 | Materiales y almacén | El sistema deberá permitir registrar las entradas y salidas de materiales del almacén. | Responsable de almacén | HU08 |
| RF07 | Materiales y almacén | El sistema deberá permitir consultar el stock disponible de cada material considerando los movimientos registrados. | Responsable de almacén | HU09 |
| RF08 | Personal | El sistema deberá permitir registrar, modificar y consultar la información de los trabajadores. | Responsable de personal | HU10 |
| RF09 | Personal | El sistema deberá permitir asignar trabajadores a proyectos o actividades y consultar dichas asignaciones. | Responsable de personal, responsable de proyectos y obras | HU11 |
| RF10 | Maquinaria | El sistema deberá permitir registrar, modificar y consultar la maquinaria y los equipos de la empresa. | Responsable de proyectos y obras | HU12 |
| RF11 | Maquinaria | El sistema deberá permitir consultar y actualizar el estado y la asignación de la maquinaria y los equipos. | Responsable de proyectos y obras | HU13 |
| RF12 | Finanzas | El sistema deberá permitir registrar, modificar y consultar el presupuesto asignado a cada proyecto. | Responsable financiero | HU14 |
| RF13 | Finanzas | El sistema deberá permitir registrar y consultar los gastos asociados a cada proyecto. | Responsable financiero | HU15 |
| RF14 | Reportes | El sistema deberá permitir generar reportes de proyectos, materiales, personal, maquinaria y gastos. | Gerencia y responsables del sistema | HU16 |
| RF15 | Información general | El sistema deberá mostrar un panel principal con información resumida de la empresa y sus proyectos, según los datos disponibles. | Gerente general | HU02 |
| RF16 | Usuarios y roles | El sistema deberá permitir administrar usuarios y asignarles roles de acceso. | Administrador del sistema | HU01 |

## Criterios generales de aplicación

- Las operaciones de registro, modificación y consulta deberán estar
  disponibles únicamente para usuarios con permisos acordes a sus roles.
- Los datos que pertenezcan a una obra deberán poder relacionarse con el
  proyecto correspondiente.
- Las consultas de avance, stock, asignaciones y gastos deberán basarse en la
  información registrada en sus respectivos módulos.
- Los reportes y el panel principal presentarán información que ya se gestione
  en el sistema; no implican integración con plataformas externas.

## Trazabilidad

Cada requisito se relaciona con una historia de usuario identificada en el
documento anterior. Esta correspondencia permite rastrear la necesidad que
origina cada capacidad del sistema y servirá para revisar su cobertura en los
documentos de calidad y arquitectura.
