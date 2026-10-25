---
name: require-integration-flow-tests
description: Require integration tests for changed flows, contracts, persistence, and external boundaries.
---

# Require Integration Flow Tests

Require integration coverage when changing an endpoint, contract, orchestrating use case, persistence, queue, adapter/gateway, external integration, or complete interface flow.

Select risk-proportional scenarios: success, invalid input, empty, partial, missing, permission, conflict, external failure, timeout/retry, idempotency, and request/response contract. Do not mock so many layers that integration is no longer proven. Never use real secrets.

For external boundaries, apply `enforce-external-integration-boundaries`: prove that consumers use the internal contract, the adapter translates requests/responses/failures, and composition selects the implementation without leaking provider details. Use a faithful fake or sandbox when the real API is unsafe or nondeterministic.

Report the flow, file, scenarios, fakes/mocks and rationale, gaps, and risk.

Planning describes interaction across components scenarios with Given/When/Then, expected outcomes, and coverage. Implementers translate them into the real test framework; planning must not contain ready-made test files. Quality checks scenario-to-test coverage and semantic adherence.
