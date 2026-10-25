---
name: review-architecture-flow
description: Review placement, dependencies, contracts, data, and external effects without imposing a product-specific architecture.
---

# Review Architecture Flow

## Use when

A new module, boundary change, dependency, public contract, persistence, integration, security concern, critical flow, or durable technical decision is involved.

## Procedure

1. Read the product definition, project contract, actual structure, specs, and existing decisions. Never use architecture to fill a product gap.
2. Read `docs/project/technical-foundation.md` and `docs/decisions/project/`. If the foundation is `pending`, help `planner` complete it after the product is sufficient.
3. Map affected components and dependency direction.
4. Separate business rules, orchestration, and I/O according to local conventions.
5. Define contracts, data ownership, transactions, idempotency, and failure handling when applicable.
6. Assess compatibility, migration, observability, security, and testability.
7. Record a durable decision in `docs/decisions/project/` when it guides more than one future feature, module, or flow. Keep delivery-local decisions in the PRD/spec or its linked Technical Design.

Block cycles, inverted dependencies without clear ports, business rules in adapters/UI, external details leaking into the domain, ambiguous ownership, irreversible migrations without a strategy, or assumed critical contracts.

Apply `enforce-external-integration-boundaries` and `enforce-frontend-componentization` independently when applicable. Report the decision, alternatives, tradeoffs, boundaries, files, risks, rollout/migration, and expected verification.

## Feature Technical Design

Keep simple technical decisions inside the PRD/spec. For relevant architectural decisions, produce or review explicit Technical Design embedded there or linked as `docs/planning/<area>/<feature-slug>/<feature-slug>-technical-design.md`. A separate file is optional, not a readiness condition by itself.

Cover affected components, contracts, data, synchronous/asynchronous behavior, concurrency, failure modes, security, observability, migration, rollout, and compatibility where applicable; record rationale for non-applicable concerns, alternatives, decisions, risks, and verification implications. Link to source PRD and dependent specs. Do not write production implementations or redefine business semantics. Unresolved critical decisions block dependent readiness and return to root/planner.

Feature design explains how the delivery fits the system; `docs/project/technical-foundation.md` remains the global stack/architecture/commands/test/infrastructure baseline. Promote durable project-wide decisions to ADRs and synchronize the foundation rather than copying feature detail into it.

For a technical change that replaces an existing planned contract, record the change decision in `docs/decisions/project/` even when the impact is feature-local. Return that decision path and affected contracts through root to planner for traceability. This replacement-decision requirement is distinct from promoting only cross-cutting design choices into the global foundation; do not duplicate the canonical rationale inside the successor.
