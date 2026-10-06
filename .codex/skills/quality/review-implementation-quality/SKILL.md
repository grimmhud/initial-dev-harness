---
name: review-implementation-quality
description: Review planning or implementation against product, architecture, security, risk, and test strategy.
---

# Review Planning And Implementation Quality

Declare exactly one mode at the start of the handoff:

- `planning-review`: review a PRD/spec, including `blocked`, before implementation;
- `implementation-review`: review the diff and implementation evidence.

A `blocked` planning artifact may be `approved` when its blocker is honest and complete. This approves planning quality, not implementation or resolution.

1. Read product definitions and decisions, the PRD/spec, technical decisions, and handoffs; for implementation, read the full diff.
2. Confirm status/classification, scope, mockup/flow, file tree/impact, and acceptance criteria. For a blocker, confirm cause, resolution owner, impact, next step, objective unblock condition, and artifacts/criteria to revisit.
3. Find unreviewed business rules, product drift, regressions, contract errors, incomplete failure handling, architectural violations, secrets, sensitive data, accessibility gaps, and applicable responsive behavior.
4. When skills may become obsolete, verify the impact matrix, deterministic ownership, and order `skill_guard analyzes -> owners correct -> quality reviews -> applicable verifiers -> skill_guard audits`. Missing evidence, unjustified `no-impact`, wrong order, or self-approval requires `return-for-changes`.
5. Apply external-boundary and frontend-componentization skills when applicable.
6. Require unit tests for business rules and integration tests for flows/contracts.
7. Confirm tests would fail without the change and cover relevant risks.
8. For backend implementation, apply `verify-backend-flow` independently of implementer results.
9. Classify findings by severity and cite precise evidence.

Do not approve from the implementer's report alone, replace a selected `frontend_verifier`, or silently expand scope. Deliver the mode, decision (`approved`, `approved-with-caveats`, or `return-for-changes`), applicable backend checks, residual risks, and whether any blocker remains or was demonstrably resolved.

## Contract adherence

Review applicable feature Technical Design alongside PRD/spec and canonical rules. For root-selected short-flow maintenance, review recorded scope, acceptance, checks, and the risk justification in place of new planning artifacts. This exception does not exempt features from PRDs.

In planning review, confirm explicit rule semantics, GWT scenarios, risk-proportional test levels, applicable UI states and visual evidence expectations; reject unnecessary production or concrete test implementation in planning. In implementation review, map each relevant scenario and criterion to actual behavior and tests, including failure/edge cases. Passing tests alone do not establish contract adherence. Record missing coverage and visual evidence, and preserve verifier ownership.

Check planning traceability using `../../planning/create-spec-driven-plan/references/contract-traceability.md`: header precedes content, links resolve, effective replacement links are reciprocal without cycles (draft proposals remain explicitly pending), both sides identify canonical decisions, and old bodies retain historical semantics. Reject implementation based on superseded contracts or an unready successor. Current-contract status is not proof of implemented behavior; inspect completion evidence separately.
