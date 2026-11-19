# Tokenwise

Tokenwise is an [Agent Skill](https://agentskills.io/specification) that helps coding agents spend less context finding their way around a project. It starts with the smallest source that can answer the question, then reads more when the task needs it. It keeps the requested deliverable and verification steps intact.

## Quick start

### Install with GitHub CLI

Use a version of [GitHub CLI](https://cli.github.com/) that supports `gh skill install`. Run the command for your agent.

**Codex**

```sh
gh skill install Noraara/tokenwise tokenwise --agent codex --scope user
```

**Claude Code**

```sh
gh skill install Noraara/tokenwise tokenwise --agent claude-code --scope user
```

Use `--scope user` to make Tokenwise available across projects. To install it in just one project, run the command from that project's Git repository with `--scope project`. GitHub CLI selects the latest tagged release when available and falls back to the default branch. [GitHub CLI skill installation](https://cli.github.com/manual/gh_skill_install)

### Install manually

Download or clone this repository and copy the **entire** [`skills/tokenwise`](skills/tokenwise) folder to your agent's skills directory.

| Agent | One project | All projects |
| --- | --- | --- |
| Codex | `.agents/skills/` | `~/.agents/skills/` |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |

Paths starting with `~/` are relative to your user home. For example, in a Codex project the copied file should be at `.agents/skills/tokenwise/SKILL.md`. [Codex skills locations](https://developers.openai.com/api/reference/cli) · [Claude Code skills](https://code.claude.com/docs/en/skills)

### Try it

Open a fresh session in a project and try the prompt for your agent.

**Codex**

> Use $tokenwise to find where the retry limit is configured and which test covers it.

**Claude Code**

```text
/tokenwise Find where the retry limit is configured and which test covers it.
```

For that first run, expect a direct lookup or exact search, a read of the relevant code and test, and an answer that points to both. The agent can also select Tokenwise for relevant tasks on its own. Explicit invocation is useful when checking your setup.

## How it works

| If you ask the agent to… | Tokenwise starts with… |
| --- | --- |
| Find a known setting, symbol or error | A direct read or exact search, followed by the relevant caller or check. |
| Trace a dependency across several modules | A focused query against a current graph that covers the question, if one exists. Then it verifies decisive links in source. |
| Explain an earlier project decision | The project's index or handoff, then the original decision record. |
| Diagnose a large test or build log | The exit status, totals, each distinct failure and enough surrounding lines to investigate. |

An existing graph can point to a few relevant files. The agent still receives text, and the savings come from the material it can skip safely. If the graph is missing, stale or incomplete, Tokenwise falls back to tracing in source. Graph creation and updates can be handled separately. See [graph retrieval](skills/tokenwise/references/graph-retrieval.md) for an example with [Graphify](https://github.com/Graphify-Labs/graphify).

Tokenwise consists of [skill instructions](skills/tokenwise/SKILL.md), short references and [Codex UI metadata](skills/tokenwise/agents/openai.yaml). Graphify and project knowledge tools such as Atlas are optional. Tokenwise ships without an executable, service, hooks or telemetry.

## Verify and measure

Use the [verification cases](skills/tokenwise/references/evaluation.md) to check routine lookups, small fixes, graph routing and large logs. To test token savings, compare equivalent runs and account for retries and any index build or refresh cost. Results depend on the task, host and available index.

## Contributing

For an issue or pull request, include the agent and version, a minimal example with synthetic or redacted data, the behavior you expected, and what you observed. For a behavior change, include the relevant verification case and result. Keep instructions used on every invocation short and put optional detail in references.

## License

Code and documentation are available under the [MIT license](LICENSE).
