# Agent Workflow Skills

A personal workflow for collaborating with coding agents through a GUI or other
harness. Four complementary skills describe how to reach a shared understanding,
ask questions, plan and implement software changes, using the portable Agent
Skills `SKILL.md` format supported by the [Skills CLI](https://github.com/vercel-labs/skills).

## Install

List the available skills:

```sh
npx skills add durkinliam/agent-workflow-skills --list
```

Install all four skills:

```sh
npx skills add durkinliam/agent-workflow-skills --skill '*'
```

Install one skill:

```sh
npx skills add durkinliam/agent-workflow-skills --skill understanding
```

Installation defaults to the current project. Add `--global` to install across
projects, or use `--agent` to specify the target agents. See the
[CLI options](https://github.com/vercel-labs/skills#options) for details.

For a Linux workstation using both Codex and Claude Code, install all four for
both agents across projects:

```sh
npx skills add durkinliam/agent-workflow-skills \
  --skill '*' --agent codex claude-code --global
```

With the default configuration, the CLI uses `~/.agents/skills` for Codex and
`~/.claude/skills` for Claude Code. Install on the machine where the agents run.
If a provider uses a custom configuration directory, check its skill discovery
paths. See the [supported agents](https://github.com/vercel-labs/skills#supported-agents)
and [T3 Code's Claude configuration](https://github.com/pingdotgg/t3code/blob/main/docs/user/providers-claude.md#skills).

## Compatibility

The skills use a portable format and are not tied to a particular model,
agent or operating system. Skill discovery, invocation, tool access and
permissions depend on the agent and harness.

Implementation work is reviewed by a fresh agent in a clean context, without
the implementation conversation. No particular reviewer model or effort is
required. If the harness cannot provide independent review, report it as
outstanding rather than substituting self-review.

See [Claude Code's support for the Agent Skills standard](https://code.claude.com/docs/en/skills).

In T3 Code, select the environment and provider, then use `$` in the composer
to choose an installed skill. Check that all four appear for both Codex and
Claude when switching providers. After installing or changing skills, use
**Restart agent session** in the command palette. These instructions follow
[T3 Code's documentation](https://github.com/pingdotgg/t3code/blob/main/docs/user/composer.md#commands-and-skills);
they do not establish that a particular workstation or provider version has
been tested with these skills.

## Skills

| Skill | Purpose |
|---|---|
| [understanding](skills/understanding/SKILL.md) | Reach a shared understanding of an idea, plan or task, using a design tree of resolved, deferred and blocking branches. |
| [questioning](skills/questioning/SKILL.md) | Ask the user questions one at a time from a prioritised backlog, using examples and alternatives rather than asking for investigable facts. |
| [planning](skills/planning/SKILL.md) | Turn a shared understanding into a parent plan with independently verifiable child tasks. |
| [implementing](skills/implementing/SKILL.md) | Standards for any code or configuration change: independent test expectations, distinguishing evidence and fresh-context review. |

Each linked `SKILL.md` contains the full activation guidance and instructions.

## Workflow

Understanding establishes the current state from evidence and agrees the future
design with the user. Planning synthesises that understanding without repeating
settled discovery. Implementing applies to every change, however small. Both
understanding and planning use questioning whenever they ask the user anything.

Planning writes `.agent/plans/<plan-name>/PLAN.md` with the problem
statement, scope, acceptance criteria, completion destination and linked tasks.
Each child task lives in `.agent/plans/<plan-name>/tasks/<NN-task-name>.md` and
names the acceptance criteria it serves and the verification statement it must
meet. Split by independently verifiable outcome; a single child task is fine
when splitting creates no useful boundary.

Work isn't done until there is evidence that tells success apart from a
plausible failure. Tests take expected results from agreed requirements,
contracts or reference values, never from current output. A fresh reviewer
receives the requirements, diff and raw verification evidence, and reads the
surrounding source and runs checks itself.

## License

MIT
