# Final Handoff

This is the canonical contract for every coordinated delivery. The root agent consolidates participating agents' evidence; each producer supplies actual results and accessible artifact references for its owned checks.

## Delivery contents

Include the outcome, changed files, planning satisfied (executable PRD/spec or recorded short-flow scope), summarized ledger and participating agents, handoffs, skipped steps and reasons, checks and results, omitted checks and reasons, blockers and next step, risks, remaining decisions, and updated memory.

## Scenario and evidence record

Organize all tests and verifications actually performed by acceptance criterion and scenario. Include applicable Given/When/Then scenarios and interface states. For checks without a feature scenario, identify their verification purpose instead. Use a table such as:

| Criterion / scenario / state | Expected result | Observed result | Status | Execution reference | Evidence |
|---|---|---|---|---|---|
| Criterion ID and scenario, or check purpose | Required behavior | Actual observation | passed / failed / blocked / not-run / not-applicable | Command or manual procedure reference | Artifact links or recorded result |

For each execution reference, record the exact command or reproducible manual steps, executor, relevant environment (including revision or worktree state and applicable browser/viewport), exit status when available, and result summary. Shared executions may be referenced by multiple scenarios without rerunning or duplicating their output. Distinguish implemented tests from executed tests and planned visual evidence from captured evidence.

Include every actual evidence artifact in an organized index or directly in the scenario record: test reports, relevant output/logs, screenshots, recordings, traces, and other produced proof. Link artifacts so the reader can inspect them. If a check produces no separate artifact, retain its actual result in the execution record; a file is not required solely to repeat tool output. Never fabricate evidence, claim an unexecuted check passed, or treat a mockup as proof of runtime behavior.

Preserve failures alongside subsequent corrections and retests, linking each attempt and its result. For blocked, omitted, unavailable, or non-applicable checks and evidence, explain why; blockers also identify the owner and concrete next step. Missing or inaccessible artifacts must be identified as missing evidence, not presented as available proof.

## Images and presentation

Group images by scenario or interface state. Give every image a caption describing what it shows, the associated criterion, and relevant environment or viewport. Display images inline when the delivery surface supports it and they help assess the result; otherwise provide clearly labeled links. Keep all image references available even when only representative images are displayed in the summary.

The final response may be concise and link a comprehensive evidence record rather than dump logs or every image into the conversation. The linked record must cover all executed checks, their scenarios and results, and all produced evidence. Reuse existing handoffs and artifact locations; this contract does not require a new reporting system, storage directory, or standalone report for every task. Documentation-only maintenance does not require screenshots or application tests without a relevant verification purpose.

Never include secrets, credentials, or raw sensitive data in evidence. Use safe fixtures and sanitized artifacts; state any redaction or resulting evidence limitation.

## Completion and paths

Before finishing, the root agent confirms that no agent remains `selected` or `called`, implementation received independent review, required verifiers completed or explicitly blocked, and changes to rules, agents, skills, or structural memory received `skill_guard` review. Terminalize `active-task.md` and incorporate the last handoff before writing the final session. Saved memory, handoffs, and documentation use repository-relative paths, never machine-specific absolute paths. Resolve relative Markdown links from the containing document. In the user-facing response, render local file and media links using the absolute paths required by the host, without persisting those machine-specific paths in repository documents.
