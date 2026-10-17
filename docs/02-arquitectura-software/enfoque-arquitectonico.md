# Enfoque arquitectónico

## Propósito

Este documento explica el enfoque propuesto para estructurar el sistema de
gestión de la empresa constructora. Complementa la [arquitectura
inicial](./arquitectura-inicial.md) con el razonamiento que guía su forma y
delimita qué aspectos siguen pendientes de confirmación.

## Enfoque propuesto

Se propone una aplicación web centralizada como **monolito modular con
Clean Architecture**. Los usuarios internos acceden desde un navegador a una
aplicación que organiza sus funcionalidades por módulos de negocio y persiste
la información en una base de datos relacional central.

La solución separa cuatro capas:

- **Presentación:** interfaz web y puntos de entrada que reciben solicitudes,
  validan el formato de entrada y presentan resultados.
- **Aplicación:** casos de uso que coordinan operaciones y dependen de
  abstracciones, no de frameworks ni de persistencia concreta.
- **Dominio:** entidades, conceptos y reglas de negocio independientes de la
  aplicación web y de las tecnologías externas.
- **Infraestructura:** adaptadores que implementan los puertos requeridos por
  la aplicación y conectan con tecnologías como Spring, Spring Security y
  MySQL.

La regla de dependencias apunta hacia el núcleo: Presentación depende de
Aplicación; Infraestructura implementa contratos definidos por Aplicación; el
Dominio no depende de las capas externas. Los puertos de persistencia son
propiedad de la capa que los necesita (Aplicación).
Los módulos de negocio —proyectos y actividades, almacén, personal, maquinaria,
finanzas, reportes y usuarios— se organizan dentro de estas capas, no como
capas adicionales.

Los módulos comparten los límites iniciales de despliegue y persistencia. Esta
separación busca reducir el acoplamiento interno sin introducir la complejidad
operativa de distribuir el sistema en servicios independientes.

## Razones para esta propuesta

1. **Cohesión con el alcance:** los procesos comparten proyectos, recursos y
   registros relacionados, por lo que necesitan consistencia y trazabilidad.
2. **Simplicidad operativa:** el caso no establece despliegues independientes,
   equipos separados ni una escala que justifique microservicios.
3. **Mantenibilidad:** las capas y módulos delimitan responsabilidades; la
   regla de dependencias protege las reglas de negocio de los cambios técnicos.
4. **Seguridad coherente:** la autenticación y autorización pueden aplicarse de
   forma transversal a los puntos de entrada y a los casos de uso protegidos.
5. **Evolución gradual:** la solución puede ampliarse mientras se mantengan
   interfaces explícitas y se evite que los módulos dependan de detalles de
   persistencia.

## Límites y supuestos

- Java, Spring Boot, Spring Security, tecnologías web y MySQL son tecnologías
  previstas en el caso; su confirmación final depende del equipo y de las
  condiciones del proyecto.
- No se asumen integraciones externas, acceso directo de clientes, telemetría
  de maquinaria ni servicios desplegados de forma independiente.
- La separación por módulos es lógica. No implica una base de datos o un
  despliegue separado por módulo.
- Los cálculos de avance, inventario y costos deberán especificarse antes de
  implementar sus reglas.
- Requisitos de despliegue, recuperación, auditoría y operación quedan sujetos
  a validación con los responsables.

## Alternativas consideradas

| Alternativa | Evaluación para el alcance actual |
|---|---|
| Monolito modular con Clean Architecture | Propuesta inicial: mantiene una operación sencilla y separa el dominio de los detalles técnicos mediante puertos y adaptadores. |
| Microservicios | No se proponen porque no se han identificado necesidades de despliegue independiente, escalado autónomo o propiedad por equipos distintos. |
| Arquitectura dirigida por eventos | No se propone como base porque el caso no define procesos asíncronos o integraciones que la requieran. |

Estas alternativas podrán revisarse si cambian los requisitos o aparecen
restricciones operativas que lo justifiquen.

## Trazabilidad

El enfoque responde principalmente a los drivers [DA01–DA08](../01-analisis-de-sistema/06-drivers-arquitectonicos.md),
en particular a la integración de proyectos y recursos, la seguridad, la
integridad de la información, la mantenibilidad y el crecimiento funcional.
