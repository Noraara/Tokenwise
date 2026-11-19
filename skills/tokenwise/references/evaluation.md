# Evaluate Tokenwise

## Check routing and quality

Run these cases against disposable or redacted project data. Use fresh sessions and inspect the tool trace alongside the result.

| Case | Expected behavior |
| --- | --- |
| Routine lookup with one known symbol | Exact search or direct read, then a source-backed answer. No graph query is needed. |
| Small fix that affects one caller | Targeted reads, a working change and the relevant check. |
| Several related modules and a current graph | A bounded graph query leads to source verification of decisive relationships. |
| Missing, outdated or incomplete graph | Direct source tracing, with no index creation for the read-only task. |
| Verbose test run with several distinct failures | Original exit status, totals and each distinct failure are accounted for. |
| No companion skills available | Project files, search and ordinary shell tools are sufficient. |

Try both ordinary prompts and explicit invocation. Skill discovery, implicit selection and successful execution are separate outcomes. Include a context-free question when testing implicit selection so you can see whether the skill stays out of unrelated work.

## Measure savings when requested

- Prepare the same tasks, source snapshot, tools, model, reasoning settings and acceptance criteria for both variants. Decide whether both variants can use a prebuilt graph. Keep that condition fixed or disclose it as a separate comparison.
- Start fresh for each run. Record completed and failed runs, retries and tool calls. Sum reported input and output tokens across attempts. Report cached input separately as a subset of input when the host exposes it. Keep separately billed or metered preprocessing visible as well.
- Grade the completed work against the same acceptance criteria. Report quality differences and any missing measurements alongside counts. Failed or incomplete runs stay in the results.
- If Tokenwise's route uses a unique index, show the one-time build and expected refresh cost alongside the per-task figure. For multiple runs, state how many runs share the index. If the host exposes no usage counters, report observations without a token-saving percentage.
