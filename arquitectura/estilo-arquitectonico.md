# Estilo arquitectónico

## Estilo propuesto

El sistema se propone como un **monolito modular organizado en capas**. Es una
aplicación web desplegable como una unidad, cuyos módulos de dominio mantienen
responsabilidades diferenciadas y se apoyan en capas con límites explícitos.
Esta es una propuesta inicial, no una decisión de implementación irreversible.

## Capas

| Capa | Responsabilidad | Evita |
|---|---|---|
| Presentación | Exponer la interfaz web, recibir solicitudes y presentar resultados. | Contener reglas de negocio o acceder directamente a la base de datos. |
| Aplicación y dominio | Coordinar casos de uso, validar reglas y controlar operaciones relacionadas. | Depender de la tecnología concreta de interfaz o persistencia. |
| Acceso a datos | Implementar consultas y persistencia mediante repositorios o adaptadores. | Definir reglas funcionales propias de los módulos. |
| Persistencia | Conservar información relacional centralizada y sus relaciones. | Ser accedida directamente desde la presentación. |

La dirección de dependencias debe apuntar hacia las reglas de aplicación y
dominio: la presentación invoca casos de uso y estos utilizan abstracciones de
acceso a datos. Los detalles de persistencia no deben dictar las reglas del
negocio.

## Módulos de negocio

- **Proyectos y actividades:** datos de proyectos, actividades y avance.
- **Materiales y almacén:** catálogo, movimientos y consulta de existencias.
- **Personal:** trabajadores y asignaciones.
- **Maquinaria:** equipos, estado y asignación.
- **Finanzas:** presupuestos y gastos asociados a proyectos.
- **Reportes e información general:** consultas consolidadas y panel principal.
- **Usuarios y roles:** cuentas, autenticación y permisos.

Los módulos deben colaborar a través de servicios o interfaces definidos.
Cuando una operación abarque datos relacionados, la capa de aplicación debe
coordinarla para conservar la integridad. No se presupone una separación física
de bases de datos.

## Mecanismos transversales

- **Autenticación y autorización:** validar la identidad y los permisos de cada
  operación protegida; ocultar una opción en la interfaz no sustituye la
  autorización del lado servidor.
- **Validación e integridad:** comprobar datos obligatorios, relaciones y reglas
  de dominio antes de persistir cambios.
- **Manejo de errores:** comunicar fallos de forma comprensible sin exponer
  detalles internos ni aparentar que una operación fallida tuvo éxito.
- **Observabilidad y recuperación:** definir registros operativos y respaldos
  verificables al concretar el entorno de despliegue.

## Correspondencia tecnológica prevista

La propuesta del caso contempla Java y Spring Boot para la aplicación y los
servicios, Spring Security para el control de acceso, tecnologías web para la
presentación y MySQL para la persistencia. Estas tecnologías son compatibles
con el estilo propuesto, pero deben confirmarse antes de considerarse
restricciones definitivas.

## Consecuencias y riesgos

**Beneficios esperados**

- Despliegue y operación iniciales más sencillos que una solución distribuida.
- Límites de responsabilidad claros para los módulos y las capas.
- Consistencia transaccional más directa para procesos que relacionan varios
  registros.

**Riesgos a controlar**

- Un monolito puede convertirse en una estructura acoplada si los módulos
  comparten lógica o acceden entre sí sin interfaces.
- El crecimiento puede aumentar el impacto de despliegues coordinados.
- La concentración en una base de datos requiere respaldos, control de acceso y
  gestión cuidadosa de cambios de esquema.

Se deberá reconsiderar la distribución física si aparecen requisitos medibles
de escalado independiente, autonomía de equipos o disponibilidad por módulo.

## Referencias

- [Enfoque arquitectónico](./enfoque/README.md)
- [Arquitectura inicial](./arquitectura-inicial.md)
- [Drivers arquitectónicos](../requisitos/06-drivers-arquitectonicos.md)
