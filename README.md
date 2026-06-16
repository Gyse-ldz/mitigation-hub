# 🛡️ SecOps-SIEM-SOAR

Plataforma de ciberseguridad desarrollada sobre .NET 10 orientada a la detección, análisis y respuesta automatizada ante incidentes de seguridad.

El proyecto implementa una arquitectura desacoplada de alto rendimiento basada en eventos, capaz de procesar grandes volúmenes de telemetría, persistir evidencia de manera confiable y ejecutar acciones de mitigación en tiempo real.

---

## 🎯 Objetivos

- Detectar eventos de seguridad en tiempo real.
- Procesar grandes volúmenes de telemetría.
- Persistir incidentes para auditoría y análisis forense.
- Automatizar respuestas de mitigación.
- Implementar resiliencia ante fallos de infraestructura.
- Visualizar eventos en vivo mediante dashboard independiente.

---

# 🏗️ Arquitectura General

El sistema sigue una arquitectura distribuida orientada a eventos.

### 🏗️ Arquitectura de Datos
```mermaid
graph LR
    A[API Controller] --> B(RabbitMQ)
    B --> C[Worker Service]
    C --> D[(SQL Server)]


### Componentes principales

- **Backend:** .NET 10
- **ORM:** Dapper
- **Base de Datos:** SQL Server 17
- **Mensajería:** RabbitMQ
- **Frontend:** React + SignalR
- **Resiliencia:** Polly
- **Patrones:** Circuit Breaker, Retry, Failover

---

## 🔄 Flujo de Procesamiento

1. Recepción de telemetría.
2. Publicación de eventos en RabbitMQ.
3. Consumo concurrente mediante workers.
4. Persistencia de incidentes en SQL Server.
5. Notificación en tiempo real mediante SignalR.
6. Ejecución de acciones de mitigación.

---

## Arquitectura y Modelo de Datos

​El sistema implementa una arquitectura desacoplada de alto rendimiento. Para garantizar la integridad en la respuesta ante incidentes, se diseñó un modelo de datos robusto persistido en SQL Server.

<p align="center">
  <img src="SQL_IncidentLogTabla.jpg" width="1000">
</p>

Esquema relacional diseñado para normalizar los datos de telemetría y garantizar la trazabilidad completa, permitiendo auditorías rápidas y la persistencia transaccional de cada evento detectado.

<p align="center">
  <img src="VC_Terminal_Escuchando.jpg" width="1000">
</p>

Visualización del backend en operación, escuchando eventos y gestionando conexiones entrantes de manera asíncrona.

## 🚀 Pruebas de Alta Concurrencia

​Sometimos el sistema a pruebas de carga masiva para validar su comportamiento ante picos de telemetría, asegurando resiliencia mediante Polly y una arquitectura orientada a eventos.

Dashboard en tiempo real mostrando la estabilidad operativa bajo alta carga. Se observa cómo el sistema mantiene el throughput constante sin degradación del servicio a pesar de la inyección masiva de eventos.
​Detalle del monitoreo de flujo en tiempo real durante la simulación: aquí validamos que el buffer y las estrategias de reintento gestionan correctamente los picos de telemetría sin pérdida de paquetes.

<p align="center">
  <img src="SecOps_275_Hilos.jpg" width="1000">
</p>

Dashboard de métricas durante el pico máximo de concurrencia.

<p align="center">
  <img src="Mitad_De_Rafaga.jpg" width="1000">
</p>

## 🛡️ Procesamiento y Mitigación

​El ciclo de vida del incidente incluye la detección automática, respuesta técnica y mecanismos de recuperación para asegurar la continuidad del servicio ante amenazas reales.

### Prueba de estrés: 

El backend procesa ráfagas de datos en tiempo real, demostrando un uso eficiente de hilos y gestión asíncrona de recursos.

​Acción de contención: ejecución de respuestas automatizadas. En este escenario, el sistema detecta patrones anómalos y aplica una política de contención definida, bloqueando las amenazas detectadas en el flujo y protegiendo el núcleo de la aplicación.

​Estado post-incidente: tras la neutralización, los mecanismos de limpieza se ejecutan de forma autónoma, garantizando que el sistema regrese a un estado estable sin intervención manual, reduciendo el tiempo de recuperación (MTTR).

<p align="center">
  <img src="VC_Terminal_Rafagas_Con_Exito.jpg" width="1000">
</p>

### Acción de contención: ejecución de respuestas automatizadas para neutralizar amenazas detectadas en el flujo.

Esta fase demuestra la capacidad de respuesta proactiva del sistema. Al identificar patrones de tráfico malicioso en tiempo real, el motor de seguridad dispara automáticamente protocolos de contención. En la captura se observa el momento preciso en que se bloquean las conexiones no autorizadas, aislando la amenaza sin interrumpir el procesamiento del tráfico legítimo.

<p align="center">
  <img src="Boton_Frenar.jpg" width="700">
</p>

### Estado post-incidente: mecanismos de limpieza y estabilización automática para el retorno al flujo operativo normal.

Una vez neutralizada la amenaza, el sistema ejecuta de forma autónoma rutinas de saneamiento de datos y liberación de recursos. Esto asegura la integridad del estado operativo, permitiendo que el servicio recupere su latencia y niveles de disponibilidad óptimos en milisegundos, reduciendo así al mínimo el impacto operativo y el tiempo de respuesta ante incidentes (MTTR).

<p align="center">
  <img src="Terminal_Limpia.jpg" width="1000">
</p>

---

### 🧠 Características Técnicas

**Backend**
* **Framework**: .NET 10, ASP.NET Core
* **Comunicación en Tiempo Real**: SignalR
* **ORM**: Dapper
* **Base de Datos**: SQL Server

**Mensajería y Eventos**
* **Broker**: RabbitMQ
* **Arquitectura**: Productores y consumidores desacoplados
* **Procesamiento**: Asíncrono de alto rendimiento

**Resiliencia**
* **Gestión de Fallos**: Polly
* **Patrones**: Circuit Breaker (Cortocircuitos), Políticas de reintento (Retry)
* **Alta Disponibilidad**: Estrategias de Failover híbrido

**Observabilidad**

* **Registro estructurado:** Implementado con Serilog para trazabilidad completa.
* **Telemetría de eventos:** Monitoreo del flujo mediante Application Insights (o la herramienta que uses).
* **Dashboard en tiempo real:** Visualización centralizada para monitoreo de KPI operativos.
---
### 🛠️ Desafíos Técnicos Resueltos
Durante el desarrollo del sistema, se superaron obstáculos críticos para garantizar la estabilidad operativa:

* **Gestión de Concurrencia:** Se neutralizaron condiciones de carrera (Race Conditions) generadas durante ráfagas de 25 peticiones HTTP/ms mediante validación asíncrona temprana y bloqueo de hilos.
* **Integridad de Datos:** Se resolvió la desalineación de tipos de datos entre el `ulong` de Discord y el `BIGINT` de SQL Server mediante el uso de `DynamicParameters` en Dapper, asegurando la precisión transaccional.
* **Serialización Segura:** Se optimizó la transferencia de datos configurando `PropertyNameCaseInsensitive` para evitar errores de deserialización en las respuestas de la API.

---

### 🚀 Cómo Ejecutar el Proyecto
Para desplegar este entorno de pruebas y monitoreo en tu máquina local, sigue estos pasos:

1. **Requisitos Previos**:
   * Tener instalado [.NET 10 SDK](https://dotnet.microsoft.com/download).
   * Contar con una instancia de [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) activa.
   * Tener [RabbitMQ](https://www.rabbitmq.com/download.html) instalado y corriendo.

2. **Configuración**:
   * Clona el repositorio: `git clone https://github.com/Gyse-Idz/mitigacion-h.git`
   * Configura la cadena de conexión en el archivo `appsettings.json` apuntando a tu instancia de SQL Server.

