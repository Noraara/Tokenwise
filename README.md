# Tokenwise Skill

**Save input tokens on everyday coding tasks.** Tokenwise helps Codex and Claude Code read fewer irrelevant files, skip repetitive log output, and keep the evidence they need to finish the job. Use it for quick fixes, dependency tracing, and debugging sessions.

## Quick start

Use [GitHub CLI](https://cli.github.com/) with support for [`gh skill install`](https://cli.github.com/manual/gh_skill_install).

```sh
# Codex
gh skill install Noraara/Tokenwise tokenwise --agent codex --scope user

# Claude Code
gh skill install Noraara/Tokenwise tokenwise --agent claude-code --scope user
```

To install in one project, run from that project's Git checkout with `--scope project`. For manual setup, copy the entire [`skills/tokenwise`](skills/tokenwise) folder into one of these directories. The destination should end in `tokenwise/SKILL.md`.

| Agent | One project | All projects |
| --- | --- | --- |
| Codex | `.agents/skills/` | `~/.agents/skills/` |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |

## Try it on a real task

Try this in a fresh Codex session.

> Use $tokenwise to find where the retry limit is set and which test covers it.

In Claude Code, start the same request with `/tokenwise`. Expect the setting and the relevant test, backed by file references. The host can also select the skill automatically when it fits the task.

## Where it saves context

| Task | What Tokenwise brings into context |
| --- | --- |
| Find a known symbol or fix a familiar error | The exact match and the relevant callers or checks. |
| Trace a dependency across modules | A focused query against a current, relevant graph when available, followed by the source files that verify the relationship. |
| Recover a past project decision | The owning note and decisive evidence, starting from the project index or handoff. |
| Diagnose a long test run | The exit status, totals, each distinct failure, and the lines needed to investigate. |

Tokenwise is a standalone [Agent Skill](https://agentskills.io/specification). [Graphify](https://github.com/Graphify-Labs/graphify) is optional. If the graph is missing, stale, or incomplete, Tokenwise can trace relationships directly in source. It follows explicit requests to use Graphify and project graph-first instructions. See the [graph retrieval guide](skills/tokenwise/references/graph-retrieval.md).

## What an everyday run looks like

Say a test reports a retry limit of three when you expected five. Tokenwise starts at the exact failure or setting name, opens its definition and reads the relevant caller and test. For a lookup, the answer can end with the value and its source. For a fix, the same route ends with the smallest change and the focused regression check.

A dependency trace starts differently. If a current graph covers the modules, use a small query to find candidate edges. Open the actual definitions and call sites before stating what calls what. For a large test log, retain the exit status, totals, and each distinct failure. Expand the excerpt if an error lacks the context needed to diagnose it.

## What you get back

Expect an answer backed by the relevant source, or an edit with the same verification your project normally requires. Tokenwise can work alongside the skill that owns the task. It applies the project’s existing search and graph rules and starts from the smallest useful read. With ordinary file tools alone, it can still trace imports, find decisions, and filter command output.

## How I use it

Start with Tokenwise on its own. Ordinary project search and source reads are enough for routine lookups and fixes. In my own setup, [Ponytail Full](https://github.com/DietrichGebert/ponytail#install) guides implementation choices while Tokenwise controls what enters context. I use [Graphify](https://github.com/Graphify-Labs/graphify#install) selectively for relationships across files and [Atlas Notes](https://github.com/Noraara/Atlas-Notes) for past decisions. Each companion is optional.

## Measure the result

Savings depend on the task and how much irrelevant context the agent would otherwise read. Tokenwise has no published benchmark yet. The [evaluation guide](skills/tokenwise/references/evaluation.md) shows how to compare equivalent runs, count retries and graph costs, and check that the result still meets the same requirements.

## Help and contributing

For a bug report, include your agent and version, a small redacted example, the behavior you expected, and what the agent did. For a behavior change, include the relevant verification case and result. [GitHub Issues](https://github.com/Noraara/Tokenwise/issues)

## License

Released under the [MIT license](LICENSE).

## Credit

Made by [Noraara](https://github.com/Noraara).
