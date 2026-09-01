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

### 🔀 [Driftstore: Leaderless, Gossip-Coordinated Key-Value Store](https://github.com/jsampson07/driftstore)
STATUS: Phases 0–3 of 9 complete (gossip membership, consistent hashing, quorum
coordination); vector clocks, hinted handoff, and read-repair in progress —
see [PROGRESS.md](https://github.com/jsampson07/driftstore/blob/main/PROGRESS.md) for the phase-by-phase log.

The deliberate AP counterpart to GTStore above — same key-value problem,
every core decision inverted: gossip instead of centralized heartbeats,
consistent hashing instead of modulo, sloppy quorum instead of write-all.
- Built Dynamo-style gossip membership (push-pull merge, LWW conflict
  resolution), keeping local failure detection separate from gossiped
  membership — they converge on different timescales, for different reasons.
- Replaced modulo hashing with consistent hashing + virtual nodes, bounding
  key remapping to ~1/N of the keyspace on node join/leave; virtual-node
  count sized empirically via measured load-distribution variance.
- Enabled any node to coordinate a request (no manager, no client fan-out)
  via tunable sloppy quorum (N=3/W=2/R=2, R+W>N guarantees overlap).
- Debug via structured, correlated logs across independent nodes and
  reproducible failure-injection scripts, not gdb — no single leader or
  log to step through.

### 🎯 [Inroad: Targeted Outreach Platform](https://github.com/jsampson07/inroad)
STATUS: Core pipeline demoable end-to-end (local); public deployment deliberately deferred (see docs)

A platform that discovers a plausible hiring contact for a target company, then drafts a resume↔JD-grounded cold email with an automated quality check — copy-paste only, the app never sends mail.
- Built a Python/FastAPI + React/TypeScript full-stack app around a multi-vendor `ContactProvider` interface (Hunter.io live, Apollo/Anymail deferred, mock for dev), using a status-result pattern so rate limits, errors, and empty results degrade gracefully instead of raising exceptions the orchestrator must catch.
- Designed an LLM pipeline — structured resume/JD extraction, match/gap analysis, grounded email generation, rubric evaluation — around a shared Anthropic client wrapper with Pydantic-validated structured outputs at every call site.
- Built an LLM-as-judge eval with three binary hard gates (unsupported claims, contact-name accuracy, unprompted gap admission) and five graded dimensions, silently retrying once on gate failure before a result reaches the user.
- Implemented tiered contact discovery (recruiter → generalist TA → hiring manager → founder/CEO) backed by a Postgres cross-user cache, with an explainable confidence signal from verification tier, cross-provider corroboration, employment-currency, and domain checks.
- Hand-rolled JWT auth (short-lived access + DB-backed revocable refresh tokens) over a 9-entity PostgreSQL schema (SQLAlchemy + Alembic) spanning resumes, job descriptions, contacts, generated emails, and outcomes.

### 🖥️ [GTStore: Distributed Key-Value Store](https://github.com/jsampson07/distributed_gtstore)
A distributed, replicated, in-memory key-value store in C++ over gRPC, using a centralized manager for sharding, replica placement, and failure recovery, with a strong write-all consistency model.
- Sharded keys across N storage nodes via modulo hashing for deterministic, O(1) key→node lookup.
- Replicated each key onto K nodes via ring-based placement, tolerating up to K−1 node failures with no data loss.
- Enforced write-all, read-any strong consistency, with client-side read-before-write and rollback on partial-write failure.
- Detected dead nodes via manager-driven heartbeats and automatically re-replicated their partitions from a live backup.
- Benchmarked throughput across replication factors (200k ops, K=1/3/5), quantifying write-all's latency cost: 2561 → 1643 → 1199 ops/sec.

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
- **Tools & Platforms:** PostgreSQL, Redis, Bash, Docker, Git, Alembic
- **Applied AI:** Anthropic API — structured extraction, match/gap analysis, LLM-as-judge evaluation pipelines
- **Testing:** Vitest, Supertest, React Testing Library
---

## 📫 Connect
- [LinkedIn](https://www.linkedin.com/in/joshua-sampson)
