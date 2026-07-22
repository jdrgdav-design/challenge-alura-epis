# 🤖 EPIS - Sistema Inteligente de Gestión Farmacéutica y Notificaciones a Pacientes

> **Proyecto desarrollado para el Challenge Alura - Agente IA**  
> *Plataforma de gestión logística orquestada con n8n, Supabase y Gmail API para optimizar el inventario farmacéutico y notificar automáticamente a los usuarios.*

---

## Contexto y Problemática en Colombia

En Colombia, el proceso para reclamar medicamentos a través de las EPS representa un gran obstáculo para los ciudadanos. Los usuarios suelen realizar **viajes en vano** y hacer **largas filas de espera** sin saber si su fórmula médica está disponible en la sede o si les falta presentar algún documento o requisito específico.

Por otro lado, el personal de farmacia y los despachadores no cuentan con herramientas ágiles para gestionar el stock crítico y comunicarse masivamente con los pacientes.

---

##  La Solución: EPIS

**EPIS** resuelve esta problemática dividiendo la solución en dos frentes clave:

### 1.  Asistente Virtual para Personal de Farmacia y Despachadores
Un Chatbot con Inteligencia Artificial que sirve como **herramienta interna de trabajo** para el equipo logístico. Les permite:
* Consultar en tiempo real el stock de medicamentos agotados o críticos.
* Generar reportes consolidados de reabastecimiento.
* Ordenar el envío de notificaciones masivas o individuales a los pacientes.

### 2. Sistema de Notificaciones por Gmail para Pacientes
Los usuarios/pacientes reciben correos electrónicos automáticos informándoles:
 **Disponibilidad de Recojo:** Confirmación de que su pedido ya está listo en la sede.
 **Requisitos y Documentación:** Indicaciones claras sobre qué llevar (cédula, fórmula física, autorización, etc.).
 **Avisos de Reabastecimiento:** Notificación inmediata a su correo cuando llega el lote de un medicamento que estaba agotado.

---

##  Arquitectura y Flujo de Comunicación

```text
  [  Pacientes ] ──(Solicitan medicamentos)──┐
                                               │
                                               ▼
  [  Despachadores ] ──(Usan Chatbot IA)──> [  Web Frontend ]
                                                   │
                                                   ▼
                                          [  n8n Backend ] <──> [  Agente IA ]
                                                   │                   │
                                                   ├───────────────────┘
                                                   │
                         ┌─────────────────────────┴─────────────────────────┐
                         ▼                                                   ▼
            [  Supabase DB ]                                 [  Gmail API (n8n) ]
         (Solicitudes e Inventario)                                          │
                                                                             ▼
                                                                   [  Correo al Paciente ]
