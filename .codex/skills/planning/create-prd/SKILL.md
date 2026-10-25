---
name: create-prd
description: Create or review a PRD for an initiative or feature, either directly executable or divided into specs, without replacing product and technical definitions.
---

# Create PRD

Use for every initiative or feature intended for implementation.

## Preconditions

- Read the technical foundation; a PRD does not silently decide pending stack or architecture.
- Read the product definition; a PRD does not invent goals, users, value, or business rules. Rule changes require a recorded root-agent product-governance review and updated canonical source.
- Confirm a feature is `ready-for-planning`; return the created PRD path for catalog update.
- Read existing planning and decisions to avoid competing artifacts.

## Organization

```text
docs/planning/<area>/<feature-slug>/
  <feature-slug>-prd.md
  decisions.md
  specs/
```

Use a short stable slug; never create a loose or generic `prd.md`.

Classify the PRD as `executable` or `requires-specs`. An executable PRD contains enough detail to implement and verify one delivery. A `requires-specs` PRD lists independently auditable derived specs. Include a mockup for UI changes or an equivalent flow/contract/diagram for non-UI work.

Every PRD includes a hierarchical `text` file tree with one explicit common root and expanded levels, terminal `create`/`modify`/`delete` actions, and an exactly matching file-impact table. Reject flat lists, compressed paths, and brace expansion.

For `executable`, detail applicable external-integration boundaries and proportional frontend componentization. For `requires-specs`, record only macro constraints; each spec owns details.

Record open decisions without inventing answers. A `blocked` PRD uses the template's structured blocker and may receive planning review but is not executable. Use `assets/prd-template.md`.

Report path, feature slug, derived specs, open decisions, risks, and next step.

## Contract depth

The PRD focuses on what, why, expected outcomes, main flow, scope, behavior, high-level acceptance, risks, and test/verification strategy. `executable` fits one small or medium, closed, clear, end-to-end verifiable delivery. `requires-specs` means multiple independent or sequential vertical deliveries, not merely technical complexity.

Apply the behavior, scenario, UI-state, evidence, and no-production-code guidance in `../create-auditable-spec/SKILL.md` to executable PRDs as well. For `requires-specs`, keep the PRD at macro level and place delivery detail in its specs. Do not duplicate concrete implementation or test files in planning.

Record whether feature Technical Design is needed and why. Simple decisions stay in planning; relevant architectural decisions require `architect` to produce or review an explicit embedded or linked design before dependent planning is ready. The global foundation is not a feature design document.

Apply `../create-spec-driven-plan/references/contract-traceability.md` when creating or editing planning. Put the traceability header before other metadata/content, inspect existing contracts and decisions, preserve historical bodies, and maintain reciprocal effective replacement links and canonical decision references. Never treat `superseded` planning as executable; `active` denotes the current accepted contract, not completed implementation.
