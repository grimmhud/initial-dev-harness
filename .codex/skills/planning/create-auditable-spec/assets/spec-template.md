# [Spec name]

Status: `[draft|blocked|ready|active|superseded]`

Supersedes:

- `[document link|none]`

Superseded by:

- `[document link|none]`

Related decisions:

- `[canonical decision link|none]`

Related PRD: `[path|not-applicable]`

## Summary and objective
## Auditable deliverable

Consumer-visible result: `[describe]`
End-to-end vertical slice: `[interfaces/layers included to produce and prove the result]`

A schema-only, endpoint-only, UI-only, adapter-only, migration-only, or tests-only spec is an invalid technical slice. Include that work in a vertical delivery.

## Scope
## Out of scope
## Expected behavior and contracts
## Business rules and invariants

Reference canonical rules and make decision conditions, edge cases, and invariants explicit.

## Behavioral scenarios

For relevant behavior, identify the criterion and expected test level. Describe contracts, not production code or runnable test files. For a requires-specs PRD, summarize and reference derived scenarios instead of duplicating them.

### Unit-level scenarios

Scenario: `[isolated business rule and criterion, or not-applicable with reason]`
Given `[precondition]`
When `[action]`
Then `[observable outcome/invariant]`

### Integration scenarios

Scenario: `[flow across components and criterion, or not-applicable with reason]`
Given `[state and dependencies]`
When `[interaction]`
Then `[observable contract, persistence or failure outcome]`

## Interface states and accessibility

Consider initial, loading, success, empty, error, validation, permission denied, disabled, retry, and responsive states. Identify applicable keyboard/focus/accessibility behavior and justify non-applicable states. For requires-specs PRDs, detail states in derived specs.

## Visual evidence expectations

State what must be proven: initial view, successful result, validation/error, empty state, and applicable named viewports (for example 390px mobile and 1440px desktop). Choose viewports by the delivery, not as universal defaults. Map expectations to acceptance criteria. The verifier chooses captures/filenames and may add evidence. For non-UI work, record not-applicable and why.

## Feature Technical Design

`[embedded decision/design or link | not needed with rationale]`
Architect production/review: `[required for relevant architecture; evidence/status | not-applicable]`
Critical unresolved decisions block dependent readiness. Keep global decisions in the foundation/ADRs.

## Mockup or equivalent representation

Required: mockup for a UI; flow, contract, sequence, or diagram for backend, CLI, or non-UI integration.

## Expected file tree

```text
./
├── <main-area>/
│   ├── <subarea>/
│   │   ├── <new-file.ext> [create]
│   │   └── <existing-file.ext> [modify]
│   └── <tests>/
│       └── <test-file.ext> [create]
└── <configuration>/
    └── <obsolete-file.ext> [delete]
```

Use one explicit common root and draw every level with connectors. Do not use a flat list, compressed `/` paths, or brace expansion. Actions belong on terminal nodes, and terminals must exactly match the table below.

## High-level file impact

| File | Action | Change responsibility |
|---|---|---|
| `<main-area>/<subarea>/<new-file.ext>` | `create` | `[summary]` |
| `<main-area>/<subarea>/<existing-file.ext>` | `modify` | `[summary]` |
| `<main-area>/<tests>/<test-file.ext>` | `create` | `[summary]` |
| `<configuration>/<obsolete-file.ext>` | `delete` | `[summary]` |

## Data, persistence, and integrations
## Applicable architectural practices

- External integrations: `[capability and internal contract; adapter; composition point; model/failure translation; replacement strategy; tests|not-applicable]`
- Frontend: `[extracted units and reuse/responsibility evidence; local sections; props/data contracts; tests|not-applicable]`

## Observability and operations
## Test plan
Describe scenarios, expectations, required coverage and criterion mappings. Select levels proportionally to risk; justify omissions. Do not include concrete test files.

### Business-rule unit tests
### Required integration test
### Contract or end-to-end tests
### Manual or browser verification
## Acceptance criteria
## Risks and mitigations
## Dependencies and open questions

## Structured blocker

Complete when `Status: blocked`; otherwise use `not-applicable` everywhere.

- Cause: `[proven cause|not-applicable]`
- Resolution owner: `[user|root agent|planner|architect|other agent|not-applicable]`
- Artifact impact: `[what cannot proceed|not-applicable]`
- Next step: `[concrete action|not-applicable]`
- Objective unblock condition: `[required evidence|not-applicable]`
- Artifacts/criteria to revisit after unblock: `[objective list|not-applicable]`
