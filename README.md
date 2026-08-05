# Hi, I’m Joshua

I’m a recent grad from Georgia Tech with my bachelor's in computer science passionate about **full-stack development (specifically backend development), infrastructure/systems programming, and OS design**.
This profile highlights some personal projects and relevant work.

---

## 🚀 Featured Projects

### 🔎 [RoleSignal](https://github.com/jsampson07/rolesignal)

A company-targeted job intelligence platform and explainable role-matching engine that helps job seekers find relevant roles across inconsistent ATS career pages.
- Built a TypeScript monorepo with a React frontend, Express API, PostgreSQL database, Prsma ORM, BullMQ worker, Redis queueing, and deterministic rule-based search.
- Implemented explainable job ranking with role-family, seniority, specialization, experience-aware entry/new-grad matching, match tiers, fallback groupings, and human-readable result explanations.
- Added ATS ingestion for Greenhouse, Lever, and Ashby, including source registration, raw payload storage, normalized job upserts, lifecycle tracking, closesure/reopen detection, and admin ingestion tooling.
- Developed authenticated saved searches with persisted check runs, new-match badges, in-app alert state, editable criteria, and per-user ownership controls.
- Created internal evaluation and benchmarking tools for search relevance, search performance, and ingestion metrics, with latest local validation covering 1300+ tests across API, web, and worker packages.

### 🎯 [Targeted Outreach Tool](https://github.com/jsampson07/inroad)
STATUS: Core pipeline demoable end-to-end (local); public deployment deliberately deferred (see docs)

A tool that discovers a plausible hiring contact for a target company, then drafts a resume↔JD-grounded cold email with an automated quality check — copy-paste only, the app never sends mail.
- Built a Python/FastAPI backend and React 19/TypeScript frontend around a multi-vendor `ContactProvider` interface (Hunter.io live, Apollo/Anymail Finder deferred, plus a scripted mock provider for development), using a status-result pattern so rate limits, errors, and empty results degrade gracefully instead of raising exceptions the orchestrator has to catch everywhere.
- Designed an LLM pipeline — structured resume/JD extraction, match/gap analysis, grounded email generation, and rubric-based evaluation — around a shared Anthropic API client wrapper with Pydantic-validated structured outputs at every call site.
- Built an LLM-as-judge eval step with three binary hard gates (no unsupported claims, correct contact name, no unprompted gap admission) and five graded dimensions, with a silent single retry on gate failure before a result is ever shown to the user.
- Implemented tiered contact discovery (recruiter → generalist TA → hiring manager → founder/CEO fallback) with a Postgres-backed cache for cross-user credit savings, and an explainable confidence signal built from provider verification tier, cross-provider corroboration, employment-currency, and domain checks.
- Hand-rolled JWT auth (short-lived access token + DB-backed revocable refresh token) over a 9-entity PostgreSQL schema (SQLAlchemy + Alembic) covering users, resumes, job descriptions, companies, raw per-provider results, contacts, generated emails, outcomes, and refresh tokens.

### 🖥️ [Distributed System](https://github.com/jsampson07/DistributedSystems/tree/main/gtstore)
A distributed key-value storage system (GTStore) supporting networked node communication and coordinated data storage.
- Focused on key distributed system properties including scalability, availability, and resilience to node failure.
- Applied lessons from systems design by building a multi-process distributed system from scratch, reinforcing understanding of practical distributed communication and data consistency strategies.
- Included comprehensive project documentation, tests, and reports detailing design decisions, performance considerations, and verification of correctness under simulated conditions.

### 🍎 [MacroTracker](https://github.com/jsampson07/Summer2025-Portfolio/tree/main/MacroTracker)
STATUS: Work in Progress

A full-stack nutrition tracking application. Currently minimal front-end functionality.
- **Backend:** Flask + SQLAlchemy + JWT auth, Python
- **Frontend:** React, JavaScript
- **Features:** Meal logging, macro tracking, progress summaries, register/log-in

---

## 🛠️ Skills Used
- **Languages:** TypeScript, Python, C++, SQL, JavaScript
- **Frameworks & Libraries:** React, Node.js, Express, FastAPI, Flask, SQLAlchemy, Prisma, BullMQ, gRPC, Protobuf, PyJWT
- **Tools & Platforms:** PostgreSQL, Redis, Docker, Git, Alembic
- **Applied AI:** Anthropic API — structured extraction, match/gap analysis, LLM-as-judge evaluation pipelines
- **Testing:** Vitest, Supertest, React Testing Library
---

## 📫 Connect
- [LinkedIn](https://www.linkedin.com/in/joshua-sampson)
