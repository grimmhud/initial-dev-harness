# AGENTS.md

This file defines the repository's operational invariants. The root agent coordinates the work: detailed routing, call order, and selection criteria belong to the root agent and its coordination skill.

## 1. Sources of truth

- The root agent may answer a request directly, without starting the coordinated flow, only when ALL of the following are true:
  - it is narrow and limited;
  - it can be answered from existing local state;
  - it is strictly read-only and does not change the worktree, index, refs, memory, cache, or external state;
  - it does not change any artifact;
  - it does not require specialized judgment, a readiness gate, an agent, review, or verification.
- If any criterion is not met, the root agent starts the coordinated flow.
- Agents configured in `.codex/agents/`, when selected, must be invoked through an actual agent tool. Simulating their roles or handoffs is not valid.
- A specialized agent defines **who acts** within its responsibility. A skill defines **how to act**. The root agent defines **when and in what order** each agent participates.
- The canonical product definition is `docs/product/product-definition.md`.
- Durable product decisions live in `docs/decisions/product/`; cross-cutting technical decisions live in `docs/decisions/project/`.
- PRDs and specs live in `docs/planning/`. Their opening traceability block records Status, Supersedes, Superseded by, and Related decisions. Effective replacement links are reciprocal; proposed draft replacements remain explicitly pending; historical bodies are preserved and `superseded` contracts are never executable. Change rationale remains canonical in `docs/decisions/`, not duplicated in planning.
- The cross-cutting technical foundation is `docs/project/technical-foundation.md`.
- Operational context lives in `.codex/memory/` and does not replace Git or product documentation.
- User instructions and approved specifications take precedence when they do not violate safety requirements.

## 2. Project contract

- product objective: `pending`; define it in `docs/product/product-definition.md` when adopting the harness;
- architecture and boundaries: `pending`; record them in `docs/project/technical-foundation.md` and `docs/decisions/project/`;
- stack and official commands: `pending`; discover and verify them during initial definition, never infer them from available agents;
- domain and security rules: `pending`; the root agent governs business semantics and architect owns technical trust boundaries;
- local conventions: generic harness rules apply until the adopting project records its own foundation and approved planning under `docs/planning/`.

Do not invent missing commands, architecture, or rules. Discover them in the repository or record the gap.

## 3. Readiness gates

- `docs/product/product-definition.md` must be `ready` before the technical foundation or feature planning begins.
- A feature must be `ready-for-planning` in the product catalog before its PRD is created.
- `docs/project/technical-foundation.md` must be `ready` before any implementation.
- Creating, changing, or removing a business rule requires product-governance review by the root agent using `define-and-govern-product`.
- Any change to code, contracts, architecture, commands, tests, tooling, domain rules, business rules, or flows that may make a skill obsolete triggers an impact analysis. `skill_guard` inventories and audits the impact, and artifact owners apply corrections before completion. Domain and business-rule changes require the root agent to update the canonical source first.
- A material or conflicting product change requires explicit user confirmation.
- When an applicable gate is not satisfied, dependent work becomes `blocked` and returns to the root agent with the cause and next step.

Gates are permanent and must not be removed once the project is ready. State belongs only in canonical documents and task memory, never in a duplicate backlog table in this file.

Feature flow: the root agent directly applies `define-and-govern-product` to record and release the feature; `planner` creates the PRD; the root agent records its path and status in the catalog without duplicating planning details. Product decisions remain subject to user authority; PRDs/specs remain owned by `planner`.

## 4. Available agents

| Agent | Responsibility |
|---|---|
| `planner` | Create a PRD or auditable specification |
| `architect` | Define and preserve the technical foundation, boundaries, and architectural decisions |
| `backend` | Implement backend changes and corresponding tests |
| `frontend` | Implement frontend changes and corresponding tests |
| `quality` | Review scope, risk, regressions, and coverage |
| `frontend_verifier` | Produce independent technical and operational frontend evidence |
| `skill_guard` | Analyze project-change impact on skills and audit consistency across rules, agents, skills, and memory |

Call, skip, blocking, parallelism, and check-ownership rules live in `.codex/skills/coordination/primary-agent-coordination/`. The root agent executes those rules directly and invokes configured agents only for specialized work.

## 5. Planning and implementation

Development has two distinct processes:

- **planning flow:** creates one PRD per initiative or feature and divides it into specs only when there is more than one deliverable;
- **implementation flow:** executes an `executable` PRD or an approved derived spec for features; simple local maintenance may use the documented short flow with explicit scope. It adds applicable tests, receives independent review, and produces proportional verification evidence.

Planning must clarify the problem, scope, out of scope, behavior, mockup or equivalent representation, expected file tree and high-level file impact, acceptance criteria, risks, and testing strategy. Each executable PRD or spec represents one complete, independently verifiable end-to-end deliverable.

Implementation must stay within the executable PRD/spec or the recorded short-flow maintenance scope. Every changed business rule requires unit tests. Every changed flow, contract, persistence path, or integration requires integration tests proportional to risk.

External integrations depend on capability-oriented internal contracts, replaceable adapters, and provider details contained at the boundary. Frontend code must be componentized according to demonstrated reuse or cohesive responsibility, without micro-componentization or speculative generalization.

The root agent selects the flow by complexity and risk before calling `planner`. Simple, local, low-risk maintenance may proceed with explicit scope, acceptance, and proportional checks without a new PRD/spec; every initiative or feature still requires a PRD. Record the reason and preserve applicable gates and independent quality invariants.

Conceptual feature flow: Product definition (root agent) -> PRD -> Technical Design when needed -> executable PRD or vertical specs -> implementation -> quality review -> applicable frontend/backend verification. `architect` produces or reviews explicit feature Technical Design for relevant architectural decisions, within planning or in a linked document; the technical foundation remains global.

Planning specifies behavior completely without anticipating production code or concrete test files. Short pseudocode, schemas, payloads, signatures, formulas, and input/output examples are allowed only to remove material ambiguity. Relevant behavior uses Given/When/Then scenarios. UI planning includes applicable interface states and visual evidence expectations; the verifier determines capture procedures and relates real evidence to criteria.

## 6. Quality invariants

- Implementers do not approve their own work alone.
- Changed code receives independent `quality` review.
- Every check reported as executed must have real evidence.
- Unavailable or non-applicable checks must be recorded with a reason.
- A blocked agent must report the cause and a concrete next step.
- Failures return to the owner of the proven cause; uncertain causes remain blocked until diagnosed.
- Changes to `AGENTS.md`, `.codex/agents/**`, `.codex/skills/**`, structural memory, or routing receive `skill_guard` review.

## 7. Safety and hygiene

- Never store real secrets, credentials, or raw sensitive data in code, logs, fixtures, documentation, or memory.
- Preserve the user's existing changes and keep the diff within scope.
- Never claim a verification succeeded unless it was executed.
- Destructive operations, publishing, and external changes require authorization consistent with the request.
- Record durable decisions, recurring errors, and runbooks only when they are reusable.

## 8. Final handoff

Every coordinated delivery reports: outcome; changed files; planning satisfied; participating agents; skipped steps and reasons; verifications and results; omitted verifications and reasons; blockers; risks; and remaining decisions.

A direct request reports only the result, the local evidence consulted, and any relevant limitation.
