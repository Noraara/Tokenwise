---
name: tokenwise
description: Use for tasks that search, read, or verify project material, including routine lookups, small fixes, dependency tracing, and long logs. Start with the narrowest source that can answer the question and expand as needed.
license: MIT
---

# Tokenwise

Use the task's active instructions and workflow. Preserve the requested deliverable, relevant edge cases and acceptance checks. Apply the smallest useful retrieval step and widen it when evidence is incomplete or contradictory. On a routine lookup, a single targeted read and direct answer can complete the task. For a small fix, read the affected callers and run its focused check. Add no separate planning or reporting step solely because Tokenwise is active.

Follow explicit requests to use Graphify and any graph-first instructions for the project. Otherwise, use direct search for a known file, symbol or error, and query a current, scoped graph when it can narrow a relationship search across files, modules or notes.

| What you need | First move |
| --- | --- |
| A known file, symbol, setting or error | Open the known location or search for the exact term. Read the matching region and affected callers or checks. Follow an obvious import or link directly. |
| A relationship that spans files, modules or notes | If a current scoped graph covers the question and can avoid substantial exploration, query it before broad reads. Use a small result to choose which original sources to verify. See [graph retrieval](references/graph-retrieval.md) when taking this route. Otherwise use targeted search and follow the links or references in source. |
| An earlier project decision | Start from the current index or handoff. Use Atlas if available. Open the owning note or decision record and verify ambiguous or stale claims in source. |
| A large command result | Use scoped output or capture it locally. Preserve the command exit status, totals, each distinct failure and the lines needed to investigate. Reopen the full capture if the visible output is clipped or omits needed evidence. Respect the task's data-handling rules. |

Do the same domain checks the task would normally require. For an edit, verify the changed behavior through its normal entry point when feasible. Report decisive evidence and any unverified checks at the level of detail the user requested. Reuse verified evidence while it is current, including after an interruption.

Leave index creation and refresh to separate, authorized work. If the user asks to measure savings, use the [evaluation method](references/evaluation.md).
