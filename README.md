<h1 align="center">Konstantin Fatykov</h1>

<p align="center">
  <b>Backend Developer · Go &amp; Python</b><br>
  I take products from an empty repo to production — and keep them running there.
</p>

<p align="center">
  <a href="mailto:konstantinfatykov03@gmail.com"><img src="https://img.shields.io/badge/Email-konstantinfatykov03%40gmail.com-4A4A4A?logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://t.me/whoismilton"><img src="https://img.shields.io/badge/Telegram-%40whoismilton-26A5E4?logo=telegram&logoColor=white" alt="Telegram"></a>
  <img src="https://img.shields.io/badge/Yekaterinburg-remote%20%C2%B7%20open%20to%20Moscow-6B7280" alt="Location">
</p>

---

### Highlights

- 🚀 **AD Sender v2 — the primary SaaS product.** I designed and built the main product in Go and PostgreSQL: multi-tenant campaign automation, complex sales funnels and provider-agnostic communications. The first version was a hypothesis-validation pilot; v2 is the standalone SaaS platform, with tenant isolation, durable workflows and 1,600+ automated tests.
- 🏦 **I lead VRTCRM: AI analytics and business automation.** I drive the project from requirements and architecture to implementation and delivery for a 100M ₽ investment pool. The first release ran on real data in 10 days. AI-assisted deal analysis and automated financial workflows are the core; German, our analyst and data engineer, owns the data layer.
- 🤝 **Built it, sold it.** I built Orbita AI, put real customer orders through it in three days, then licensed it to a B2B supplier through my own sole proprietorship. I kept the IP and turned delivery into ongoing paid support.
- 🤖 **AI that actually ships.** LLM pipelines that parse purchase requests, supplier offers and calls, a 31-tool MCP server, RAG with cited sources — and a human, never the model, confirms anything dangerous.
- 🛡️ **I keep production running.** Reliability is part of delivery: PostgreSQL row-level security, a second person's approval for financial transactions, durable inbox/outbox, two-VPS failover, Prometheus / Grafana / Loki, and scheduled backup-restoration checks.

### Projects

