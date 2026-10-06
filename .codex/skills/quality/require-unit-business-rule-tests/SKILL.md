---
name: require-unit-business-rule-tests
description: Require focused unit tests for every created or changed business rule.
---

# Require Unit Business Rule Tests

Require a unit test for an isolatable calculation, policy, permission, domain validation, state transition, normalization, decision, or invariant.

Prove the happy path, relevant boundary, invalid input or applicable error, and invariants. Prefer simple real dependencies or small fakes; mocks must not hide the decision. Endpoint-only tests do not replace unit tests when the rule is isolatable.

Report the rule, file, covered scenarios, omissions, and risk.

Planning describes isolated rule scenarios with Given/When/Then, expected outcomes, and coverage. Implementers translate them into the real test framework; planning must not contain ready-made test files. Quality checks scenario-to-test coverage and semantic adherence.
