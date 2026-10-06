---
name: define-technical-foundation
description: Define a project's cross-cutting technical foundation without assuming backend or frontend and without duplicating feature specifications.
---

# Define Technical Foundation

Use this skill with `planner` and `architect` when `docs/project/technical-foundation.md` is `pending`, missing, or insufficient.

Precondition: `docs/product/product-definition.md` is `ready` and sufficient. The technical foundation must not fill product gaps.

## Goal

Turn known product needs into an explicit, verifiable, cross-cutting technical baseline. Features and their implementations remain in PRDs and specs.

## Required discovery

1. Read `AGENTS.md`, the repository, and product documentation.
2. Read `docs/decisions/project/`; identify existing decisions, evidence, and choices that require the user.
3. Determine the project type without assuming backend or frontend.
4. Mark absent capabilities `not-applicable` and open decisions `pending`.
5. Do not place feature mockups, acceptance criteria, or file impact in the foundation.

## User interview

Return to the root agent only decisions that require the user, with context, impact, and viable alternatives. Ground stack and architecture in the product definition. Do not ask for details agents can safely discover or recommend.

## Minimum content

Complete `docs/project/technical-foundation.md` from `assets/technical-foundation-template.md` with: technical goal and project type; planned and non-applicable capabilities; stack, runtimes, package managers, and versions; initial structure and ownership; architecture, boundaries, allowed dependencies, and shared contracts; configuration and environments; data, persistence, and migrations; external integrations, internal contracts, adapters, composition, and replaceability; security, observability, and quality attributes; official commands; test and verification strategy; browser automation backend and preflight when frontend exists; shared conventions and proportional frontend componentization criteria; open decisions and risks.

Record a durable cross-cutting technical choice in `docs/decisions/project/` when it needs its own context, alternatives, and consequences. Keep only the consolidated current state in the foundation.

## Status

- `pending`: required cross-cutting decisions are missing.
- `ready`: agents can plan and implement without inventing stack, structure, or commands.
- `superseded`: another referenced foundation is now authoritative.

Do not mark `ready` merely because the template is filled. Decide applicable fields and explicitly mark all others `not-applicable`.

## Responsibilities

- `planner` clarifies capabilities, constraints, and planning needs.
- `architect` defines alternatives, boundaries, feasibility, and quality attributes.
- The root agent tracks gaps and blocks premature implementation.
- The user decides choices involving preference, cost, or unresolved risk.

## Limits and handoff

Do not define product features or rules, include delivery-specific mockups or file trees, or replace a PRD/spec. Report status, project type, capabilities, decisions and rationale, `not-applicable` fields, open questions, risks, and whether planning or implementation is unblocked.

Feature-local Technical Design belongs in or alongside the PRD/spec and is produced/reviewed through `review-architecture-flow`; it does not require a new foundation document. Only durable cross-cutting decisions update the global baseline and applicable ADRs.
