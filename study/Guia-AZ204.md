# Guía de estudio AZ-204 (Developing Solutions for Microsoft Azure)

Esta guía te acompaña en 6 semanas para aprobar el AZ-204 combinando teoría, práctica y simulacros.

## Objetivos del examen (dominios)
1. Desarrollar soluciones de Azure Compute (25–30%)
   - App Service, Azure Functions, Azure Container Apps/AKS, Durable Functions
2. Desarrollar para almacenamiento (15–20%)
   - Blob, Queue, Table, Files, Cosmos DB
3. Implementar seguridad (20–25%)
   - Microsoft Entra ID (Azure AD), Managed Identity, Key Vault, RBAC
4. Supervisar, resolver problemas y optimizar (15–20%)
   - Azure Monitor, Application Insights, logging, alertas
5. Conectar y consumir servicios (15–20%)
   - Service Bus, Event Grid/Event Hubs, API Management, REST/SDKs

Referencias oficiales:
- Medidas del examen (skills measured): https://aka.ms/az-204-skills
- Microsoft Learn: https://learn.microsoft.com/training/paths/az-204-develop/
- Docs Azure: https://learn.microsoft.com/azure/?product=popular

## Plan de 6 semanas (2–3 h/día, 5 días/semana)

- Semana 1: Fundamentos de Compute
  - App Service (planes, despliegue, settings)
  - Azure Functions (triggers/bindings, escalado)
  - Laboratorios: Lab-01, Lab-02

- Semana 2: Almacenamiento
  - Azure Storage (Blob/Queue/Table), SAS, lifecycle
  - Cosmos DB (SDK, particiones, RU/s)
  - Laboratorios: Lab-03, Lab-04

- Semana 3: Mensajería y eventos
  - Service Bus (colas, topics, dead-letter)
  - Event Grid vs Event Hubs
  - Laboratorios: Lab-05

- Semana 4: Seguridad
  - Microsoft Entra ID (apps, scopes, roles)
  - Managed Identity y Key Vault
  - Laboratorios: Lab-06, Lab-07

- Semana 5: Integración y observabilidad
  - API Management (políticas)
  - Monitor, Application Insights, alertas
  - Laboratorios: Lab-08 (+ extra de observabilidad si puedes)

- Semana 6: Repaso + simulacros
  - Repaso rápido por objetivos
  - Simulacro 1 (Examen de prueba 1)
  - Simulacro 2 (Examen de prueba 2)
  - Revisión de errores y dudas

Sugerencia de método:
- 70-20-10: 70% práctica (labs), 20% docs/teoría, 10% simulacros.
- Toma notas de comandos, límites, y diferencias de servicios (p.ej. Event Grid vs Event Hubs vs Service Bus).

## Recomendaciones de recursos
- Microsoft Learn + sandbox gratuito para muchos módulos.
- Suscripción Azure gratuita o créditos de estudiante.
- SDKs: .NET 8 / Node.js LTS / Python 3.12 (elige tu stack primario).
- Azure CLI (az), Azure Functions Core Tools, Postman/REST Client.

## Lista de verificación (checklist)
- [ ] Despliegas una Web API en App Service con variables de entorno y slots
- [ ] Diseñas y ejecutas Functions (HTTP/Timer/Queue/Service Bus/Event Grid)
- [ ] Usas Blob/Queue/Table y Cosmos DB con SDK y claves administradas
- [ ] Proteges secretos en Key Vault y usas Managed Identity
- [ ] Empleas Service Bus topics/subs y Event Grid para eventos
- [ ] Configuras APIM e implementas políticas (rate limit, rewrite)
- [ ] Monitoreas con App Insights, logs, KQL básico
- [ ] Entiendes opciones de despliegue (Run From Package, Zip Deploy, Oryx)
- [ ] Conoces patrones de resiliencia (reintentos, DLQ, idempotencia)

## Estrategia para el examen
- Lee con atención los escenarios; identifica el servicio adecuado (p. ej. pub/sub => Service Bus topics).
- Elige opciones “managed” cuando sea posible (menos administración).
- Fíjate en requisitos no funcionales: latencia, costos, throughput, consistencia, TTL, reintentos, limits.
- Practica preguntas tipo “selecciona 2 que apliquen” y “políticas APIM”.
- Revisa límites/capacidades: Storage SAS vs RBAC, Cosmos RU/s, Service Bus modos, Event Grid filtros.

¡Éxitos en tu preparación!