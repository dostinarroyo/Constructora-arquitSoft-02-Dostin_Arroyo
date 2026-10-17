# Patrones de diseño propuestos

## Criterio

Se proponen patrones solo cuando resuelven una necesidad identificada. Son
opciones de diseño para guiar la implementación, no evidencia de que el
sistema ya los use en código de producción.

## Repository

- **Problema:** los casos de uso necesitan consultar y guardar proyectos,
  materiales, asignaciones y otros registros sin depender de sentencias SQL.
- **Aplicación:** definir contratos como `RepositorioAlmacen` y proporcionar
  adaptadores concretos para pruebas y persistencia.
- **Beneficio:** separa reglas de negocio de la tecnología de almacenamiento y
  facilita probar casos de uso.
- **Riesgo:** no crear interfaces sin una responsabilidad clara ni permitir
  que los repositorios concentren reglas de negocio.
- **Estado:** contrato y adaptadores son una propuesta para el diseño; todavía
  no están implementados.

## Adapter

- **Problema:** los contratos de dominio/aplicación deben conectarse con
  tecnologías concretas, como MySQL y Spring Data, sin exponer esas APIs a las
  reglas.
- **Aplicación:** una implementación de repositorio traduce las operaciones del
  contrato a consultas y transacciones de persistencia.
- **Beneficio:** los detalles de infraestructura permanecen sustituibles y
  fuera del dominio.
- **Riesgo:** evitar adaptadores que oculten errores de persistencia o devuelvan
  valores ficticios para simular éxito.

## Caso de uso / servicio de aplicación

La coordinación de procesos se mantiene en clases de aplicación con una
responsabilidad concreta, por ejemplo `RegistrarSalidaMaterial`. El caso de
uso controla el orden de validación y persistencia; las entidades conservan
las reglas propias de su estado. No se recomienda un servicio único que
concentre todos los procesos de la empresa.

## Patrones no adoptados inicialmente

No se propone usar Factory, Observer, Strategy ni una arquitectura dirigida por
eventos sin una necesidad validada. Podrían considerarse si aparecen
variaciones reales de reglas, notificaciones asíncronas o procesos que lo
justifiquen, manteniendo la solución inicial sencilla.