| | What it is | Stack |
|---|---|---|
| **[quizmaster](https://github.com/Miltonian66/quizmaster)** | Mock-interview trainer with a grounded LLM-as-judge: versioned rubric, score computed outside the model, no sycophancy. [418 offline tests + 4 end-to-end checks](https://github.com/Miltonian66/quizmaster/actions/runs/34236236668). | FastAPI · SQLAlchemy · Alembic · FSRS · htmx |
| **[english-lab](https://github.com/Miltonian66/english-lab)** | English-learning platform in Telegram: 221 grammar rules and 2,723 exercises across A1–C2, adaptive level test, speaking practice with local Whisper + Piper. Pure stdlib, [416 tests](https://github.com/Miltonian66/english-lab/actions/runs/36968041953). | Python 3.11+ · SQLite · faster-whisper · Piper |
| **[rag-service](https://github.com/Miltonian66/rag-service)** | RAG API that answers with inline-cited sources. Swappable embedding / LLM / vector-store providers, SSE streaming. | FastAPI · pgvector · Claude |
| **[Task-Tracker](https://github.com/Miltonian66/Task-Tracker)** | Async task API with Redis cache and graceful degradation, status state machine, request-id error envelope. | FastAPI · PostgreSQL · Redis |
| **Orbita AI**<br><sub>private · sold to a client</sub> | AI-first B2B platform: a purchase request (photo, Excel, PDF) becomes supplier SKUs, a human moderator approves. 81% of lines accepted without edits. 73 registered business operations, a 31-tool MCP server, 1,400+ tests. | FastAPI · SQLite · MCP |
| **AD Sender v2**<br><sub>private · main SaaS product</sub> | The primary SaaS platform for campaign automation and sales funnels. Greenfield Go/PostgreSQL architecture, tenant isolation with RLS, provider-agnostic communications and durable jobs. v1 was the hypothesis-validation pilot. | Go · PostgreSQL · River · React |
| **VRTCRM**<br><sub>private · project lead</sub> | AI-assisted operations for an investment car-resale business: Telegram offers become validated purchase opportunities, financial workflows and investor reporting are automated. I lead the project and own most of the engineering delivery; German owns data engineering and data quality. | TypeScript · Fastify · React · PostgreSQL · LLM |

<details>
<summary><b>More about each project</b></summary>
<br>

**quizmaster** — asks questions on your weakest topics, grades free-text answers against a versioned rubric. The score is derived deterministically from covered points, not asked from the model; the candidate's answer is wrapped as data to block prompt injection; a provider outage yields `ungraded` instead of a crash. FSRS + confidence EMA decide what to ask next. CLI and htmx web share one service layer; CI runs ruff → mypy → migration drift check → pytest, all offline via a fake provider.

**english-lab** — 221 grammar rules and 2,723 exercises across A1–C2, an adaptive placement test, SM-2 repetition, listening, writing feedback, role-play dialogues and a grounded `/help` assistant over a verifiable knowledge base. No framework: own Telegram Bot API client, per-user sequential queues, isolated worker pools for LLM / STT / TTS, backpressure under Telegram rate limits. LLM provider is one env var: Codex CLI, Claude Code CLI, OpenAI or Anthropic.

**rag-service** — ingest → chunk → embed → retrieve with pgvector → answer with citations via Claude. Async FastAPI + SQLAlchemy 2.0, Alembic, Docker, CI, offline test suite.

**Task-Tracker** — a small service done properly: PostgreSQL + Redis cache with graceful degradation, unified error envelope with `request_id`, status state machine, Alembic, non-root Docker image with healthcheck, CI (ruff + pytest).

**Orbita AI** — three independent LLM roles (parse → select → verify) behind a swappable provider (Claude Code CLI / Codex CLI), with a per-role model and spend cap. Every user action lives once in an operations layer and is exposed both as an HTTP route and as an MCP tool with identical permission checks and audit. Moderator decisions become selection rules only after an owner approves them. 30+ releases in the first month; deployed on a hardened VPS with health checks, auto-recovery, daily snapshots and one-command rollback.

**AD Sender v2** — the main version of AD Sender, built as a standalone SaaS independently from the v1 pilot. I own the product architecture, backend, integrations, tests and delivery. The platform supports complex communication funnels through a provider-agnostic design, with PostgreSQL row-level security for tenant isolation, durable background jobs, reliable inbox/outbox processing, monitoring and recovery. The v1 pilot served to validate the initial hypothesis on real workflows; v2 is the primary SaaS codebase.

**VRTCRM** — I lead the project and own most of the engineering delivery: requirements, architecture, AI analytics and automation, the Fastify/Drizzle API, React/TanStack front end and releases. German is the analyst and data engineer responsible for the data model, pipelines and data quality. The product automates offer intake, supports AI-assisted purchasing analysis and streamlines investment operations: offers from Telegram are parsed by an LLM, personal data is masked, and code checks VINs, prices and business constraints before offers enter the purchasing workflow. AI-assisted offer analysis helps distinguish viable opportunities from unprofitable ones; financial operations and investor reporting run on a shared data foundation. Deny-by-default permissions, a separate investor database role, second-person approval for money movements and an audit trail protect the workflow. Live updates use SSE over `LISTEN/NOTIFY`; conflicting edits return 409, and undo is a compensating operation.

</details>

### Stack

| Area | Tools |
|---|---|
| **Languages** | Go · Python · TypeScript · SQL |
| **Backend** | net/http · pgx · River · FastAPI · asyncio · SQLAlchemy 2.0 · Fastify · Drizzle · Celery / RabbitMQ |
| **Data** | PostgreSQL (RLS, pgvector) · Redis · ClickHouse · SQLite |
| **Infra** | Docker · Caddy · GitHub Actions (self-hosted JIT runners) · GitLab CI · Prometheus · Grafana · Loki |
| **AI** | OpenAI / Anthropic APIs · Claude Code / Codex CLI · Whisper · RAG · MCP |

<sub>Most of my commercial work is private or under NDA — AD Sender v2, Orbita AI, VRTCRM, marketplace integrations (Ozon / Wildberries), CRM data pipelines, call transcription and AI summarization, ClickHouse analytics. The public repos show the stack and how I build.</sub>
