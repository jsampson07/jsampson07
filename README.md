# Hi, I’m Joshua

I’m a recent grad from Georgia Tech with my bachelor's in computer science passionate about **infrastructure/systems programming, OS design, and full-stack development (specifically backend development)**.
This profile highlights some personal projects and relevant work.

---

## 🚀 Featured Projects

### 🔀 [Driftstore: Leaderless, Gossip-Coordinated Key-Value Store](https://github.com/jsampson07/driftstore)
STATUS: Phases 0–6 of 9 complete (gossip membership, consistent hashing, quorum
coordination, vector clocks, hinted handoff, read-repair); dashboard and
fault-injection harness remaining — see [PROGRESS.md](https://github.com/jsampson07/driftstore/blob/main/PROGRESS.md) for the phase-by-phase log.

A leaderless, gossip-coordinated distributed key-value store in C++ over
gRPC, staying available through node failures and network partitions with
no central coordinator.
- Built Dynamo-style gossip membership with push-pull table merge and last-writer-wins resolution, converging cluster view across nodes with no central registry.
- Implemented consistent hashing with virtual nodes for key placement, bounding remapping to ~1/N of the keyspace on any node join or leave.
- Enabled any node to coordinate a read or write via tunable sloppy quorum (N=3/W=2/R=2, R+W>N guarantees overlap), with no single point of coordination.
- Designed per-key vector clocks with causal dominance/concurrency detection and last-writer-wins resolution, backed by hinted handoff and read-repair to reconcile replicas without blocking writes.
- Verified correctness with 9 reproducible fault-injection scripts and dedicated unit tests, debugging via correlated structured logs across independently-running nodes instead of a debugger.
  
### 🖥️ [GTStore: Distributed Key-Value Store](https://github.com/jsampson07/distributed_gtstore)
A distributed, replicated, in-memory key-value store in C++ over gRPC, using a centralized manager for sharding, replica placement, and failure recovery, with a strong write-all consistency model.
- Sharded keys across N storage nodes via modulo hashing for deterministic, O(1) key→node lookup.
- Replicated each key onto K nodes via ring-based placement, tolerating up to K−1 node failures with no data loss.
- Enforced write-all, read-any strong consistency, with client-side read-before-write and rollback on partial-write failure.
- Detected dead nodes via manager-driven heartbeats and automatically re-replicated their partitions from a live backup.
- Benchmarked throughput across replication factors (200k ops, K=1/3/5), quantifying write-all's latency cost: 2561 → 1643 → 1199 ops/sec.

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
- Built a Python/FastAPI + React/TypeScript full-stack app around a multi-vendor `ContactProvider` interface (Hunter.io live, Apollo/Anymail deferred, mock for dev), using a status-result pattern so rate limits, errors, and empty results degrade gracefully instead of raising exceptions the orchestrator must catch.
- Designed an LLM pipeline — structured resume/JD extraction, match/gap analysis, grounded email generation, rubric evaluation — around a shared Anthropic client wrapper with Pydantic-validated structured outputs at every call site.
- Built an LLM-as-judge eval with three binary hard gates (unsupported claims, contact-name accuracy, unprompted gap admission) and five graded dimensions, silently retrying once on gate failure before a result reaches the user.
- Implemented tiered contact discovery (recruiter → generalist TA → hiring manager → founder/CEO) backed by a Postgres cross-user cache, with an explainable confidence signal from verification tier, cross-provider corroboration, employment-currency, and domain checks.
- Hand-rolled JWT auth (short-lived access + DB-backed revocable refresh tokens) over a 9-entity PostgreSQL schema (SQLAlchemy + Alembic) spanning resumes, job descriptions, contacts, generated emails, and outcomes.

---

## 🛠️ Skills Used
- **Languages:** C++, TypeScript, Python, SQL
- **Frameworks & Libraries:** gRPC, Protobuf, React, Node.js, Express, FastAPI, SQLAlchemy, Prisma, BullMQ, PyJWT
- **Tools & Platforms:** PostgreSQL, Redis, Bash, Docker, Git, Alembic
- **Applied AI:** Anthropic API — structured extraction, match/gap analysis, LLM-as-judge evaluation pipelines
- **Testing:** Vitest, Supertest, React Testing Library
---

## 📫 Connect
- [LinkedIn](https://www.linkedin.com/in/joshua-sampson)
