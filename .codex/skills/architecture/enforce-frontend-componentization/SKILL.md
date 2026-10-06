---
name: enforce-frontend-componentization
description: Plan, implement, review, and verify pragmatic frontend componentization that balances reuse, cohesion, testability, and simplicity without micro-componentization.
---

# Enforce Frontend Componentization

1. Extract a component, hook, or module when there is identified reuse, a cohesive visual or behavioral responsibility, isolatable complexity/state/accessibility, or explicit variation supported by props or slots.
2. Before extracting, confirm another consumer exists or the unit has a clear name and contract, and that separation reduces complexity.
3. Keep simple one-off markup local. Avoid trivial wrappers, responsibility-free fragments, and generic APIs based on imagined reuse.
4. Do not create a layer for every file. Reassess extraction when concrete evidence appears.
5. Keep visual components free of external-provider details; pass internal models and callbacks and concentrate remote access at the stack's data boundary.
6. Record the componentization decision in planning and prove reuse, behavior, accessibility, or testability according to risk.

In the handoff, report extracted or local units, concrete rationale, consumers, tests/evidence, and exceptions.
