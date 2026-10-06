# Operational Memory

Procedural source: `.codex/skills/memory/manage-operational-memory/SKILL.md`.

Use `.codex/memory/active-task.md` for current state, `sessions/` for summaries, `decisions/` only for local drafts or non-canonical checkpoints, `projects/` for stable context, `runbooks/` for procedures, and `errors/` for recurring failures. Durable decisions belong in `docs/decisions/product/` or `docs/decisions/project/` according to ownership.

The root agent maintains this memory during coordination. Record verifiable facts, date, and source. Avoid duplication, dumps, long transcripts, secrets, and personal data. At completion, clear `active-task.md` or explicitly leave the blocker and next step.
