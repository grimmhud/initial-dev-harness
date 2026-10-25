# Routing

## Direct-request exception

The root agent may answer without coordinated flow only when ALL criteria hold: the request is narrow and limited; derives from existing local state; is strictly read-only with no worktree, index, refs, memory, cache, or external-state change; changes no artifact; and requires no specialist judgment, readiness gate, agent, review, or verification. Otherwise start the coordinated flow. Commit, push, editing, memory/cache updates, publishing, and external-state queries are not direct requests.

## Product gate

Before technical foundation or planning, read `docs/product/product-definition.md`:

- `ready` and sufficient: continue;
- `pending`, missing, or insufficient: the root agent directly applies `define-and-govern-product`;
- business rule added, changed, or removed: the root agent reviews the change using `define-and-govern-product` and updates the canonical source before calling `planner`;
- a change may obsolete skills: apply `synchronize-affected-skills`; for domain/rules, do so after the root agent updates the canonical source;
- a `material` or `conflicting` change: remain `blocked` until explicit user confirmation.

For a new feature: the root agent directly applies `define-and-govern-product`, records and releases the feature as `ready-for-planning`, then calls `planner`. Planner creates the PRD and returns its path; the root agent records the path and `planned` status in the catalog.

## Technical-foundation gate

Before selecting a flow, read `docs/project/technical-foundation.md`:

- `ready` and sufficient: continue;
- `pending`, missing, or insufficient: call `planner` and `architect` with `define-technical-foundation`;
- relevant capability `not-applicable`: do not call its agent;
- a required decision depends on the user: record `blocked` with the question and impact.

Backend and frontend are never assumed merely because agents exist. Availability does not mean selection.

## Planning flow

Use for PRDs, specs, technical decisions, or documentation that prepares implementation.

`root product governance when needed -> skill_guard impact inventory when applicable -> planner drafts PRD -> architect Technical Design when relevant -> planner consolidates executable PRD/specs -> assigned owners synchronize affected skills -> quality planning review -> skill_guard final audit when applicable -> root final`

If review fails, return to the responsible owner and repeat only the necessary correction and review stages. Planning does not implement product code.

## Implementation flow

Use when changing code, tests, contracts, persistence, integrations, or runtime.

`root business-rule governance when needed -> skill_guard impact inventory when applicable -> planner/architect by risk -> backend and/or frontend -> assigned owners synchronize affected skills -> quality review and backend verification -> frontend_verifier when selected -> skill_guard final audit when applicable -> root final`

Backend and frontend may work in parallel when scope and contracts are closed. `quality` always applies proportional `verify-backend-flow` when backend exists. `frontend_verifier` requires an operational browser backend once selected; unavailable tooling results in `blocked`, not a skip.

Select `frontend_verifier` for critical or multi-step flows, three or more screens/routes, global navigation/layout/state/design-system changes, shared components used across three or more screens, API contracts consumed by two or more screens, or verification at two or more named breakpoints/viewports/devices. For a small frontend change, the root agent may record a justified skip and require lightweight evidence from `frontend`.

Failures return to the owner of a proven cause. An uncertain cause remains blocked until diagnosed.

## Short flow

A short flow is a reduced planning or implementation flow for a simple, local, low-risk task—not a third process. Record skipped stages and preserve every `AGENTS.md` invariant.

## Planner selection and feature Technical Design

Assess complexity and risk before selecting `planner`. Simple, local, low-risk maintenance with known behavior may use explicit scope -> implementation -> proportional quality review. Record objective, scope, acceptance, checks, and why planning is skipped in task memory. This remains coordinated work, not the read-only exception. New initiatives/features still require a PRD and product catalog readiness; short flow does not bypass product review for changed rules or the foundation gate.

For features: Product definition (root agent) -> PRD -> conditional Technical Design -> executable PRD or vertical specs -> implementation -> quality -> applicable verification. Select `architect` for material boundary, data, concurrency, failure, security, compatibility, migration, or rollout decisions. Simple technical decisions stay in PRD/spec; relevant architecture needs explicit Technical Design produced or reviewed by `architect`, embedded or linked. Return the design to `planner` before declaring dependent contracts ready. Unresolved critical design blocks dependent implementation. Durable project-wide decisions also belong in an ADR and the current foundation.

The root chooses whether `frontend_verifier` is needed using the criteria above. Planning defines what visual behavior must be proven; the verifier chooses how, executes the real browser, and maps screenshots/evidence to criteria. Backend verification remains owned by `quality`; do not introduce a separate backend verifier agent.

## Replacing planned behavior

The root agent evaluates product changes and architect evaluates technical changes; each records the accepted canonical decision within that responsibility before planner replaces affected contracts. Apply planning's `create-spec-driven-plan/references/contract-traceability.md`: preserve historical bodies, reciprocal effective predecessor/successor links, and direct decision links on both sides. Reconcile catalog/index navigation via its owner. Never dispatch implementation from a superseded contract; unresolved successor readiness blocks dependent work. Document `active` is not evidence of runtime completion.

## Handoff and review ordering

The arrows describe stages coordinated by root, not permission for agents to dispatch each other. Root receives each handoff and selects the next stage. Inventory known skill impact before assigning corrections; if new impact emerges later, obtain/update the inventory before correcting those additional skills. Final audit is required only when skill/system impact warrants it, with a recorded reason otherwise.

Catalog `planned` records that a PRD exists; it is not execution approval. Root checks contract status, unresolved blockers, planning review, applicable Technical Design, parent PRD and dependency readiness before implementation. After design changes, planner reconciles contracts before quality review. A superseded parent PRD requires planner reconciliation even if a child spec still says ready. Root must not choose a replacement by filename or date alone.

For frontend-only work, root assigns shared technical checks to frontend_verifier when selected, otherwise to quality, using existing evidence where adequate. Backend work keeps shared checks with quality. If verification finds a proven defect, return it to its implementer and repeat affected review/verification before final audit; diagnostics alone do not make the reviewer an implementer.
