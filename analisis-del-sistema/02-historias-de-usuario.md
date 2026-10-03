# 02. Historias de usuario

## Propósito

Las siguientes historias expresan las necesidades de los actores del sistema
desde su perspectiva. Se limitan a las funciones incluidas en el caso de la
empresa constructora y servirán como base para derivar los requisitos
funcionales.

## Historias de usuario

### Gestión de usuarios e información general

#### HU01. Administrar usuarios y roles

**Como** administrador del sistema,
**quiero** registrar, modificar y asignar roles a los usuarios,
**para** controlar el acceso a las funciones de acuerdo con sus
responsabilidades.

**Criterios de aceptación**

- El administrador puede registrar y actualizar usuarios.
- Cada usuario puede tener asignado un rol definido por la empresa.
- Las opciones disponibles para cada usuario corresponden a los permisos de su
  rol.

#### HU02. Consultar un resumen general

**Como** gerente general,
**quiero** consultar un panel con información resumida de la empresa,
**para** conocer el estado general de los proyectos y apoyar la toma de
decisiones.

**Criterios de aceptación**

- El panel presenta información consolidada de los proyectos registrados.
- La información resumida incluye el avance disponible y datos relevantes de
  recursos y gastos.
- Los datos mostrados se obtienen de la información registrada en los módulos
  correspondientes.

### Gestión de proyectos y actividades

#### HU03. Administrar proyectos

**Como** director de proyectos,
**quiero** registrar, modificar y consultar proyectos de construcción,
**para** mantener organizada la información de las obras de la empresa.

**Criterios de aceptación**

- Se puede registrar la información básica de un proyecto.
- Se puede consultar y modificar la información de los proyectos registrados.
- Las actividades, recursos y datos financieros pueden asociarse al proyecto
  correspondiente.

#### HU04. Consultar estado y avance del proyecto

**Como** gerente general o director de proyectos,
**quiero** consultar el estado y el porcentaje de avance de cada proyecto,
**para** hacer seguimiento a la ejecución de las obras.

**Criterios de aceptación**

- Se puede consultar el estado registrado de cada proyecto.
- El avance del proyecto se presenta como porcentaje.
- La información de avance corresponde a las actividades registradas para el
  proyecto.

#### HU05. Registrar actividades de un proyecto

**Como** residente de obra,
**quiero** registrar las actividades correspondientes a cada proyecto,
**para** organizar y dar seguimiento al trabajo planificado en la obra.

**Criterios de aceptación**

- Cada actividad queda asociada a un proyecto registrado.
- Se puede consultar la lista de actividades de un proyecto.
- La información permite distinguir cada actividad y su estado de ejecución.

#### HU06. Actualizar avance de actividades

**Como** residente o ingeniero de obra,
**quiero** actualizar el avance de las actividades,
**para** mantener informado el estado de ejecución de la obra.

**Criterios de aceptación**

- Se puede registrar y actualizar el avance de una actividad.
- El avance actualizado se refleja en la consulta de la actividad y del
  proyecto asociado.
- Solo los usuarios autorizados pueden actualizar la información.

### Gestión de materiales y almacén

#### HU07. Registrar materiales utilizados en proyectos

**Como** encargado de almacén,
**quiero** registrar los materiales utilizados en los proyectos,
**para** identificar los recursos de almacén relacionados con cada obra.

**Criterios de aceptación**

- Se puede registrar la información de los materiales gestionados.
- Los materiales utilizados pueden relacionarse con el proyecto
  correspondiente.
- Los materiales registrados pueden consultarse posteriormente.

#### HU08. Registrar movimientos de almacén

**Como** encargado de almacén,
**quiero** registrar las entradas y salidas de materiales,
**para** mantener actualizado el control del almacén.

**Criterios de aceptación**

- Cada movimiento identifica el material y la cantidad correspondiente.
- El movimiento queda identificado como entrada o salida.
- Las salidas relacionadas con una obra pueden asociarse al proyecto
  correspondiente.