3. **Ejecución**:
   * Navega hasta la carpeta raíz del proyecto y ejecuta:
     ```bash
     dotnet run
     ```
   * El sistema iniciará automáticamente el servicio de escucha y el dashboard estará listo para recibir telemetría.

---

### 📊 Estado del Proyecto
Este sistema ha sido diseñado siguiendo una hoja de ruta estructurada para garantizar robustez:

| Componente | Estado | Tecnología Principal |
| :--- | :--- | :--- |
| **Resiliencia** | Completado | Polly v8 (Circuit Breaker) |
| **Seguridad de Datos** | Completado | Data Protection API (AES-256-GCM) |
| **Mensajería** | Completado | RabbitMQ (Asíncrono) |
| **Persistencia** | Completado | Dapper & SQL Server |

---

# 📈 Resultados Alcanzados

✅ Arquitectura orientada a eventos

✅ Persistencia confiable de incidentes

✅ Procesamiento concurrente

✅ Dashboard en tiempo real

✅ Integración SignalR

✅ Integración RabbitMQ

✅ Tolerancia a fallos

✅ Mitigación automatizada

---

# 🔐 Casos de Uso

- Security Operations Center (SOC)
- SIEM
- SOAR Recuperación ante desastres
- Correlación de eventos
- Respuesta automática a incidentes
- Monitoreo corporativo
- Laboratorios de Ciberseguridad

---

# 👩‍💻 Autora

**Gisela**

Cybersecurity | .NET Developer | SIEM/SOAR Engineering

Certificaciones:

- IBM Cybersecurity 
- IBM Artificial Intelligence 
- Microsoft Learn
- Microsoft Playwright Testing
---

## ⭐ Si te resulta interesante este proyecto

No olvides dejar una estrella al repositorio.
