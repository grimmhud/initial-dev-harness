---
name: manage-operational-memory
description: Initialize and maintain local operational memory for tasks, sessions, local checkpoints, stable context, runbooks, and recurring errors without replacing canonical documentation.
---

# Manage Operational Memory

Use with the root agent at project initialization, for substantial tasks, and whenever reusable operational context appears.

## Structure and ownership

```text
.codex/memory/
  START_HERE.md
  index.md
  active-task.md
  decisions/
  errors/
  projects/
  runbooks/
  sessions/
```

The directory may be local and Git-ignored. Recreate missing structure from `assets/templates/` before coordinating long work. The root agent initializes, updates, and promotes memory. Specialized agents provide facts and evidence in handoffs. `skill_guard` audits structural changes, hygiene, references, and absence of secrets.

## Procedure

1. Read `AGENTS.md`, the technical foundation, and existing memory.
2. Maintain `active-task.md` with objective, flow, planning, ledger, state, checks, and blockers.
3. Update the ledger after every real call and handoff.
4. Before writing a substantial task session, terminalize the ledger and record the final handoff/check.
5. Promote only reusable operational content: local non-canonical decision drafts to `decisions/`; stable verified context to `projects/`; validated repeatable procedures to `runbooks/`; recurring failures with proven causes to `errors/`. Durable product and technical decisions belong under `docs/decisions/`.
6. Update `index.md` when creating durable memory.
7. Finish with `active-task.md` terminal: `idle` when complete or `blocked` with cause, owner, and concrete next step.

## Hygiene

Memory does not replace Git, PRDs, specs, decision records, technical documentation, or an issue tracker. Prefer links to canonical sources; use repository-relative paths; record date, source, and status; never store secrets, credentials, raw personal data, dumps, long logs, or full transcripts; label uncertainty; never keep durable rules only in local memory; never reuse another project's history. Write the session summary last so it reflects terminal state.

Report updated files, promoted facts, referenced canonical sources, task-local items, and content deliberately omitted for safety or lack of confirmation.
