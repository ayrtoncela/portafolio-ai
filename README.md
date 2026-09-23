# Ayrton Cela — Engineering & Automation Portfolio

> Engineering manager and hands-on builder with 8+ years across telecommunications, APIs, infrastructure and AI automation.
> I build production systems that turn real conversations into clean, structured, searchable data.

🌐 **Portfolio:** [ayrtoncela.cloud](https://ayrtoncela.cloud)
🎥 **Video demo:** [WhatsApp bot + backend](https://www.youtube.com/watch?v=_C-984BwlBQ)
🇪🇸 **Versión en español:** [portafolio-bots](https://github.com/ayrtoncela/portafolio-bots)

> Client code lives in private repositories. Happy to walk through architecture, data models or a live demo on a call.

---

## Projects

### 1. Atico Film Lab — Order management over Instagram DMs · `Live`

> Film processing lab in Mexico City. Every order used to live in the team's Instagram inbox — no tracking, no history.

**Results:** $50K+ MXN processed in the first 2 months · 150+ film rolls tracked end to end

- Conversational bot quotes from the real catalog, confirms the order and guides payment (ES/EN, auto-detected)
- Each conversation becomes a structured order: ID (`ORD-YYYYMM-XXXX`), format, quantity, price, branch, status
- Payment receipts received by DM and validated from the dashboard
- Operations dashboard: kanban pipeline, financial KPIs by week/month, global search (Cmd+K), human takeover
- RAG over past conversations (`text-embedding-3-small` → pgvector) so the team can ask questions in plain language

**Stack:** `Node.js` `Express` `OpenAI` `pgvector` `Instagram Graph API` `Supabase` `PostgreSQL` `Stripe` `Railway` `Sentry`

📄 [Case study](https://www.ayrtoncela.cloud/atico.html)

---

### 2. Mikaela Montenegro — Conversational CRM and lead attribution · `Live`

> Visual artist and art school in Ecuador. 880+ unanswered Instagram conversations, students tracked in notes, no idea which campaign brought which student.

**Results:** 880+ conversations managed · 100+ DMs handled in 24 h without intervention · unattributed leads 370 → 4

- Bot grounded on her real catalog (RAG)
- Dashboard for students, workshops, commissions, exhibitions and campaigns
- Reconciliation of Meta ad exports against lead records to attribute each lead to its campaign
- Campaign bot: each boosted reel has its own context (offer, price, schedule, seats); DMs are matched to the ad automatically and the campaign pauses itself when the last seat is filled
- Bilingual website with exhibitions, artwork lightbox and a shop for originals and giclée prints
- Content calendar synced 1:1 with the source document (202 pieces)

**Stack:** `Node.js` `Express` `OpenAI` `RAG` `Supabase` `Stripe` `Resend` `Railway`

📄 [Case study](https://www.ayrtoncela.cloud/mikaela.html)

---

### 3. RENACE 2026 — QR tickets, offline check-in and certificates · `Delivered`

> Two-day event in Guayaquil (September 6–7, 2026). Individual QR tickets for every attendee, door check-in that could not depend on the venue's wifi, and attendance certificates afterwards.

**Results:** 318 attendees across 4 ticket types · 305 tickets delivered by email without a bounce · 6 phones scanning offline at one door · 237 certificates delivered

- Data cleaning from the organizer's spreadsheet: missing headers, two emails in one cell, invisible characters
- Ticket generator (designer template + name + unique QR) and SMTP delivery with automatic reconnect
- Bounce checker over IMAP matched against the attendee list; every failed delivery traced with a reason
- Offline check-in PWA: QR scanning, duplicate detection with time of first entry, search by name, CSV export
- 253 certificate PDFs matched to attendees by normalized name

**Stack:** `Python` `openpyxl` `Pillow` `qrcode` `SMTP/IMAP` `ReportLab` `PWA` `html5-qrcode` `Vercel`

📄 [Case study](https://www.ayrtoncela.cloud/renace.html) · 🔗 [Demo](https://checkin-rho-teal.vercel.app) (access code `renace2026`, sample data only)

---

### 4. AyrTok — Conversational booking platform (multi-tenant SaaS) · `Live`

> My own product. Small clinics and businesses take bookings by hand over WhatsApp and Instagram.

- One backend serving many businesses; webhook routing per tenant
- Conversations become validated appointments and client records
- Google Calendar sync, payments through Stripe Connect (each business gets paid directly)
- Dashboard per business: agenda, client records, conversations, payments

**Stack:** `Node.js` `Express` `Supabase` `WhatsApp Cloud API` `Instagram Graph API` `Google Calendar API` `Stripe Connect` `OpenAI` `Railway`

🔗 [ayrtok.com](https://ayrtok.com)

---

### 5. Clinical lab — WhatsApp booking bot · `Live demo`

- Step-by-step booking: study type → branch → day → time → patient data
- 3 branches with embedded schedules and preparation instructions per study
- Every lead logged to Google Sheets + email notification
- Same backend also serves a web chat widget

**Stack:** `Node.js` `OpenAI` `Meta Cloud API (WhatsApp)` `Google Apps Script` `Google Sheets` `Railway`

🔗 [Live demo](https://web-page-saa-s.vercel.app) (chat widget in the bottom-right corner)

---

### 6. Personal finance platform — Local-first data pipeline

- One parser per bank/card issuer: PDF text extraction plus OCR for scanned statements
- Transactions normalized into a single SQLite database with categorization and monthly indicators
- Data-quality audit found and fixed 29 duplicated and 4 miscategorized transactions that inflated one month by ~25%

**Stack:** `Python` `SQLite` `pdfplumber` `Tesseract OCR`

📄 [Case study](https://www.ayrtoncela.cloud/finanzas.html) (screens use fictional data)

---

## Shared bot architecture

```
┌──────────────────┐     ┌─────────────────────┐     ┌──────────────────┐
│  Instagram DMs   │────▶│                     │────▶│   OpenAI API     │
│  WhatsApp        │     │  Node.js + Express  │     │  (prompt + RAG   │
│  Web chat        │────▶│      backend        │     │   per client)    │
└──────────────────┘     │                     │     └──────────────────┘
                         │  • Webhook handler  │
                         │  • State machine    │────▶┌──────────────────┐
                         │  • Deduplication    │     │    Supabase      │
                         │  • Session + lang   │     │  (PostgreSQL)    │
                         │  • Human takeover   │     └──────────────────┘
                         │  • Email alerts     │
                         └──────────┬──────────┘
                                    │
                         ┌──────────┴──────────┐
                         │  Operations         │
                         │  dashboard          │
                         └─────────────────────┘
```

- Per-client state machine so structured flows never go off track; LLM fallback for free-form messages
- Message deduplication (`processed_messages`), configurable session timeout, ES/EN detection
- Real Instagram/WhatsApp constraints handled: 24-hour window, message types, retries with backoff
- Human takeover: pause the bot and reply manually from the dashboard

---

## Professional background

- **Consulting Engineering Manager** at a US-based UCaaS platform (KAZOO) — lead 6 globally distributed engineers; ~10,000-seat contact center rollout, the largest in the company's history; 30+ enterprise projects across Europe, South Africa, the US and LATAM
- **Senior Engineer** at MCM Telecom (Mexico) — 40+ telecom projects across Mexico and LATAM
- Kamailio · FreeSWITCH · Kazoo · BroadWorks · MetaSwitch · SIP/RTP · Ansible · Python · Linux
- B.Eng. Electronics & Telecommunications · MBA

---

## Stack

| Area | Tools |
|---|---|
| Data & backend | PostgreSQL · Supabase · SQLite · Node.js · Express · Python · REST APIs · Webhooks |
| Automation & AI | OpenAI API · RAG / pgvector · Google Apps Script · Google Sheets · n8n · Claude Code |
| Messaging & payments | WhatsApp Cloud API · Instagram Graph API · Stripe / Stripe Connect · Google Calendar API |
| Infrastructure | Linux · Docker · Ansible · Bash · Git / GitHub · Railway · Vercel · Cloudflare · Sentry |

---

## Contact

📧 [ayrton@ayrtoncela.cloud](mailto:ayrton@ayrtoncela.cloud)
📱 [+52 55 4462 1764](https://wa.me/525544621764) (WhatsApp)
💼 [LinkedIn](https://linkedin.com/in/ayrton-c-66361a203)
🌐 [ayrtoncela.cloud](https://ayrtoncela.cloud)
