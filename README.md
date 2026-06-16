# Proyecto SecOps-SIEM-SOAR

🛡️ Descripción del Proyecto
Arquitectura de seguridad corporativa diseñada para la detección, análisis y respuesta automatizada ante incidentes (SOAR). El sistema implementa un ecosistema desacoplado que garantiza la ingesta masiva de telemetría, persistencia inmutable y respuesta en tiempo real.

🏗️ Arquitectura del Sistema

El proyecto se basa en una arquitectura de alto rendimiento:

Backend: .NET Core, Dapper (ORM de alto rendimiento) y SQL Server.

Gestión de Eventos: Integración nativa con RabbitMQ para desacoplamiento de carga volumétrica.

Resiliencia: Implementación de patrones de tolerancia a fallos y failover híbrido para asegurar la continuidad del servicio ante caídas de infraestructura.

Frontend (ResAct): Panel de monitoreo independiente desarrollado para visualización de logs en tiempo real sin recarga de componentes.

🚀 Características Clave

Procesamiento Concurrente: Optimizado para condiciones de alta concurrencia mediante controladores asincrónicos.

Blindaje de Seguridad: Control estricto de Whitelist y persistencia mediante triggers transaccionales que garantizan el principio de no repudio de logs.

Desacoplamiento: Sistema orientado a eventos que aísla el procesamiento web del almacenamiento físico.

🛠️ Tecnologías Utilizadas

.NET Core / C#

SQL Server & Dapper

RabbitMQ (Message Broker)

React (para el dashboard operativo)

Arquitectura: Distribuida y orientada a eventos.


📂 Estructura del Repositorio
(Aquí podrías poner un breve árbol de directorios, por ejemplo:)

Plaintext
/src
  /Core.API         # Lógica de servidor y controladores
  /Data.Persistence # Mapeo Dapper y triggers de seguridad
  /Infrastructure   # Configuración de RabbitMQ y manejo de fallos
/docs               # Documentación maestra del proyecto
/dashboard          # Interfaz React

📈 Estado del Proyecto (V8)

Estado actual: Arquitectura completada y funcional. El núcleo básico está blindado y optimizado para entornos de producción corporativa.
