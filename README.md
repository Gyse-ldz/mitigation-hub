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

# 🚀 Simulación de Alta Concurrencia

El sistema fue sometido a pruebas de carga mediante generación masiva de eventos concurrentes.

<p align="center">
  <img src="SecOps_275_Hilos.jpg" width="1000">
</p>

**Resultado:**

- Procesamiento simultáneo de cientos de eventos.
- Sin pérdida de mensajes.
- Persistencia consistente.
- Dashboard actualizado en tiempo real.

---

# 📡 Servicio en Ejecución

Backend escuchando eventos y conexiones entrantes.

<p align="center">
  <img src="VC_Terminal_Escuchando.jpg" width="1000">
</p>

---

# ⚡ Procesamiento de Ráfagas

Prueba de estrés mediante envío masivo de eventos.

<p align="center">
  <img src="VC_Terminal_Rafagas_Con_Exito.jpg" width="1000">
</p>

El sistema mantiene estabilidad operativa incluso bajo picos abruptos de carga.

---

# 🧹 Recuperación y Limpieza

Mecanismos de limpieza y estabilización posteriores al procesamiento.

<p align="center">
  <img src="Terminal_Limpia.jpg" width="1000">
</p>

---

# 🗄️ Persistencia de Incidentes

Todos los eventos procesados son almacenados para auditoría y análisis posterior.

<p align="center">
  <img src="SQL_IncidentLogTabla.jpg" width="1000">
</p>

Características:

- Persistencia transaccional.
- Trazabilidad completa.
- Evidencia para investigaciones.
- Base para correlación futura.

---

# 🛑 Mitigación Automática

El sistema incorpora acciones de respuesta automatizada para contener amenazas detectadas.

<p align="center">
  <img src="Boton_Frenar.jpg" width="700">
</p>

Funcionalidades:

- Contención de incidentes.
- Interrupción controlada de flujos.
- Respuesta inmediata ante eventos críticos.

---

# 🔥 Procesamiento Parcial de Ráfagas

Visualización de ejecución durante escenarios de carga continua.

<p align="center">
  <img src="Mitad_De_Rafaga.jpg" width="1000">
</p>

---

# 🧠 Características Técnicas

### Backend

- .NET 10
- ASP.NET Core
- SignalR
- Dapper
- SQL Server

### Mensajería

- RabbitMQ
- Productores y consumidores desacoplados
- Procesamiento asíncrono

### Resiliencia

- Polly
- Circuit Breaker
- Retry Policy
- Failover híbrido

### Observabilidad

- Logging estructurado
- Telemetría de eventos
- Dashboard en tiempo real

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
- SOAR
- Correlación de eventos
- Respuesta automática a incidentes
- Monitoreo corporativo
- Laboratorios de ciberseguridad

---

# 👩‍💻 Autora

**Gisela**

Cybersecurity | .NET Developer | SIEM/SOAR Engineering

Certificaciones:

- IBM Cybersecurity Fundamentals
- IBM Artificial Intelligence Fundamentals
- Microsoft Learn
- Microsoft Playwright Testing

---

## ⭐ Si te resulta interesante este proyecto

No olvides dejar una estrella al repositorio.
