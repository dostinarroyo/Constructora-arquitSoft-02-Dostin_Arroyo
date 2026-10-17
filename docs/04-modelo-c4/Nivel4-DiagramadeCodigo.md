# Nivel 4 · Diagrama de código

> **Proyecto:** Sistema de gestión de una empresa constructora<br>
> **Módulo detallado:** Materiales y almacén<br>
> **Modelo:** C4 · Nivel 4 de 4 · **Notación:** UML / Mermaid · **Versión:** 1.0

---

## 1. Objetivo

Mostrar las clases, contratos y colaboraciones propuestos para el caso de uso
**Registrar salida de material**. Este nivel es opcional en C4 y se enfoca aquí
en almacén porque el flujo relaciona reglas de negocio, stock y persistencia
transaccional. Los diagramas son un diseño, no código implementado.

| Aspecto | Descripción |
|---|---|
| Pregunta que responde | ¿Qué clases e interfaces participan en el caso de uso y cómo colaboran? |
| Audiencia | Desarrolladores y responsables del diseño detallado. |
| Nivel anterior | [Nivel 3 · Componentes](./Nivel3-Diagrama-de-Componentes.md). |
| Caso de uso | Registrar una salida de material asociada a un proyecto. |

## 2. Diagrama de clases

![Diagrama de clases del caso de uso de salida de almacén](../../img/nivel4-clases.png)

Fuente Mermaid editable: [nivel4-clases.mmd](../../img/fuentes/nivel4-clases.mmd).

## 3. Capas de Clean Architecture

| Capa | Contiene | Regla |
|---|---|---|
| Presentación | `SalidaMaterialController` | Traduce la solicitud de entrada y presenta el resultado del caso de uso. |
| Aplicación | `RegistrarSalidaMaterial`, `SolicitudSalida`, `ResultadoSalida` y `RepositorioAlmacen` | Coordina el flujo y declara el puerto que necesita; no conoce la implementación concreta. |
| Dominio | `Material`, `MovimientoAlmacen`, `TipoMovimiento` y reglas de stock | Protege invariantes de negocio sin depender de las otras capas ni de frameworks. |
| Infraestructura | Adaptador de almacén y MySQL | Implementa el puerto de Aplicación y persiste el movimiento y el stock. |

**Regla de dependencia:** Aplicación depende de las reglas del Dominio y define
los contratos que necesita. Infraestructura implementa esos contratos; el
Dominio y el caso de uso no importan MySQL, Spring Data ni detalles HTTP.

## 4. Clases del caso de uso

| Clase / contrato | Tipo | Capa | Responsabilidad |
|---|---|---|---|
| `SalidaMaterialController` | Controlador | Presentación | Recibe la solicitud web y convierte el resultado del caso de uso en una respuesta. |
| `RegistrarSalidaMaterial` | Caso de uso | Aplicación | Coordina la validación, lectura del material, creación del movimiento y persistencia. |
| `SolicitudSalida` | DTO de entrada | Aplicación | Transporta identificador de material, proyecto y cantidad hacia el caso de uso. |
| `ResultadoSalida` | DTO de salida | Aplicación | Expone el resultado de la operación al adaptador de presentación. |
| `RepositorioAlmacen` | Puerto / interfaz | Aplicación | Declara operaciones de lectura y persistencia requeridas por el caso de uso. |
| `Material` | Entidad | Dominio | Mantiene el stock y rechaza una reducción que viole las reglas de negocio. |
| `MovimientoAlmacen` | Entidad | Dominio | Representa la salida de material vinculada al proyecto. |
| `TipoMovimiento` | Enumeración | Dominio | Distingue entradas de salidas. |
| `AdaptadorAlmacen` | Adaptador de persistencia | Infraestructura | Implementa `RepositorioAlmacen` y ejecuta las operaciones relacionales necesarias. |
| MySQL | Base de datos | Infraestructura | Conserva materiales, existencias y movimientos. |

Los nombres y responsabilidades son propuestas para el diseño detallado; no
afirman que existan clases implementadas con esos nombres.

## 5. Diagrama de secuencia: registrar salida

![Diagrama de secuencia de salida de almacén](../../img/nivel4-secuencia.png)

Fuente Mermaid editable: [nivel4-secuencia.mmd](../../img/fuentes/nivel4-secuencia.mmd).

| Paso | Origen → destino | Acción |
|---|---|---|
| 1 | Encargado → `SalidaMaterialController` | Solicita una salida con material, proyecto y cantidad. |
| 2 | Presentación → autorización del servidor | Verifica identidad y permiso antes de ejecutar la operación protegida. |
| 3 | `SalidaMaterialController` → `RegistrarSalidaMaterial` | Envía `SolicitudSalida` al caso de uso. |
| 4 | `RegistrarSalidaMaterial` → `RepositorioAlmacen` | Consulta el material y el stock mediante el puerto declarado en Aplicación. |
| 5 | Adaptador → MySQL | Obtiene los datos necesarios; devuelve un resultado o un error explícito. |
| 6 | `RegistrarSalidaMaterial` → `Material` | Solicita descontar la cantidad; Dominio valida que sea positiva y que el stock no resulte negativo. |
| 7 | `RegistrarSalidaMaterial` → `RepositorioAlmacen` | Solicita registrar el movimiento y actualizar el stock en una transacción. |
| 8 | Adaptador → MySQL | Confirma la transacción o informa del fallo. |
| 9 | Caso de uso → Presentación → Encargado | Devuelve el resultado exitoso solo si la operación se completó; en caso contrario comunica el rechazo. |

## 6. Reglas y garantías

- La cantidad debe ser mayor que cero.
- El material y el proyecto referenciado deben existir.
- El stock resultante no puede ser negativo.
- El movimiento y la actualización de stock se persisten atómicamente.
- Si falla una regla o la persistencia, se devuelve un error explícito y no se
  confirma una operación parcial.
- La implementación deberá contemplar concurrencia para evitar que dos salidas
  simultáneas consuman el mismo stock disponible.

Estas garantías son requisitos de diseño y todavía no se han implementado ni
probado.

## 7. Notación y patrones

| Elemento | Patrón o principio |
|---|---|
| `RepositorioAlmacen` y `AdaptadorAlmacen` | Repository y Adapter. |
| Caso de uso que depende de un puerto | Inversión de dependencias (DIP). |
| `Material` protege el stock | Entidad de dominio y responsabilidad única. |
| El adaptador implementa el puerto interno | Regla de dependencias de Clean Architecture. |

## 8. Documentos relacionados

- [Diseño interno de módulos](../03-diseno-de-software/dise%C3%B1o-interno/dise%C3%B1o-interno-de-modulos.md)
- [Principios de diseño](../03-diseno-de-software/dise%C3%B1o-interno/principios-de-dise%C3%B1o.md)
- [Patrones de diseño](../03-diseno-de-software/dise%C3%B1o-interno/patrones-de-dise%C3%B1o.md)
