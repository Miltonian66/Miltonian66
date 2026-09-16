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

- 🚀 **From scratch to production.** Summer 2026: a multi-tenant communication-funnel platform in Go for an advertising agency — v1 running in production, v2 in pilot three weeks after its first commit. ~180k lines of Go, 3 000+ tests, one engineer.
- 🤖 **AI that actually ships.** Call transcription and LLM summaries for a CRM, RAG with cited sources, a 29-tool MCP server, and LLM pipelines where a human — never the model — confirms dangerous actions.
- 🛡️ **Boring on purpose.** PostgreSQL with row-level security, durable inbox/outbox, fail-closed release delivery, two-VPS failover, Prometheus / Grafana / Loki, backups that get restored on a timer.

### Projects

| | What it is | Stack |
|---|---|---|
| **[quizmaster](https://github.com/Miltonian66/quizmaster)** | Mock-interview trainer with a grounded LLM-as-judge: versioned rubric, score computed outside the model, no sycophancy. 400 offline tests. | FastAPI · SQLAlchemy · Alembic · FSRS · htmx |
| **[english-lab](https://github.com/Miltonian66/english-lab)** | English-learning platform in Telegram: A1–C2 course, adaptive level test, speaking practice with local Whisper + Piper. Pure stdlib, 239 tests. | Python 3.11 · SQLite · faster-whisper · Piper |
| **[rag-service](https://github.com/Miltonian66/rag-service)** | RAG API that answers with inline-cited sources. Swappable embedding / LLM / vector-store providers, SSE streaming. | FastAPI · pgvector · Claude |
| **[Task-Tracker](https://github.com/Miltonian66/Task-Tracker)** | Async task API with Redis cache and graceful degradation, status state machine, request-id error envelope. | FastAPI · PostgreSQL · Redis |
| **Orbita AI** <sub>private, in production</sub> | AI-first B2B platform: a free-form purchase request becomes supplier SKUs, a human moderator approves. One operations layer behind ~100 HTTP routes and a 29-tool MCP server. 900+ tests. | FastAPI · SQLite · MCP |

<details>
<summary><b>More about each project</b></summary>
<br>

**quizmaster** — asks questions on your weakest topics, grades free-text answers against a versioned rubric. The score is derived deterministically from covered points, not asked from the model; the candidate's answer is wrapped as data to block prompt injection; a provider outage yields `ungraded` instead of a crash. FSRS + confidence EMA decide what to ask next. CLI and htmx web share one service layer; CI runs ruff → mypy → migration drift check → pytest, all offline via a fake provider.

**english-lab** — 221 grammar rules and 1 768 exercises across A1–C2, an adaptive placement test, SM-2 repetition, listening, writing feedback, role-play dialogues and a grounded `/help` assistant over a verifiable knowledge base. No framework: own Telegram Bot API client, per-user sequential queues, isolated worker pools for LLM / STT / TTS, backpressure under Telegram rate limits. LLM provider is one env var: Codex CLI, OpenAI or Anthropic.

**rag-service** — ingest → chunk → embed → retrieve with pgvector → answer with citations via Claude. Async FastAPI + SQLAlchemy 2.0, Alembic, Docker, CI, offline test suite.

**Task-Tracker** — a small service done properly: PostgreSQL + Redis cache with graceful degradation, unified error envelope with `request_id`, status state machine, Alembic, non-root Docker image with healthcheck, CI (ruff + pytest).

**Orbita AI** — three independent LLM roles (parse → select → verify) behind a swappable provider (Claude Code CLI / Codex CLI). Every user action lives once in an operations layer and is exposed both as an HTTP route and as an MCP tool with identical permission checks and audit. Moderator decisions become selection rules only after approval; supplier price lists (xlsx / xls) rebuild the catalog with golden-set regression. RBAC, sessions, CSRF, audit log, hardened VPS deployment.

</details>

### Stack

| | |
|---|---|
| **Languages** | Go · Python · TypeScript · SQL |
| **Backend** | net/http · pgx · River · FastAPI · asyncio · SQLAlchemy 2.0 · Celery / RabbitMQ |
| **Data** | PostgreSQL (RLS, pgvector) · Redis · ClickHouse · SQLite |
| **Infra** | Docker · Caddy · GitHub Actions (self-hosted JIT runners) · GitLab CI · Prometheus · Grafana · Loki |
| **AI** | OpenAI / Anthropic APIs · Whisper · RAG · MCP · Claude Code |

<sub>Most of my commercial work is under NDA — the Go platform above, marketplace integrations (Ozon / Wildberries / Yandex Market), CRM data pipelines, call transcription and AI summarization, ClickHouse analytics. The public repos show the stack and how I build.</sub>
