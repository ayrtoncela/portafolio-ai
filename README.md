# AI Solutions Builder — Ayrton Cela

> Diseño e implemento sistemas de IA de extremo a extremo — del modelo a la interfaz que el equipo usa todos los días.
> No prototipos: sistemas en producción con lógica de negocio real, integraciones reales e impacto medible.

🌐 **Portfolio:** [ayrtoncela.vercel.app](https://ayrtoncela.vercel.app/)
🌐 **Demo live:** [web-page-saa-s.vercel.app](https://web-page-saa-s.vercel.app)
🎥 **Video demo:** [Ver en YouTube](https://www.youtube.com/watch?v=_C-984BwlBQ)

---

## Proyectos

### 1. Atico Film Lab — Sistema completo de pedidos por Instagram DM

> Laboratorio de revelado analógico en CDMX. Pasaron de recibir pedidos a mano por DM a tener un sistema end-to-end automatizado.

**Métricas (Feb–Mar 2026):** ~$50K MXN procesados · ~30+ pedidos · ~150+ rollos revelados · v3.26 activo

```
Instagram DM  →  Bot GPT-4o-mini  →  Backend Node.js  →  Supabase
                      ↓                     ↓
               Dashboard ops          RAG pipeline
               (equipo Atico)       (pgvector + embeddings)
```

**Bot conversacional**
- Detecta intención, cotiza según catálogo real, confirma pedido, guía pago
- Bilingüe (ES/EN) con detección automática de idioma
- Máquina de estados por conversación — sin intervención humana en flujo estándar
- Manejo de restricciones reales de Instagram: ventana 24h, tipos de mensaje, reintentos con backoff

**Backend**
- Node.js + Express en Railway — webhooks de Instagram con deduplicación
- Persistencia en PostgreSQL vía Supabase, monitoreo con Sentry
- Test suite automatizado para el extractor de IA

**Dashboard de operaciones**
- Kanban en tiempo real con drag-and-drop
- KPIs financieros con gráficas por semana/mes/3M/6M
- Historial completo de conversaciones + búsqueda global (Cmd+K)

**RAG pipeline**
- Ingestión: chunking de conversaciones → `text-embedding-3-small` → pgvector (HNSW index)
- Query: embed pregunta → similitud coseno → top-5 chunks → GPT-4o-mini con contexto real
- El equipo consulta sus conversaciones en lenguaje natural: _"¿qué clientes preguntaron por escaneo?"_

**Stack:** `Node.js` `Express` `GPT-4o-mini` `text-embedding-3-small` `pgvector` `Instagram Graph API` `Supabase` `PostgreSQL` `Railway` `Vercel` `Sentry`

🔗 [github.com/ayrtoncela/client-foto](https://github.com/ayrtoncela/client-foto) · Status: **Live**

---

### 2. Laboratorio Clínico — Bot de agendamiento por WhatsApp

> Agendamiento automático en 5 pasos — selección de sucursal, estudio e instrucciones de preparación.

- 3 sucursales con horarios embebidos
- Instrucciones de preparación por tipo de estudio
- Logging en Google Sheets + notificaciones email
- Human takeover cuando el bot no puede resolver

**Stack:** `Node.js` `GPT-3.5` `Meta Cloud API (WhatsApp)` `Google Apps Script` `Railway`

Status: **Live Demo** — [web-page-saa-s.vercel.app](https://web-page-saa-s.vercel.app)

---

### 3. Hub de Clientes — Herramienta interna con automatización Ansible

> Sistema centralizado de información de clientes para una firma de consultoría. Acceso rápido a datos, contratos e historial. Runner de playbooks Ansible para automatizar tareas de administración en servidores de clientes.

**Stack:** `n8n` `Python` `Ansible` `Node.js`

Status: **En desarrollo**

---

## Lo que construyo

| | |
|---|---|
| **Agentes conversacionales** | LLM + lógica de negocio real + edge cases + escalación humana |
| **RAG pipelines** | Chunking · embeddings · vector search · respuesta contextualizada |
| **Backend** | Webhooks · máquinas de estado · APIs · persistencia · monitoreo |
| **Dashboards** | Operaciones en tiempo real · finanzas · búsqueda semántica |
| **Automatización** | n8n · Python · Ansible · GitHub Actions |

---

## Stack completo

`Node.js` `Express` `Python` `OpenAI API` `GPT-4o-mini` `text-embedding-3-small`
`pgvector` `PostgreSQL` `Supabase` `Instagram Graph API` `Meta Cloud API`
`n8n` `Ansible` `Railway` `Vercel` `Sentry` `Google Apps Script` `GitHub Actions`
`Cursor` `MCP`

---

## Contacto

**WhatsApp:** [+52 993 234 0850](https://wa.me/529932340850)
**Email:** ayrtoncela94@gmail.com
**GitHub:** [github.com/ayrtoncela](https://github.com/ayrtoncela)

> Construido con ayuda de Claude
