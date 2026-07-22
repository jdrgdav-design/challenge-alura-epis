# 🤖 EPIS - Asistente Inteligente de Inventario Farmacéutico

> **Proyecto desarrollado para el Challenge Alura - Agente IA**  
> *Plataforma web e inteligencia artificial orquestada con n8n, Supabase y desplegada en Oracle Cloud Infrastructure (OCI).*

---

##  Descripción General

**EPIS** es un Agente de Inteligencia Artificial especializado en la gestión logística e inventario farmacéutico. El sistema conecta una interfaz web interactiva (**Frontend**) con un motor de automatización (**n8n**) que analiza en tiempo real el consumo de medicamentos, identifica productos en riesgo o agotados, calcula proyecciones de rotación y responde a consultas en vivo o envía informes consolidados.

---

##  Integración y Flujo de Comunicación: Web Frontend ⟷ n8n Backend

La página web actúa como la interfaz de usuario, mientras que **n8n funciona como el backend Serverless de la aplicación**. La comunicación entre ambos ocurre en tiempo real siguiendo estos pasos:

```text
[  Usuario en Web ]
         │
         │ 1. Envía mensaje/evento (Fetch HTTP POST)
         ▼
[  Webhook Trigger en n8n ]
         │
         │ 2. Consulta inventario
         ▼
[  Supabase PostgreSQL ] ──> (Retorna datos actualizados)
         │
         │ 3. Procesa prompt + contexto
         ▼
[  Agente IA (EPIS + Simple Memory) ]
         │
         │ 4. Retorna respuesta JSON / HTML
         ▼
[  Widget Web ] / [  Telegram API ]
