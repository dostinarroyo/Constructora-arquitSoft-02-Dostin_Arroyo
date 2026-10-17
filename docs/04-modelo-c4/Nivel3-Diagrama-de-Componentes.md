# C4 - Nivel 3: componentes

## Alcance

El diagrama descompone la aplicación Spring Boot propuesta en controladores,
seguridad, servicios/casos de uso, módulos de dominio y adaptadores de
persistencia. Los componentes comparten un mismo proceso de aplicación; los
módulos no son microservicios.

## Diagrama

![Diagrama a color C4 nivel 3, componentes](../../img/nivel3-componentes.png)

Fuente Mermaid editable: [nivel3-componentes.mmd](../../img/fuentes/nivel3-componentes.mmd).

## Responsabilidades

| Componente | Responsabilidad |
|---|---|
| Controladores web | Recibir solicitudes, validar formato y convertir resultados en respuestas web. |
| Autenticación y autorización | Verificar identidad y permisos en el servidor antes de ejecutar operaciones protegidas. |
| Casos de uso | Coordinar flujos concretos, como registrar proyecto, actualizar avance o registrar salida. |
| Dominio | Representar conceptos y reglas que deben cumplirse con independencia de la interfaz y la base de datos. |
| Contratos de repositorio | Declarar operaciones de lectura y escritura requeridas por casos de uso. |
| Adaptadores de persistencia | Implementar contratos y traducirlos a operaciones transaccionales sobre MySQL. |

## Dependencias

Los casos de uso dependen de contratos; infraestructura los implementa. El
dominio no importa Spring, MySQL ni tipos de transporte HTTP. Los reportes son
consultas sobre datos de origen, no un almacén independiente.

El acceso directo entre módulos debe limitarse a interfaces o consultas
explícitas. La separación por paquetes o tablas no basta por sí sola para
garantizar bajo acoplamiento.
