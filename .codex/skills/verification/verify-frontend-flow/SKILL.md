---
name: verify-frontend-flow
description: Verify frontend behavior through technical checks and real operation using a browser MCP or agent-browser automation backend.
---

# Verify Frontend Flow

## Preconditions

When selected, a real browser automation backend is mandatory. Accepted backends are an environment-provided browser MCP, including Playwright MCP, or the `agent-browser` CLI using `.codex/skills/verification/agent-browser/SKILL.md`.

The `frontend_verifier` agent exposes Playwright MCP in its TOML. Availability is not selection: the technical foundation chooses the backend, including `agent-browser` when specified, even if another backend starts successfully.

Use the backend recorded in `docs/project/technical-foundation.md`. If the foundation does not confirm an operational backend, return `blocked` through root with `architect` as resolution owner instead of choosing silently. Static checks are not a fallback, and the verifier must not silently install global tools. Read `references/browser-tooling.md` for preflight, installation, and diagnostics.

## Procedure

1. Run the browser-backend preflight.
2. Discover and run applicable build, lint, typecheck, and tests while respecting ownership of shared checks.
3. Start the application reproducibly.
4. Open it through the selected backend and inspect console and network.
5. Navigate, click, fill, and submit acceptance flows.
6. Verify initial, loading, success, empty, error, validation, permission denied, disabled, retry, and responsive states when relevant.
7. Verify basic accessibility, named-viewport responsiveness, and visual smoke behavior.
8. Apply frontend-componentization and external-boundary checks when planning makes them relevant.
9. Capture screenshots of relevant visual results for each test, including final and necessary intermediate states.
10. Save each set under `tmp/<feature-slug>/<deliverable>/<test-name>/` with ordered descriptive names such as `01-initial-state.png` and `02-result.png`.
11. Collect other reproducible evidence and assign failures to frontend or backend only when the cause is proven.

## Visual evidence

- Normalize path segments to kebab-case without spaces or sensitive data.
- `deliverable` identifies the executable PRD or verified spec; use its canonical identifier when available.
- Capture the application, not the entire desktop, unless an acceptance criterion requires external context.
- Never capture tokens, credentials, personal data, or other secrets.
- Record each exact evidence path and the criterion it proves in the handoff.
- Treat a missing screenshot as an omission and justify it; capture failure does not silently waive the requirement.

Do not modify the product. Deliver the backend used, commands, URL/environment, viewports, steps, results, console/network findings, screenshot paths, evidence, failures, and omissions.

Planning defines what must be visually proven in `Visual evidence expectations`, including relevant states and viewports. The root selects this verifier; the verifier chooses how to prove expectations with the real application and may capture additional evidence. Map each expectation and acceptance criterion to a result and evidence path or an explicit omission/blocker; mockups express intent and never replace real operation.
