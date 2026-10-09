---
name: primary-agent-coordination
description: Guide the root agent from intake to handoff with real agent routing, a ledger, memory, verification, and explicit blockers.
---

# Primary Agent Coordination

## When to use

Use this in the root agent for every request that does not fully satisfy the direct-request exception, especially multi-agent, substantial, risky work or changes to rules, agents, skills, or structural memory. This skill is not a selectable agent and must not be delegated to an orchestration subagent.

The direct-request exception applies only when ALL criteria hold: the request is narrow and limited; derives from existing local state; is strictly read-only with no worktree, index, refs, memory, cache, or external-state change; changes no artifact; and requires no specialist judgment, readiness gate, agent, review, or verification.

## Procedure

1. Read `AGENTS.md`, the product definition, technical foundation, memory skill, stable context, and `active-task.md`; initialize memory if needed.
2. If the product definition is missing, `pending`, or insufficient, directly apply `define-and-govern-product` before technical planning, architecture, or implementation.
3. Directly review every business-rule addition, change, removal, or domain conflict using `define-and-govern-product` and update the canonical source. Keep material or conflicting changes `blocked` until explicit user confirmation.
4. For a change that may make skills obsolete, apply `synchronize-affected-skills`; record the impact matrix, correction owners, and final `skill_guard` audit.
5. When the product is sufficient but the technical foundation is not, apply `define-technical-foundation` with `planner` and `architect` before implementation.
6. Discover feature planning and repository state, then classify the task as planning or implementation. Assess complexity/risk before selecting `planner`; use a short flow for simple local maintenance only with recorded scope, acceptance, checks, and justification. Features still require PRDs. Apply the conditional Technical Design routing in `references/routing.md`.
7. Select agents and create the ledger before calling them. Invoke each through a real agent tool and update `selected` to `called`, then `handoff_received` or `blocked`.
8. Update `active-task.md` after each meaningful phase.
9. Require `quality` for code. With backend, `quality` also applies `verify-backend-flow`. Select `frontend_verifier` by the routing rules. Require `skill_guard` for agent-system changes or affected-skill synchronization.
10. Promote only durable information to decisions, projects, runbooks, or errors.
11. Before completion, terminalize the ledger, incorporate the last handoff, leave `active-task.md` `idle` or `blocked`, write the session, and produce the final handoff. Use repository-relative paths in memory.

## Initial-definition mode

1. The root agent gathers what can be established from the repository, references, and documents.
2. The root agent consolidates only product decisions that truly require the user.
3. Ask short staged questions, explaining why each answer matters and what it unlocks.
4. After each answer, the root agent updates the product definition; update `AGENTS.md` only for global rules and update operational memory with state and gaps.
5. Repeat until applicable fields are decided or `not-applicable`.
6. Present a summary for confirmation before marking the product `ready` and starting the technical foundation.

Do not turn the conversation into a long form, ask for discoverable facts, or present an unconfirmed preference as a decision.

## Ledger

| Agent | Reason | Required? | Status | Handoff | Notes |
|---|---|---:|---|---|---|
| planner | scope/spec | conditional | selected | pending | - |

Record direct root-agent product governance as task phases and canonical evidence, not as a specialist call or self-handoff.

Statuses: `selected`, `called`, `handoff_received`, `skipped`, `blocked`. A skip needs a reason. A blocker needs a cause and next step. Never finish with `selected` or `called`.

## Constraints

- The root agent coordinates and performs only work that legitimately belongs to the primary role. Product definition, catalog maintenance, and business-rule governance belong directly to the root agent through `define-and-govern-product`, subject to user decision authority. It does not absorb other specialist responsibilities, self-approve its delivery, or simulate required agents.
- Do not duplicate checks across verifiers.
- Manage memory with `manage-operational-memory`; never use it as a Git or documentation substitute.
- Never store secrets or raw sensitive data.

## References

- `references/routing.md`
- `references/memory.md`
- `references/final-handoff.md`
