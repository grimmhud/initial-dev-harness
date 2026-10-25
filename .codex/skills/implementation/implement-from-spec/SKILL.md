---
name: implement-from-spec
description: Implement an executable PRD or approved spec end to end while preserving scope, architecture, tests, evidence, and independent handoff.
---

# Implement From Spec

This flow starts with a sufficiently ready executable artifact—an `executable` PRD or a spec derived from a PRD—and ends with the implementer's handoff to `quality`. Agent selection and later stages belong to the root agent.

For simple local low-risk maintenance, the root may explicitly select the short flow instead: recorded objective, scope, acceptance, and checks substitute for a new PRD/spec. This exception does not apply to new features, bypass applicable product/foundation gates, or waive proportional quality review. Apply artifact-specific preconditions below to feature work.

## Preconditions

1. Read `AGENTS.md`, the product definition, technical foundation, PRD, derived spec when present, applicable feature Technical Design, and applicable decisions.
2. For a changed business rule, confirm the root agent's documented governance review using `define-and-govern-product`, evidence of the updated canonical source, and explicit user confirmation for any material change.
3. Confirm the technical foundation is `ready` and the agent capability is `planned`.
4. Use the documented stack, structure, and official commands; do not choose silent substitutes.
5. Inspect opening traceability, related decisions, the parent PRD and required dependencies; a superseded parent requires planner reconciliation before executing its child spec; reject `superseded` contracts and follow successors, returning to root if none is executable. Confirm the selected contract has Status `ready` or `active` with readiness/gates satisfied, and is an `executable` PRD or an approved derived spec, with implementable objective, scope, mockup/flow, file tree/impact, behavior, and criteria.
6. If product, foundation, or executable planning is missing or insufficient, block and return to the root agent, identifying `planner` or `architect` as resolution owner when appropriate.

## Procedure

1. Map every acceptance criterion to changes and tests; use the acceptance-mapping asset for substantial work.
2. Preserve approved boundaries and contracts and implement the smallest complete change.
3. Apply external-integration and frontend-componentization skills when applicable.
4. Add unit tests for every created or changed business rule.
5. Add integration tests for every created or changed flow, contract, persistence path, or integration.
6. Cover risk-relevant states and failures, not only the happy path.
7. Run focused implementer checks and inspect the diff for out-of-scope changes, generated artifacts, and sensitive data.
8. When implementation may obsolete skills, return evidence to the root agent for `synchronize-affected-skills`. Domain/rule drift first requires the root agent's documented governance review using `define-and-govern-product` and evidence of the updated canonical source. Correct only skills assigned to your ownership as `update` in the matrix.
9. Deliver a reproducible handoff to `quality` and selected verifiers.

## Backend and frontend

Backend work validates boundaries, keeps business rules outside I/O adapters, handles external failures/transactions/idempotency/compatibility as applicable, and avoids leaking internals or secrets. Frontend work covers applicable loading, error, empty, success, and validation states; preserves accessibility, keyboard navigation, and responsiveness; respects real API contracts; and identifies routes, flows, and viewports for operational verification.

## Constraints and handoff

Do not expand scope, silently rewrite the spec, replace automatable tests with manual claims, or approve your own work. Report the executable PRD/spec, criteria satisfied, changed files, authorized decisions or deviations, tests and check results, checks expected from reviewers/verifiers, risks, limitations, and pending work.

Assets:

- `assets/acceptance-mapping-template.md`
- `assets/implementation-handoff-template.md`

Translate behavioral GWT scenarios into real framework tests and map them to criteria. Choose concrete implementation without altering rule semantics; planning snippets clarify contracts and are not prescribed production code. Include initial, disabled, retry, and permission-denied UI behavior when applicable, alongside other required states. Return evidence for the visual expectations to the selected verifier.
