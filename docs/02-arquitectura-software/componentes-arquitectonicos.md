# Componentes arquitectónicos

## Propósito y alcance

Este documento descompone la propuesta de arquitectura inicial en
responsabilidades que colaboran dentro de una sola aplicación web. El diagrama
es una vista lógica editable en Mermaid; no representa una infraestructura ya
desplegada.

## Vista de componentes

![Diagrama a color de componentes arquitectónicos](../../img/arquitectura-componentes.png)

Fuente Mermaid editable: [arquitectura-componentes.mmd](../../img/fuentes/arquitectura-componentes.mmd).

## Responsabilidades y límites

| Capa | Componentes | Responsabilidad | No debe |
|---|---|---|---|
| Presentación | Interfaz web y controladores | Capturar solicitudes, validar su formato y comunicar resultados y errores. | Ser la única barrera de autorización, implementar reglas de negocio o acceder directamente a MySQL. |
| Aplicación | Casos de uso y puertos de entrada/salida | Coordinar operaciones de proyectos, almacén, personal, maquinaria, finanzas, reportes y usuarios; declarar contratos requeridos. | Depender de frameworks, transporte web o adaptadores concretos. |
| Dominio | Entidades, objetos de valor y servicios/reglas de dominio | Proteger invariantes como la validez de movimientos y relaciones del negocio. | Depender de las otras capas o contener detalles técnicos. |
| Infraestructura | Adaptadores de repositorio, Spring Security y MySQL | Implementar los puertos y conectar con persistencia y mecanismos técnicos externos. | Ser dueña de las reglas del negocio o filtrar sus detalles hacia el Dominio. |

## Colaboración de ejemplo: registrar una salida de almacén

1. El responsable de almacén solicita registrar una salida para un proyecto.
2. El punto de entrada protegido verifica que el usuario tenga permiso; el
   caso de uso aplica las políticas que le correspondan.
3. El caso de uso coordina la validación de cantidad, material, proyecto y
   stock con las reglas del Dominio.
4. El caso de uso invoca un puerto de persistencia; el adaptador de
   Infraestructura guarda el movimiento y actualiza las existencias en una
   transacción.
5. La interfaz muestra la confirmación solo si la persistencia termina con
   éxito; ante un error, informa el fallo y no presenta una salida como
   confirmada.

Las reglas detalladas para anulación de movimientos, reservas, múltiples
almacenes o concurrencia deben acordarse antes de implementar el flujo real.

## Reglas de dependencia

- Presentación depende de los casos de uso, no de consultas SQL ni de MySQL.
- Aplicación depende del Dominio y declara los puertos que necesita.
- Infraestructura implementa esos puertos; Aplicación no conoce sus
  implementaciones concretas.
- Las dependencias de código apuntan hacia adentro, aunque el flujo de
  ejecución pueda llegar desde un caso de uso a un adaptador.
- Los módulos comparten identificadores y contratos explícitos; no deben
  invocar directamente detalles internos de otros módulos.
- La autorización se aplica en el servidor para todas las operaciones
  protegidas.

## Trazabilidad

La vista responde a los drivers DA01–DA08 y a las decisiones DA-001–DA-004.
Los módulos corresponden al alcance de RF01–RF16; el flujo de almacén se
relaciona especialmente con RF05–RF07 y AC04.
