# 07 - Decisiones arquitectónicas

## Estado del registro

Este registro documenta las decisiones propuestas para la arquitectura inicial
del sistema de gestión de la empresa constructora. Como el proyecto todavía se
encuentra en fase de análisis, las decisiones marcadas como **Propuesta** no
deben interpretarse como compromisos de implementación hasta que el equipo y
los responsables las validen.

## DA-001: Aplicación web como monolito modular en capas

- **Estado:** Propuesta
- **Contexto:** Los módulos comparten proyectos y datos operativos. El caso no
  define equipos autónomos, escalado independiente ni despliegue distribuido.
- **Decisión:** Organizar una aplicación web como monolito modular, separando
  presentación, aplicación y dominio, acceso a datos y persistencia.
- **Alternativas:** Microservicios; aplicación sin límites modulares.
- **Consecuencias:** Se simplifica el despliegue inicial y se facilita la
  consistencia entre módulos. Se deberán mantener límites internos para evitar
  acoplamiento y reevaluar la decisión si surgen necesidades de distribución.
- **Drivers relacionados:** DA01, DA05, DA07 y DA08.

## DA-002: Persistencia relacional centralizada

- **Estado:** Propuesta
- **Contexto:** Proyectos, actividades, movimientos de almacén, personal,
  maquinaria y gastos deben relacionarse y consultarse de forma coherente.
- **Decisión:** Utilizar una base de datos relacional centralizada; MySQL es la
  tecnología prevista en el caso.
- **Alternativas:** Almacenamiento separado por módulo; base de datos no
  relacional como repositorio principal.
- **Consecuencias:** Las relaciones y transacciones respaldan la integridad de
  los procesos. Será necesario definir respaldos, permisos, migraciones y
  disponibilidad para el entorno de operación.
- **Drivers relacionados:** DA01, DA03, DA06 y DA08.

## DA-003: Autorización por roles en el servidor

- **Estado:** Propuesta
- **Contexto:** Administradores, gerencia, personal de obra y responsables de
  área requieren permisos diferentes.
- **Decisión:** Aplicar autenticación y autorización centralizadas, verificando
  los permisos en las operaciones protegidas del servidor. Spring Security es
  la opción tecnológica prevista.
- **Alternativas:** Controlar el acceso únicamente en la interfaz; implementar
  permisos independientes en cada módulo.
- **Consecuencias:** Las reglas de acceso son coherentes aunque la solicitud no
  provenga de la interfaz esperada. El equipo deberá especificar una matriz de
  roles y permisos y probar accesos permitidos y denegados.
- **Drivers relacionados:** DA02 y DA08.

## DA-004: Sin microservicios ni integraciones externas en la primera etapa

- **Estado:** Propuesta
- **Contexto:** El alcance actual describe módulos internos de gestión y no
  establece requisitos de integración, despliegue por servicio o autonomía
  operativa.
- **Decisión:** Mantener los módulos dentro de la aplicación central y no
  introducir integraciones externas ni microservicios en la propuesta inicial.
- **Alternativas:** Descomponer desde el inicio los módulos en servicios
  desplegables por separado.
- **Consecuencias:** Se reduce la complejidad operativa inicial; a cambio, la
  separación modular debe ser explícita para permitir reevaluar límites si
  cambian las necesidades.
- **Drivers relacionados:** DA01, DA05, DA07 y DA08.

## Revisión de decisiones

Las decisiones deberán revisarse cuando se validen el despliegue, la cantidad
de usuarios, las políticas de seguridad y recuperación, las integraciones
requeridas o las condiciones tecnológicas del equipo. Una revisión debe
actualizar el estado y las consecuencias de la decisión afectada, y mantener
la trazabilidad con los [drivers arquitectónicos](../requisitos/06-drivers-arquitectonicos.md).

## Documentos relacionados

- [Enfoque arquitectónico](./enfoque/README.md)
- [Estilo arquitectónico](./estilo-arquitectonico.md)
- [Arquitectura inicial](./arquitectura-inicial.md)
- [Diagrama de arquitectura inicial](./arquitectura-inicial.drawio)
