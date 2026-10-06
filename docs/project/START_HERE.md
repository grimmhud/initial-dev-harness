# Start Here

Follow this document first when starting a project. No implementation begins before the technical foundation is ready.

The user can start the full process by asking the root agent to conduct the initial definition. The root agent calls `product` first and `planner`/`architect` afterward, asks staged questions, and records answers; the user does not call each agent manually.

## Expected outcome

- Product and initial scope are clear.
- `docs/product/product-definition.md` is `ready`.
- Project type and capabilities are declared.
- Stack, architecture, structure, and official commands are defined.
- Agents reflect real technologies and responsibilities.
- Applicable generic skills are reviewed and required specialized skills are created.
- Local operational memory is initialized.
- `docs/project/technical-foundation.md` is `ready`.
- Work can be planned without agents inventing technical decisions.

## Required sequence

### 1. Define the product

The root agent calls `product` with `.codex/skills/product/define-and-govern-product/SKILL.md`. Record the idea, problem, users, value proposition, goals, scope, capabilities, features, journeys, business rules, references, constraints, metrics, and risks under `docs/product/`.

When a choice depends on preference, cost, or product tradeoff, `product` returns the question through the root agent instead of assuming. The technical foundation remains blocked while the product is `pending`.

### 2. Define the technical project

The root agent calls `planner` and `architect` with `.codex/skills/architecture/define-technical-foundation/SKILL.md`. Complete `docs/project/technical-foundation.md` with project type; `planned` and `not-applicable` capabilities; stack and versions; structure and ownership; architecture, boundaries, and contracts; configuration, data, integrations, and security; observability and quality attributes; official commands; testing and verification; and technical readiness criteria.

Set status to `ready` only when implementation and verification agents can work without inventing stack, structure, or commands.

### 3. Update project rules

Complete the **Project contract** in `AGENTS.md`. Keep only global rules and invariants there; detailed routing belongs to the root agent and `primary-agent-coordination`.

### 4. Adjust agents

Review `.codex/agents/` against defined capabilities. Applicable agents receive real references, stack, commands, and limits. Agents for `not-applicable` capabilities are not selected. Create a new agent only for a recurring distinct responsibility. Preserve independence between implementation, quality, and verification.

Do not remove a generic agent solely because the first feature does not use it; remove or replace it only for a durable project decision.

### 5. Finalize skills

Review `.codex/skills/`: preserve generic coordination, planning, implementation, quality, verification, memory, and guard skills; adapt technical skills only after deciding the stack; create reusable architecture, domain, security, and integration skills; keep templates/references beside their skill; remove examples and references unrelated to the project.

### 6. Initialize operational memory

Use `.codex/skills/memory/manage-operational-memory/SKILL.md`. Memory may be local and Git-ignored, but its structure must exist during work. Update `projects/project-context.md` only with stable context. Reference the canonical technical foundation instead of copying it.

### 7. Validate and release feature planning

Review the agent system using `.codex/skills/guard/audit-agent-system/SKILL.md` and record the evidence.

Then use `.codex/skills/planning/create-spec-driven-plan/SKILL.md` for the first PRD. Classify it as `executable` or divide it into specs. The technical foundation does not replace product and feature planning.

## Completion checklist

- [ ] Project contract completed in `AGENTS.md`.
- [ ] Product definition is `ready`.
- [ ] Initial business rules are recorded or explicitly pending.
- [ ] Initial features are cataloged with status and problem/value.
- [ ] Technical foundation is `ready`.
- [ ] Capabilities are `planned` or `not-applicable`.
- [ ] Agents are reviewed against capabilities and stack.
- [ ] Applicable skills are reviewed and references resolve.
- [ ] Local operational memory is initialized.
- [ ] Official commands run or are explicitly `not-applicable`.
- [ ] Agent-system review is complete and findings are resolved.
- [ ] First PRD is identified as the next step.
