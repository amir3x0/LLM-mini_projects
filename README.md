# Learning Ladder — Software Engineering for the AI Era

**Purpose.** A single repo to grow durable skills in the right order:
1) Databases & SQL → 2) Networking & APIs → 3) Distributed Systems → 4) Cloud & Ops → 5) Security & Privacy → 6) AI-native engineering → 7) Offline-first & CRDTs.

**How this works**
- Weekly cadence: 1 concept you can teach back, 1 micro-build (200–400 LOC), 1 short write-up (“Trade-offs I chose and why”).
- Measure everything: p50/p95 latency, error rates, (if AI) cost per call. Keep tiny dashboards or logs per build.
- Single source of truth: this repo. Subfolders per rung with READMEs and scripts.

## Repo structure
/db
  /builds/…             # small projects for this rung
  /notes.md             # concepts, gotchas, links
  /checkpoints.md       # what’s done, what’s next
/api
/dist
/ops
/sec
/ai
/crdt
README.md               # this file

## Current rung: 1) Databases & SQL
**Goals**
- Model a real domain (classes ↔ registrations with waitlists, soft deletes, auditing).
- Prevent invariants from breaking using constraints & transactions.
- Make slow queries fast using the right indexes and query plans.

**Deliverables**
- `/db/builds/classes/` containing:
  - `schema.sql`, `migrations/`, `seed.sql`
  - `queries.sql` (answers to defined questions)
  - `explain.md` (before/after plans with notes)
  - `tests/` (idempotency/double-booking checks)

**Definition of done**
- All core queries under target time on 10k–100k rows.
- No double-booking possible (proved by constraints/tests).
- README in the build folder explaining trade-offs.

## Conventions
- Prefer PostgreSQL (>=14) for SQL examples.
- Keep migrations small and numbered. Never edit history.
- Name indexes by intent: `idx_registrations_user_class_active`.
- Avoid `SELECT *` in app code; list needed columns.

## Cadence checklist (weekly)
- [ ] One 5-minute “teach-back” note
- [ ] One micro-build or refactor
- [ ] Metrics captured (latency/error/cost)
- [ ] Brief retrospective: bug or surprise + fix

## Roadmap
- 1) Databases ✅/🔜
- 2) Networking (HTTP/gRPC, idempotency, webhooks)
- 3) Distributed (queues/streams, Sagas)
- 4) Cloud & Ops (CI/CD, observability, autoscale)
- 5) Security & Privacy (OIDC, KMS, PII handling)
- 6) AI-native (RAG, evals, safety)
- 7) Offline-first & CRDTs (on-device DB, sync)
