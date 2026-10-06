---
name: audit-agent-system
description: Audit changes to AGENTS.md, agents, skills, memory, planning, and routing to keep the system consistent and portable.
---

# Audit Agent System

## Required use

Use when changing `AGENTS.md`, `.codex/agents/**`, `.codex/skills/**`, structural memory, templates, or flow rules.

When a change to code, contracts, architecture, commands, tests, tooling, domain rules, business rules, or flows may affect operational knowledge, also apply `synchronize-affected-skills`: first inventory justified `update` and `no-impact` decisions; after owners correct artifacts, audit the final set. Do not implement every correction and then self-approve it.

For `guard/**`, analyze and request corrections, but require another existing agent designated by the root agent to implement them. The final sequence is `designated implementer -> quality -> skill_guard`.

## Checklist

- Required agents exist and their names match routing.
- `product` owns product definitions/rules and `docs/decisions/product/`; `planner` owns PRDs/specs; `architect` owns the technical foundation and `docs/decisions/project/`.
- Every TOML has `name`, `description`, and instructions covering role, limits, and handoff.
- Every skill has valid frontmatter, purpose, triggers, procedure, constraints, and delivery.
- References and paths exist and contain no unrelated product artifacts.
- `AGENTS.md`, agents, and skills do not conflict.
- Implementers and `quality` remain independent; `frontend_verifier` remains independent when selected. `Quality` may combine review and backend verification but never implements the change under review.
- Business-rule changes require `product`; material changes require explicit user confirmation.
- Potentially obsoleting changes have a `change -> source/artifact -> skills assessed -> update/no-impact -> owner/evidence` matrix and proof that stale instructions are gone. Domain/rule changes first have a `product` handoff.
- An operational browser MCP or `agent-browser` remains mandatory when `frontend_verifier` is selected.
- Frontend screenshots remain under `tmp/<feature-slug>/<deliverable>/<test-name>/` and their paths appear in the handoff.
- Ledger, `blocked`, `skipped`, and handoff remain defined.
- No secrets, sensitive data, generated files, or unrelated project details are present.
- Memory and templates provide a usable bootstrap.

Inspect the checklist above and record evidence. Deliver inconsistencies with paths, corrections, risks, and a decision.
