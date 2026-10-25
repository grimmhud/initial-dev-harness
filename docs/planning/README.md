# Planning

Every initiative or feature intended for implementation has a PRD:

```text
docs/planning/<area>/<feature-slug>/
  <feature-slug>-prd.md
  decisions.md
  specs/
    01-<feature-slug>-<deliverable>-spec.md
```

A small PRD may be classified as `executable` and implemented directly. Create `specs/` only when the PRD is `requires-specs` and must be divided into multiple auditable deliverables.

Every PRD and spec includes a mockup when there is a UI, or an equivalent flow/contract/diagram when there is not, plus an expected file tree and high-level impact per file.

The file tree is always a hierarchical `text` block with one explicit common root, expanded directory levels, and `├──`, `└──`, and `│`. A flat list, compressed path, or brace expansion is not a valid tree. Put `create`, `modify`, or `delete` on terminal nodes; terminals and file-impact table rows must match exactly in both directions.

Skills and templates:

- classification, index, and decisions: `.codex/skills/planning/create-spec-driven-plan/`;
- PRD: `.codex/skills/planning/create-prd/`;
- auditable spec: `.codex/skills/planning/create-auditable-spec/`.
