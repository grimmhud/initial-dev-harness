---
name: verify-backend-flow
description: Guide quality through independent, reproducible checks of backend behavior, contracts, and local operation.
---

# Verify Backend Flow

Use with `quality` in `implementation-review` when a delivery includes backend work. This skill complements diff review with independent operational verification; it is not a separate agent.

Discover commands in manifests, CI, Makefiles, and documentation. When present, run focused tests and the suite, lint/format checks, type checks, build/import/startup, safe-environment migrations, health/smoke checks, and contract calls. Run `git diff --check` in a Git repository.

Start with the most focused check, then broaden. Never invent commands or success, and do not modify product behavior during verification. If a check does not exist or an external dependency blocks it, record the reason and next step. With backend work, `quality` owns shared checks and prevents duplication.

For external integrations, apply `enforce-external-integration-boundaries` and confirm through tests/evidence that internal contract, adapter, and composition remain separate, failures are translated, and provider dependencies do not leak into business rules. A proportional replaceability test may replace an actual provider swap.

Include every command, exit status, evidence summary, omitted check, failure, and routing decision in the `quality` handoff.
