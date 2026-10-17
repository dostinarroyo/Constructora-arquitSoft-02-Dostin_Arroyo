# C4 - Nivel 2: contenedores

## Alcance

Se propone una aplicación web central, desplegada como un monolito modular,
que usa una base de datos relacional centralizada. Los nombres tecnológicos
son los previstos en el caso y aún están sujetos a confirmación.

## Diagrama

![Diagrama a color C4 nivel 2, contenedores](../../img/nivel2-contenedores.png)

Fuente Mermaid editable: [nivel2-contenedores.mmd](../../img/fuentes/nivel2-contenedores.mmd).

## Contenedores y responsabilidades

| Contenedor | Tecnología propuesta | Responsabilidad |
|---|---|---|
| Navegador web | HTML, CSS, JavaScript y Bootstrap | Presentar formularios, consultas, panel y reportes para usuarios autorizados. |
| Aplicación de gestión | Java, Spring Boot y Spring Security | Ejecutar los casos de uso, aplicar autorización, coordinar módulos y acceder a datos. |
| Base de datos relacional | MySQL | Mantener datos centralizados y sus relaciones; soportar transacciones consistentes. |

La interfaz se muestra como un contenedor lógico desde la perspectiva del
usuario. No se presupone que tenga un despliegue independiente de la aplicación
Spring Boot. El alojamiento, topología de red, respaldos y dimensionamiento
todavía no están definidos.

## Decisiones y límites

- Un único despliegue inicial evita introducir complejidad de microservicios
  no justificada por el alcance actual.
- No se agregan proveedores externos ni integraciones contables.
- La persistencia centralizada requiere política de respaldo y restauración,
  pendiente de definir.
- Las referencias a HTTPS representan el protocolo esperado en un entorno
  desplegado; todavía no existe configuración de despliegue documentada.
