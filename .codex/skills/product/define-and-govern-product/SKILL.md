---
name: define-and-govern-product
description: Define the product and govern business-rule changes, blocking material changes until explicit user confirmation.
---

# Define And Govern Product

Use with `product` during project initialization, whenever product context is missing, and whenever a business rule is created, changed, or removed.

## Canonical sources

`docs/product/product-definition.md` contains the consolidated current product view; `docs/product/references/` contains relevant sources and research; `docs/decisions/product/` contains durable product decisions owned by `product`. PRDs and specs remain in `docs/planning/` and belong to `planner`.

## Initial definition

1. Read the repository, existing documents, and provided references.
2. Separate proven facts, assumptions, and decisions requiring the user.
3. Define the problem, users, needs, value proposition, goals, scope, out of scope, capabilities, features, journeys, principles, business rules, metrics, constraints, and risks.
4. Run the system-completeness check before treating one requested feature as the whole product.
5. Return short prioritized questions through the root agent and update the product definition after each confirmed decision.
6. Mark `ready` only when the product can guide technical foundation and planning without invented intent.

## System-completeness check

A mentioned feature is a discovery entry point, not proof that it represents the entire system.

1. Describe the minimum end-to-end journey: data entry/creation, retrieval, maintenance/correction, presented result, and applicable error recovery.
2. Map the capabilities needed to deliver value without invisible or impossible user operations.
3. Group features as confirmed, required-but-pending, complementary/operational, or future/out-of-scope.
4. Record all identified relevant features. Keep unconfirmed items as `discovery` or `idea`. Begin the Notes cell with exactly one role marker: `Slice role: confirmed`, `Slice role: required-pending`, `Slice role: complementary`, or `Slice role: future-out-of-scope`.
5. Confirm every promised outcome has an observable configuration, input, retrieval, and correction path when applicable.
6. If the catalog has only the requested feature, explain why it is self-contained or keep the definition `pending` while adjacent capabilities are investigated.

This check reveals dependencies and gaps; it does not authorize scope inflation.

## Feature catalog

For each feature, record a stable slug/name, problem or value, related capability, product status, PRD path when present, and a short dependency/constraint/decision note.

`idea -> discovery -> ready-for-planning -> planned -> in-progress -> delivered -> deprecated`

`product` moves a feature to `ready-for-planning` when its objective, user, value, dependencies, and journey responsibility are clear. The root agent calls `planner`; `product` does not write the PRD. Once the PRD exists, record its path, set `planned`, and append the transition history. Keep scope, mockups, file trees, acceptance, and tests only in PRDs/specs. A technical initiative that adds no user-perceived capability may have a PRD without becoming a feature when planning records why.

## Business-rule governance

1. Compare the request with current definitions, decisions, and rules.
2. Identify affected features, users, journeys, contracts, data, metrics, and behavior.
3. Classify the change `compatible`, `material`, or `conflicting`.
4. For `compatible`, update the canonical source and hand impact to `planner`.
5. For `material` or `conflicting`, return `blocked` through the root agent with context, impact, alternatives, and a confirmation question. Do not accept or release the change yet.
6. After explicit confirmation, record a product decision, update the consolidated definition, and deliver the new product contract.
7. Flag the confirmed rule for `synchronize-affected-skills`. `product` provides canonical intent but neither edits nor approves the skills.

A change is material when it affects the core problem, target audience, value proposition, primary capability, critical journey, promised outcome, financial/pricing/permission/privacy/security/legal rules, destructive or irreversible behavior, user-visible compatibility, principal metric, fundamental constraint/principle, or an accepted product decision. When uncertain, classify it as material and expose the uncertainty.

## Confirmation authority

Silence, ambiguity, existing implementation, or an unaccepted recommendation is not confirmation. For every confirmed `material` or `conflicting` decision, preserve structured authority evidence—even after supersession—as `direct-choice`, `delegation`, or `accepted-recommendation`. Record a traceable source, short faithful summary, affected options, scope, and recorder without copying long transcripts or sensitive data. `not-applicable` is allowed only for `compatible` or never-confirmed `proposed` decisions.

## Limits and handoff

Do not choose stack/architecture/commands, create implementation PRDs/specs, edit code, convert references into confirmed requirements, or duplicate technical documentation. Report definition status, change classification, updated documents, affected rules, confirmed decisions, questions/blockers, impacts for `planner`/`architect`, remaining risks, and for initial definition a journey map, feature groups, and MVP-completeness rationale.

## Changes to existing planning

When any accepted change replaces a planned rule or behavior, including a `compatible` change, record its rationale, alternatives, and consequences in `docs/decisions/product/` before planner creates the replacement contract. Return decision path and affected planning scope through root; planner owns historical headers and reciprocal links. Update catalog navigation when the successor is accepted. Catalog `planned` indicates a PRD exists, not that blockers or execution gates are resolved.
