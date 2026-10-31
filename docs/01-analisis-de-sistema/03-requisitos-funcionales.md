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
| RF12 | Finanzas | El sistema deberá permitir registrar el presupuesto de un proyecto y conservar cada modificación como una nueva versión inmutable que no pueda modificarse ni eliminarse, identificada con número consecutivo, monto, fecha, usuario que la registra y motivo del cambio. Cada proyecto deberá tener como máximo una versión vigente; el sistema permitirá consultar la versión vigente y el historial. | Responsable financiero | HU14 |
| RF13 | Finanzas | El sistema deberá permitir registrar y consultar los gastos asociados a cada proyecto. | Responsable financiero | HU15 |
| RF14 | Reportes | El sistema deberá permitir consultar y generar reportes de proyectos, materiales, personal, maquinaria y finanzas de acuerdo con la matriz de permisos definida en este documento. | Gerente general y responsables de proyectos, almacén, personal y finanzas, según el reporte | HU16 |
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
- La autorización se valida en el servidor para cada consulta y generación de
  reportes. Administrar usuarios y roles no concede acceso implícito a los
  reportes del negocio.

## Permisos de consulta de reportes (RF14)

| Tipo de reporte | Gerente general | Responsable de proyectos y obras | Responsable de almacén | Responsable de personal | Responsable financiero | Administrador del sistema |
|---|---|---|---|---|---|---|
| Proyectos, actividades y avance | Sí, consolidado | Sí | No | No | Sí, para seguimiento financiero del proyecto | No |
| Materiales, existencias y movimientos | Sí, consolidado | Sí, para coordinación de obra | Sí | No | Sí, para revisión de costos por proyecto | No |
| Trabajadores y asignaciones | Sí, agregado y sin datos personales individuales | Sí, para coordinación de obra | No | Sí | No | No |
| Maquinaria, estado y asignaciones | Sí, consolidado | Sí | No | No | No | No |
| Presupuestos, gastos e historial de versiones | Sí, consolidado | Sí, resumen por proyecto | No | No | Sí, detalle e historial | No |

La matriz concede solo consulta/generación de reportes, no permisos para
registrar o modificar los datos de origen. Los permisos de escritura siguen
siendo los definidos para cada módulo. El administrador del sistema conserva
sus funciones de gestión de usuarios y roles, sin acceso automático a
información operativa o financiera. La matriz constituye la política inicial
propuesta; cualquier cambio deberá reflejarse también en la configuración de
roles y en las pruebas de autorización.

## Trazabilidad

Cada requisito se relaciona con una historia de usuario identificada en el
documento anterior. Esta correspondencia permite rastrear la necesidad que
origina cada capacidad del sistema y servirá para revisar su cobertura en los
documentos de calidad y arquitectura.
