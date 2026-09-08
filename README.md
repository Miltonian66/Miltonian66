# Konstantin Fatykov

Python Backend Developer — I design and ship production data services, REST APIs, LLM integrations and agent tooling.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?logo=sqlalchemy&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?logo=celery&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)
![ClickHouse](https://img.shields.io/badge/ClickHouse-FFCC01?logo=clickhouse&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/CI-GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

### What I do

- ⚙️ Backend: FastAPI · asyncio · SQLAlchemy 2.0 · PostgreSQL · Redis · Celery / RabbitMQ · ClickHouse · Docker · CI/CD · pytest
- 🤖 AI in production: OpenAI & Whisper integrations, LLM summarization, RAG (pgvector + Claude), multi-role LLM pipelines with a human moderator in the loop, MCP servers and agent tooling
- 📍 Yekaterinburg, Russia · open to relocation (Moscow) and remote
- 🌐 English — B2

### Featured projects

**Orbita AI** *(private client project, in production)* — AI-first B2B platform that turns free-form purchase requests for engineering plumbing into supplier SKU selections, with a human moderator in the loop. Three independent LLM roles (parse → select → verify) behind a swappable provider (Claude Code CLI / Codex CLI). A single **operations layer** serves both ~100 HTTP routes and a **29-tool MCP server** (stdio + HTTP transports, personal tokens; dangerous actions are confirmed by a person, never by the model), an SSE assistant, an editable knowledge base where moderator decisions become selection rules only after approval, supplier price-list ingest (xlsx / xls) with catalog rebuild, golden-set regression, RBAC with sessions / CSRF / audit log, 900+ tests and a hardened VPS deployment (systemd units, Caddy, backups, metrics, fail2ban). FastAPI + SQLite.

**[English Lab](https://github.com/Miltonian66/english-lab)** — multi-user English-learning platform in Telegram: A1–C2 grammar course (221 rules, 1768 exercises), adaptive level diagnostic, SM-2 spaced repetition, listening, speaking practice with local **Whisper** transcription and **Piper** TTS, writing feedback, role-play dialogues and a grounded `/help` assistant over a verifiable knowledge base. Pure Python 3.11 stdlib core — own Telegram Bot API client, SQLite, no framework; pluggable LLM providers (Codex CLI / OpenAI / Anthropic), per-user sequential queues with isolated worker pools for LLM / STT / TTS, Telegram rate-limit backpressure, systemd deployment, 239 tests.

**[rag-service](https://github.com/Miltonian66/rag-service)** — Retrieval-Augmented Generation API: ingest documents → retrieve with **pgvector** → answer with cited sources via **Claude**. Async FastAPI + async SQLAlchemy 2.0, swappable embedding/LLM/vector-store providers, SSE streaming, Alembic, Docker, CI, offline test suite.

[Task-Tracker](https://github.com/Miltonian66/Task-Tracker) — async FastAPI task service: PostgreSQL + Redis cache with graceful degradation, unified error envelope with request_id, status state-machine, Alembic migrations, Dockerised (non-root + healthcheck), CI (ruff + pytest), 28 tests.

> ℹ️ Most of my commercial backend work is under NDA — marketplace integrations (Ozon / Wildberries / Yandex Market), CRM data pipelines, call transcription & AI summarization, ClickHouse analytics and the Orbita AI platform above. The public repositories here demonstrate the stack.

### Contact

- ✉️ konstantinfatykov03@gmail.com
- 💬 Telegram: [@whoismilton](https://t.me/whoismilton)
