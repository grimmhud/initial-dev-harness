---
name: create-spec-driven-plan
description: Create one PRD per initiative or feature and decide whether it is directly executable or requires auditable specs.
---

# Create Spec-Driven Plan

Every planned initiative or feature gets a PRD. It may be directly executable when it is one small or medium, closed, clear, verifiable delivery. Create specs only to divide it into two or more independent or sequential deliverables.

If the technical foundation is missing, `pending`, or insufficient, apply `define-technical-foundation` first. If the product definition is `pending` or a business-rule change lacks a `product` handoff, return to the root agent.

## Flow

1. Discover context and existing planning.
2. Define objective, scope, out of scope, and open questions.
3. Create the PRD with `create-prd` and classify it `executable` or `requires-specs`.
4. Assess feature Technical Design with the root agent; relevant architecture requires `architect` production/review of an embedded or linked design before dependent contracts are ready. For `executable`, ensure the PRD contains behavior, file tree/impact, acceptance, and test plan sufficient for implementation.
5. For `requires-specs`, create each end-to-end vertical slice with `create-auditable-spec`; never create a purely technical spec.
6. Include a mockup for UI work or equivalent flow/contract/diagram for non-UI work.
7. Evaluate external-integration boundaries and frontend componentization independently.
8. Plan GWT scenarios and unit tests for created/changed business rules, integration tests for changed flows/contracts/persistence/integrations, and other test levels by risk. Describe expected behavior and coverage, not production or test implementation. Include applicable UI states and visual evidence expectations.
9. Validate every file tree: `text` block, explicit common root, complete hierarchy, terminal actions, no flat/compressed/brace form, and exact match to the impact table.
10. Record dependencies, risks, and status without inventing decisions. Use structured blockers when needed.

Coordination assets: `assets/spec-index-template.md` and `assets/decisions-template.md`.

The plan is ready when the PRD exists with explicit classification, closed scope and behavior, clear visual/flow representation and file impact, tests that prove each delivery, and all critical gaps resolved. An explicitly documented critical gap leaves the affected artifact `blocked`; approval of the blocker representation does not make it executable.

## Existing contracts and replacement

Apply `references/contract-traceability.md` to every PRD/spec. Before planning changed behavior, find existing contracts and read canonical decisions. Product/architect owns the change decision in `docs/decisions/`; planner creates the replacement, preserves the old body, updates reciprocal Supersedes/Superseded by links and Related decisions on both sides, and reconciles current/historical navigation. A `superseded` document cannot pass executable readiness. Status describes contract lifecycle, not implementation completion.
