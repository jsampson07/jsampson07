# Hi, I’m Joshua

I’m a recent grad from Georgia Tech with my bachelor's in computer science passionate about **full-stack development (specifically backend development), infrastructure/systems programming, and OS design**.
This profile highlights some personal projects and relevant work.

---

## 🚀 Featured Projects

### 🔎 [RoleSignal: Company-Targeted Search](https://github.com/jsampson07/rolesignal)

A company-targeted job intelligence platform and explainable role-matching engine that helps job seekers find relevant roles across inconsistent ATS career pages.
- Built a TypeScript monorepo with a React frontend, Express API, PostgreSQL database, Prsma ORM, BullMQ worker, Redis queueing, and deterministic rule-based search.
- Implemented explainable job ranking with role-family, seniority, specialization, experience-aware entry/new-grad matching, match tiers, fallback groupings, and human-readable result explanations.
- Added ATS ingestion for Greenhouse, Lever, and Ashby, including source registration, raw payload storage, normalized job upserts, lifecycle tracking, closesure/reopen detection, and admin ingestion tooling.
- Developed authenticated saved searches with persisted check runs, new-match badges, in-app alert state, editable criteria, and per-user ownership controls.
- Created internal evaluation and benchmarking tools for search relevance, search performance, and ingestion metrics, with latest local validation covering 1300+ tests across API, web, and worker packages.

### 🎯 [Inroad: Targeted Outreach Platform](https://github.com/jsampson07/inroad)
STATUS: Core pipeline demoable end-to-end (local); public deployment deliberately deferred (see docs)

A platform that discovers a plausible hiring contact for a target company, then drafts a resume↔JD-grounded cold email with an automated quality check — copy-paste only, the app never sends mail.
- Built a Python/FastAPI backend and React 19/TypeScript frontend around a multi-vendor `ContactProvider` interface (Hunter.io live, Apollo/Anymail Finder deferred, plus a scripted mock provider for development), using a status-result pattern so rate limits, errors, and empty results degrade gracefully instead of raising exceptions the orchestrator has to catch everywhere.
- Designed an LLM pipeline — structured resume/JD extraction, match/gap analysis, grounded email generation, and rubric-based evaluation — around a shared Anthropic API client wrapper with Pydantic-validated structured outputs at every call site.
- Built an LLM-as-judge eval step with three binary hard gates (no unsupported claims, correct contact name, no unprompted gap admission) and five graded dimensions, with a silent single retry on gate failure before a result is ever shown to the user.
- Implemented tiered contact discovery (recruiter → generalist TA → hiring manager → founder/CEO fallback) with a Postgres-backed cache for cross-user credit savings, and an explainable confidence signal built from provider verification tier, cross-provider corroboration, employment-currency, and domain checks.
- Hand-rolled JWT auth (short-lived access token + DB-backed revocable refresh token) over a 9-entity PostgreSQL schema (SQLAlchemy + Alembic) covering users, resumes, job descriptions, companies, raw per-provider results, contacts, generated emails, outcomes, and refresh tokens.

### 🔀 [Driftstore: Leaderless, Gossip-Coordinated Key-Value Store](https://github.com/jsampson07/driftstore)
STATUS: Phases 0–3 of 9 complete (gossip membership, consistent hashing, quorum
coordination); vector clocks, hinted handoff, and read-repair in progress —
see [PROGRESS.md](https://github.com/jsampson07/driftstore/blob/main/PROGRESS.md) for the phase-by-phase log.

The deliberate AP-inverted counterpart to GTStore below — same key-value
storage problem, every core decision flipped: gossip instead of centralized
heartbeats, consistent hashing instead of modulo, sloppy quorum instead of
write-all.
- Implemented Dynamo-style gossip membership (periodic push-pull table
  exchange, LWW + writer-id tiebreak merge) with local, per-node reachability
  tracking kept deliberately separate from cluster-wide membership state —
  they converge on different timescales for different reasons.
- Built consistent hashing with virtual nodes for data placement, choosing
  virtual-node count empirically by measuring load-distribution variance
  rather than picking arbitrarily.
- Any node can coordinate a request — no manager, no client-side fan-out —
  with tunable N/W/R sloppy quorum (N=3/W=2/R=2, R+W>N enforced for
  guaranteed read/write overlap).
- Debug primarily via structured, correlated logs across independent nodes
  plus reproducible bash harness scenarios (join, remove/reboot, replica-
  boundary, coordinator-rotation) — gdb is a fallback, not the default, since
  there's no single leader or log to step through.

### 🖥️ [Distributed System](https://github.com/jsampson07/distributed_gtstore)
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
