# Proyecto SecOps-SIEM-SOAR

## Descripción del Proyecto
Arquitectura de seguridad corporativa diseñada para la detección, análisis y respuesta automatizada ante incidentes (SOAR). El sistema implementa un ecosistema desacoplado que garantiza la ingesta masiva de telemetría, persistencia inmutable y respuesta en tiempo real.

## Arquitectura del Sistema
El proyecto se basa en una arquitectura de alto rendimiento:
Arquitectura de seguridad corporativa diseñada para la detección, análisis y respuesta automatizada ante incidentes (SOAR). El sistema implementa un ecosistema desacoplado que garantiza la ingesta masiva de telemetría, persistencia inmutable y respuesta en tiempo real.

* **Backend:** .NET 10.0, Dapper (ORM de alto rendimiento) y SQL Server 17.0.
* **Gestión de Eventos:** Integración nativa con RabbitMQ para desacoplamiento de carga volumétrica.
* **Resiliencia:** Implementación de patrones de tolerancia a fallos y failover híbrido para asegurar la continuidad del servicio ante caídas de infraestructura.
* **Frontend (ResAct):** Panel de monitoreo independiente desarrollado para visualización de registros en tiempo real sin recarga de componentes.

## Características Clave
* **Procesamiento Concurrente:** Optimizado para condiciones de alta concurrencia mediante controladores asíncronos.
* **Blindaje de Seguridad:** Control estricto de Whitelist y persistencia mediante triggers transaccionales que garantizan el principio de no repudio de logs.
* **Desacoplamiento:** Sistema orientado a eventos que aísla el procesamiento web del almacenamiento físico.

## Tecnologías Utilizadas
* .NET 10.0 / C#
* SQL Server 17.0 y Dapper
* RabbitMQ (Agente de mensajería)

---
**Estado del Proyecto:** Versión funcional.

**Autor:** Gisela Estefania Ortiz.
