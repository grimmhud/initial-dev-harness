# PRD and spec contract traceability

## Visible header

Place Status, Supersedes, Superseded by, and Related decisions directly after the title, before classification, other metadata, or main content. Use Markdown lists and relative clickable links; use `none` when no relationship is known. These are Markdown fields, not YAML front matter. Never invent predecessor files or decision records to fill a field.

## Status semantics

- `draft`: incomplete or unreviewed planning.
- `blocked`: a required decision or dependency prevents readiness; include the structured blocker.
- `ready`: planning is sufficiently defined and reviewed for implementation, subject to applicable gates and authorization.
- `active`: the accepted contract explicitly designated as current for its scope. This does not prove implementation, deployment, or verification is complete and does not bypass readiness gates.
- `superseded`: historical contract replaced by the linked successor(s); never an executable current contract.

Use these values consistently in PRDs and specs. Track implementation completion separately in implementation evidence/handoffs, not with document Status `completed`. When encountering legacy statuses, establish their meaning from evidence rather than automatically promoting them to `active`.

## Replacement workflow

1. Inspect existing PRDs/specs for the behavior and read related canonical decisions before creating another contract. Check predecessors, successors, parent PRD, and spec index for competing or stale references.
2. The root agent evaluates business-rule changes using `define-and-govern-product` and updates the canonical source first; architect evaluates technical changes. Preserve material-change confirmation and other gates. The responsible owner records the accepted rationale, alternatives, and consequences in `docs/decisions/product/` or `docs/decisions/project/` before dependent contract replacement.
3. Planner creates a new contract at a distinct stable path, linking predecessor(s) in `Supersedes` and canonical decisions in `Related decisions`. Do not create unrelated competing plans. A draft replacement is not executable and must not be labeled `active`.
4. Once the replacement is accepted as current, update predecessor Status to `superseded` and its `Superseded by` links in the same change that designates the successor `active`. Both sides link the canonical decision(s). If the old behavior is already invalidated while its replacement is still blocked/draft, mark the old contract `superseded` with the real successor link (creating a clearly blocked successor if needed) and record that no executable replacement exists; block dependent implementation rather than implying the draft is current.
5. Preserve the old body and historical semantics. Change its traceability metadata, not its historical rules or acceptance criteria. Do not delete or overwrite the prior contract. A metadata correction or typo alone does not require a new contract.
6. Update affected parent PRD/spec-index/catalog navigation through its owner to point to current contracts and identify historical ones. Preserve history links; do not rewrite the old document's body for navigation. An unchanged parent need not be superseded solely because its spec links change.
7. Verify relative links resolve, effective predecessor/successor relationships are reciprocal, no self-links/cycles exist, and the same canonical change decision is discoverable from both sides. Multiple predecessors/successors are allowed for merges/splits; explicitly cover the replaced scope. Do not mark an entire contract superseded for a partial replacement unless successors carry forward all still-valid scope.

Full rationale lives only in `docs/decisions/`; planning headers and indexes provide navigation, not a second decision log. Git records technical history and diffs but does not replace semantic links. When editing existing planning, add the header using verified decisions and relationships; preserve known readiness/status and historical content unless a real replacement is authorized.

A draft successor may declare its intended predecessor in Supersedes. Until the decision accepts or invalidates the prior contract, do not change the predecessor to superseded or populate Superseded by as if replacement were effective. Review proposed links as pending; require reciprocal links when replacement takes effect. Only one accepted contract may govern the same scope; a ready candidate does not silently override an active one. If the parent PRD is superseded, reconcile its child specs and dependencies before using them, even if their own status still reads ready.

Planning readiness means dependencies and their contracts are understood; it does not claim predecessor implementation has finished. Root separately checks required implementation/verification dependencies before starting a sequential slice.
