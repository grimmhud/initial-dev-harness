---
name: enforce-external-integration-boundaries
description: Define, plan, implement, review, and verify replaceable boundaries for APIs, SDKs, AI, payments, storage, queues, and other external integrations without provider lock-in.
---

# Enforce External Integration Boundaries

1. Name the boundary after the domain capability, not the brand. Use `provider`, `gateway`, `adapter`, `client`, or `repository` only when it describes the real responsibility.
2. Define a small stable internal contract. Keep business rules and consumers free of proprietary SDKs, types, payloads, errors, and codes.
3. Contain authentication, transport, serialization, rate limits, and provider quirks in the adapter. Translate external models and failures at the boundary.
4. Select implementations at an explicit composition point. A provider change should be concentrated in the adapter, configuration, and wiring unless capability or product behavior truly differs.
5. Use the simplest idiomatic mechanism that preserves replacement and testing; an abstract class is not mandatory.
6. Model timeouts, retries, idempotency, fallbacks, observability, and security according to risk. Never hide degradation or store secrets.
7. Prove consumers against the contract, adapters against the real boundary or a faithful fake, failure translation, and proportional replaceability.

In the handoff, report the capability, internal contract, adapter, composition point, replacement strategy, tests/evidence, and justified exceptions.
