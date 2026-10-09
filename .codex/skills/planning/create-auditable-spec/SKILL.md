---
name: create-auditable-spec
description: Create or review a complete, end-to-end implementable specification provable through risk-proportional tests and verification.
---

# Create Auditable Spec

Use only for each deliverable derived from a `requires-specs` PRD.

A spec represents an observable, auditable deliverable—not an internal task. It must let implementers, quality, and verifiers work without inventing behavior or acceptance. Every spec is an end-to-end vertical slice that produces consumer-visible value and includes all layers needed to prove it. A schema-only, endpoint-only, UI-only, adapter-only, migration-only, or tests-only slice is invalid and belongs inside a vertical delivery or as an internal implementation task.

## Preconditions

- The technical foundation and product definition are `ready` and sufficient.
- Changed rules have a recorded root-agent product-governance review and updated canonical source and material-change confirmation.
- Critical dependencies and decisions are resolved or explicitly blocking.

## Required content

Include objective and auditable result; scope and out of scope; expected behavior/contracts/states; UI mockup or non-UI flow/contract/diagram; a hierarchical `text` file tree with one explicit root and expanded levels; one `create`, `modify`, or `delete` action on each terminal node; an exactly matching file-impact table; applicable data, persistence, integrations, external-boundary and frontend-componentization decisions; business rules; objective acceptance criteria; test and verification plan; risks, dependencies, and open questions.

A `blocked` spec uses the template's structured blocker with cause, resolution owner, artifact impact, next step, objective unblock condition, and items to revisit. Do not mark it `ready` while any unblock condition remains.

Every changed business rule plans a unit test. Every changed flow, contract, persistence path, or integration plans an integration test. Interfaces plan relevant states and operational verification.

The file tree rejects flat path lists, compressed `/` nodes, and brace expansion. Tree terminals and impact-table rows must match exactly in both directions. Use `assets/spec-template.md`.

Report the path, status, deliverable, criteria, tests/verifications, dependencies, and open questions.

## Behavior, not implementation

Specify rules and invariants explicitly from the canonical product source; never invent their semantics. Use objective language, decision tables, examples, edge cases, and Given/When/Then (GWT) scenarios for relevant rules, flows, contracts, states, and errors. Distinguish isolated unit-level rule scenarios from integration scenarios spanning components. Map scenarios to acceptance and the required test level.

Do not include production functions/classes/components, final queries, framework implementations, complete error handling, or copy-ready test files. Short pseudocode, formulas, expressions, schemas, payloads, important signatures, reference algorithms, and input/output examples are allowed only when they remove relevant ambiguity. The implementer chooses concrete code and test framework while preserving the contract.

Reference applicable feature Technical Design or embed simple technical decisions; do not duplicate the global foundation. Critical architectural questions return to `architect` before readiness.

For UI, consider initial, loading, success, empty, error, validation, permission denied, disabled, retry, and responsive states plus accessibility; justify non-applicable states. Include `Visual evidence expectations` describing states/results and relevant viewports to prove, not predetermined screenshot filenames or capture scripts. The verifier chooses how to obtain evidence and may add captures. For non-UI deliveries mark visual expectations not-applicable with a reason.

The test plan identifies scenarios, expectations, coverage, and acceptance mappings, not runnable test files. Unit tests are required for changed business rules; integration tests for changed flows/contracts/persistence/integrations. Contract, E2E, and browser tests are selected by consumer-observable risk, not mandated indiscriminately. Record reasons for omitted test levels.

Apply `../create-spec-driven-plan/references/contract-traceability.md` when creating or editing planning. Put the traceability header before other metadata/content, inspect existing contracts and decisions, preserve historical bodies, and maintain reciprocal effective replacement links and canonical decision references. Never treat `superseded` planning as executable; `active` denotes the current accepted contract, not completed implementation.
