---
name: synchronize-affected-skills
description: Synchronize skills affected by changes to code, contracts, architecture, commands, tests, tooling, domain rules, business rules, or flows through impact analysis, owner corrections, and an independent skill_guard audit.
---

# Synchronize Affected Skills

## Goal

Keep skills aligned with current repository sources and artifacts without turning evidence into authority or permitting self-approval.

## Deterministic ownership

- Canonical ownership follows the change: the root agent governs domain, business rules, and product decisions; `architect` governs the technical foundation and project decisions; PRDs/specs, contracts, official commands, and other artifacts retain their repository-defined owners.
- `skill_guard` inventories affected skills, requests corrections, and audits the final set.
- For `product/**`, the root agent defines and validates canonical intent under user authority and assigns a capable existing agent to implement skill corrections; independent `quality` review and `skill_guard` audit remain required.
- `planning/**` belongs to `planner`; `architecture/**` to `architect`; `implementation/**` to `backend` or `frontend` by scope; `quality/**` and `verification/verify-backend-flow` to `quality`; other `verification/**` skills to the matching verifier, while preserving independent review.
- For `coordination/**`, `memory/**`, `guard/**`, `.codex/agents/**`, `AGENTS.md`, and cross-cutting scripts, the root agent assigns a capable existing agent.
- If the natural owner must also perform mandatory final review, verification, or audit, assign another capable implementer.
- For `guard/**`, `skill_guard` only analyzes, requests corrections, and audits; another agent implements and `quality` reviews.
- The root agent records owners, designated implementers, handoffs, blockers, and evidence in the ledger.

## Procedure

1. Identify the change and its authoritative source or artifact.
2. Confirm acceptance by the applicable source owner. Domain or business-rule changes require a recorded root-agent governance review, classification, and updated canonical source; divergent code is only drift evidence. Block when authority is missing.
3. Ask `skill_guard` to analyze all potentially affected skills, agents, templates, references, and routing rules.
4. Record the required `change -> source/artifact -> skills assessed -> update/no-impact -> owner/evidence` matrix. Every candidate receives a justified result.
5. Route each `update` by ownership, recording natural owner and designated implementer when different. Change behavior, triggers, constraints, examples, and checks only where required.
6. Inspect structural contracts, run applicable available checks and focused tests, and search for obsolete terminology or behavior. Text search alone does not prove completeness.
7. Have `quality` review the corrected set. Select verifiers only when risk, scope, or applicable invariants give them concrete work; otherwise record the skip reason.
8. Return the final system to `skill_guard` for independent audit. Findings return to the responsible implementer and repeat only necessary stages; an uncertain cause remains blocked.
9. Finish only when sources, matrix, corrections, `no-impact` decisions, and evidence agree.

## Constraints and handoff

Do not copy details into every skill, update canonical sources from divergent implementation alone, hide conflicts, let `skill_guard` implement and approve all corrections, or claim complete synchronization without the matrix and final audit. Report the change and source, authority, full matrix, owners and corrected files, checks and results, audit, blockers, and residual risks.
