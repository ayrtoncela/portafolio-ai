# AI Solutions Builder — Ayrton Cela

> I design and implement AI systems end-to-end — from the model to the interface the team uses every day.
> Not prototypes: production systems with real business logic, real integrations, and measurable impact.

🌐 **Portfolio:** [ayrtoncela.vercel.app](https://ayrtoncela.vercel.app/)
🌐 **Live demo:** [web-page-saa-s.vercel.app](https://web-page-saa-s.vercel.app)
🎥 **Video demo:** [Watch on YouTube](https://www.youtube.com/watch?v=_C-984BwlBQ)

---

## Projects

### 1. Atico Film Lab — Full order management system via Instagram DM

> Analog film lab in Mexico City. Went from manually handling orders by DM to a fully automated end-to-end system.

**Metrics (Feb–Mar 2026):** ~$50K MXN processed · 30+ orders · 150+ rolls developed · v3.26 live

```
Instagram DM  →  Bot GPT-4o-mini  →  Node.js Backend  →  Supabase
                      ↓                      ↓
               Ops dashboard           RAG pipeline
               (Atico team)          (pgvector + embeddings)
```

**Conversational bot**
- Detects intent, quotes based on real catalog, confirms order, guides payment
- Bilingual (ES/EN) with automatic language detection
- Per-conversation state machine — no human intervention in the standard flow
- Handles real Instagram constraints: 24h window, message types, retries with backoff

**Backend**
- Node.js + Express on Railway — Instagram webhooks with deduplication
- PostgreSQL persistence via Supabase, monitoring with Sentry
- Automated test suite for the AI extractor

**Operations dashboard**
- Real-time Kanban with drag-and-drop
- Financial KPIs with weekly/monthly/3M/6M charts
- Full conversation history + global search (Cmd+K)

**RAG pipeline**
- Ingestion: conversation chunking → `text-embedding-3-small` → pgvector (HNSW index)
- Query: embed question → cosine similarity → top-5 chunks → GPT-4o-mini with real context
- Team queries their conversations in natural language: _"which clients asked about scanning?"_

**Stack:** `Node.js` `Express` `GPT-4o-mini` `text-embedding-3-small` `pgvector` `Instagram Graph API` `Supabase` `PostgreSQL` `Railway` `Vercel` `Sentry`

🔗 [github.com/ayrtoncela/client-foto](https://github.com/ayrtoncela/client-foto) · Status: **Live**

---

### 2. Mikaela Montenegro — Instagram bot + website for a visual artist

> Ecuadorian visual artist with exhibitions in New York, Paris and Quito. Full system: Instagram campaign bot, bilingual website, and student management dashboard.

```
Instagram DM  →  Bot GPT-4o-mini  →  Node.js Backend  →  Supabase
(from reel)          ↓ campaigns            ↓
                  AI Draft             Ops dashboard
                 (copy-paste)         (students + capacity)
```

**Campaign bot**
- Only responds to DMs originating from boosted reels
- Each campaign has its own context: what's offered, price, schedule, capacity, location
- Automatic matching by ad `post_id` (`ads_context_data` from Meta)
- Numeric max capacity: auto-pauses the campaign when the last student enrolls
- Already-enrolled students keep receiving responses even when the campaign is paused
- Per-conversation killswitch (take over / release bot per chat)
- AI Draft: generates a campaign response for manual copy-paste when the bot can't send (24h window)
- Protection against prompt injection, roleplay, and markdown

**Student dashboard**
- Enroll a student directly from the conversation → linked to the workshop and campaign
- Real-time counter: `5 / 8 enrolled` with auto-pause when full
- Per-conversation badges showing enrolled workshops and payment status

**Bilingual website (ES/EN)**
- Landing page with individual exhibition dropdown in nav
- `/exposicion/:slug` pages: slideshow with arrows + lightbox + artwork label
- Purchase modal: original artwork + giclée prints in 4 sizes (A4–A1)
- `/bio` page with full CV: education, solo and group exhibitions
- Art School section with permanent courses and special workshops

**Stack:** `Node.js` `Express` `GPT-4o-mini` `Instagram Graph API` `Supabase` `PostgreSQL` `Railway`

Status: **Live**

---

### 3. Clinical Laboratory — WhatsApp appointment bot

> Automated booking in 5 steps — branch selection, study type and preparation instructions.

- 3 branches with embedded schedules
- Preparation instructions by study type
- Google Sheets logging + email notifications
- Human takeover when the bot can't resolve

**Stack:** `Node.js` `GPT-3.5` `Meta Cloud API (WhatsApp)` `Google Apps Script` `Railway`

Status: **Live Demo** — [web-page-saa-s.vercel.app](https://web-page-saa-s.vercel.app)

---

### 4. Client Hub — Internal tool with Ansible automation

> Centralized client information system for a consulting firm. Quick access to data, contracts and history. Ansible playbook runner to automate admin tasks on client servers.

**Stack:** `n8n` `Python` `Ansible` `Node.js`

Status: **In development**

---

## What I build

| | |
|---|---|
| **Conversational agents** | LLM + real business logic + edge cases + human escalation |
| **RAG pipelines** | Chunking · embeddings · vector search · contextualized responses |
| **Backend** | Webhooks · state machines · APIs · persistence · monitoring |
| **Dashboards** | Real-time ops · financials · student management · semantic search |
| **Websites** | Bilingual landing pages · galleries · exhibition pages · art e-commerce |
| **Automation** | n8n · Python · Ansible · GitHub Actions |

---

## Full stack

`Node.js` `Express` `Python` `OpenAI API` `GPT-4o-mini` `text-embedding-3-small`
`pgvector` `PostgreSQL` `Supabase` `Instagram Graph API` `Meta Cloud API`
`n8n` `Ansible` `Railway` `Vercel` `Sentry` `Google Apps Script` `GitHub Actions`
`Cursor` `MCP`

---

## Contact

**WhatsApp:** [+52 5544621764](https://wa.me/525544621764)  
**Email:** ayrtoncela94@gmail.com  
**GitHub:** [github.com/ayrtoncela](https://github.com/ayrtoncela)

> Built with help from Claude