#### HU09. Consultar stock disponible

**Como** encargado de almacén o residente de obra,
**quiero** consultar el stock disponible de los materiales,
**para** conocer su disponibilidad para las necesidades de la obra.

**Criterios de aceptación**

- Se puede consultar la existencia disponible de cada material.
- El stock refleja los movimientos registrados en el almacén.
- La consulta permite identificar materiales con disponibilidad insuficiente
  para su uso planificado.

### Gestión de personal y maquinaria

#### HU10. Administrar información de trabajadores

**Como** responsable de recursos humanos,
**quiero** registrar y actualizar la información de los trabajadores,
**para** mantener organizada la información del personal de la empresa.

**Criterios de aceptación**

- Se puede registrar y consultar la información de los trabajadores.
- Se puede modificar la información registrada cuando corresponda.
- El acceso a los datos está limitado según los permisos del usuario.

#### HU11. Asignar trabajadores a proyectos o actividades

**Como** responsable de recursos humanos o director de proyectos,
**quiero** asignar trabajadores a proyectos o actividades,
**para** identificar el personal asociado a cada obra.

**Criterios de aceptación**

- Una asignación relaciona un trabajador con un proyecto o actividad existente.
- Se puede consultar el personal asignado a cada proyecto o actividad.
- La asignación puede actualizarse por un usuario autorizado.

#### HU12. Registrar maquinaria y equipos

**Como** encargado de maquinaria,
**quiero** registrar la maquinaria y los equipos de la empresa,
**para** mantener un inventario de los recursos disponibles para las obras.

**Criterios de aceptación**

- Se puede registrar y consultar la información de maquinaria y equipos.
- Los registros permiten identificar cada equipo.
- Se puede actualizar la información de los equipos registrados.

#### HU13. Controlar estado y asignación de maquinaria

**Como** encargado de maquinaria,
**quiero** actualizar el estado y la asignación de los equipos,
**para** conocer su disponibilidad y el proyecto en que se utilizan.

**Criterios de aceptación**

- Se puede consultar el estado registrado de cada equipo.
- Se puede asociar un equipo a un proyecto cuando sea asignado.
- Una actualización de estado o asignación queda disponible en las consultas
  del equipo y del proyecto relacionado.

### Gestión financiera y reportes

#### HU14. Registrar presupuesto del proyecto

**Como** responsable de finanzas,
**quiero** registrar el presupuesto asignado a cada proyecto,
**para** disponer de una referencia financiera para el seguimiento de la obra.

**Criterios de aceptación**

- Cada presupuesto queda asociado a un proyecto.
- Se puede consultar y actualizar el presupuesto registrado.
- El presupuesto se presenta junto con la información del proyecto al que
  corresponde.

#### HU15. Registrar y consultar gastos

**Como** responsable de finanzas,
**quiero** registrar y consultar los gastos realizados en cada proyecto,
**para** mantener el seguimiento de los costos de la obra.

**Criterios de aceptación**

- Cada gasto queda asociado al proyecto correspondiente.
- Se puede consultar el historial de gastos registrados para un proyecto.
- El sistema permite comparar los gastos registrados con el presupuesto
  asignado.

#### HU16. Generar reportes de gestión

**Como** gerente general, director de proyectos o responsable de un área,
**quiero** generar reportes de proyectos, materiales, personal, maquinaria y
gastos,
**para** revisar información consolidada que apoye el seguimiento y la toma de
decisiones.

**Criterios de aceptación**

- Se pueden generar reportes de los ámbitos indicados según los permisos del
  usuario.
- Los reportes muestran información registrada en los módulos correspondientes.
- Los datos de cada reporte pueden relacionarse con el proyecto pertinente
  cuando aplique.

## Relación con los requisitos funcionales

Las historias describen necesidades de usuario y no prescriben tecnologías ni
decisiones de arquitectura. En el documento de requisitos funcionales se
desglosarán en comportamientos verificables, manteniendo la trazabilidad
mediante identificadores.
