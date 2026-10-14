# Agent Workflow Skills

A personal workflow for collaborating with coding agents through a GUI or other
harness. Four complementary skills describe how to understand, plan, deliver and
review software changes, using the portable Agent Skills `SKILL.md` format
supported by the [Skills CLI](https://github.com/vercel-labs/skills).

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
npx skills add durkinliam/agent-workflow-skills --skill understand
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

The workflow instructions do not require a particular model, provider or
operating system. Skill discovery, invocation, tool access and permissions
depend on the agent and harness. Delivery needs repository access and the tools
required for the agreed checks; independent review needs a fresh context without
the implementation conversation. If the harness cannot provide that context,
use a separate session and pass only the review brief, fixed diff, relevant
sources and verification evidence.

Each skill's `agents/openai.yaml` supplies optional OpenAI UI metadata: a display
name, short description and default prompt. The workflow instructions live in
`SKILL.md`. See [OpenAI's metadata documentation](https://learn.chatgpt.com/docs/build-skills#optional-metadata)
and [Claude Code's support for the Agent Skills standard](https://code.claude.com/docs/en/skills).

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
| [understand](skills/understand/SKILL.md) | Clarify intent, investigate evidence and resolve the next important uncertainty. |
| [plan](skills/plan/SKILL.md) | Agree a bounded change, meaningful verification and a completion destination. |
| [deliver](skills/deliver/SKILL.md) | Implement authorized work, verify its outcome and obtain independent review. |
| [review](skills/review/SKILL.md) | Assess a fixed diff for approved behaviour and code quality in a fresh context. |

Each linked `SKILL.md` contains the full activation guidance and instructions.

## Workflow

Enter at the stage the available evidence supports and skip work already
established. An unclear symptom starts with Understand; a known outcome needing
an approach starts with Plan; approved work can start or resume with Deliver.
A fixed diff can go directly to Review. Read-only and planning-only requests
stop at their requested destination.

Use the prompt, repository instructions, code and documents to establish intent.
Ask focused questions only where evidence cannot settle it, starting with the
decision that unlocks dependent answers. Investigate technical unknowns or defer
them explicitly until the step that needs the answer.

## Approval and scope

Agree the observable outcome, boundaries, verification and completion destination
before production edits, unless existing instructions already cover them.
Readiness is distinct from permission. Preserve explicit user limits and
unrelated changes; routine implementation choices within the agreement do not
need new approval.

New behaviour, changed contracts, wider access or a changed completion standard
needs a new decision. Report adjacent ideas without adding them to scope.
Continue authorized work through its destination, stopping for a real authority,
evidence, access or decision gap, or an invalidated boundary. Publication, merge
and rollout need authority covering those actions.

## Verification and review

Plan verification around observations that distinguish the intended result from
plausible failure. Use real inputs and interfaces where the claim depends on
them. Tests are useful evidence, not an automatic deliverable; mocks and green CI
establish only what they exercise. Report missing evidence and skipped checks,
and never weaken checks to claim success.

After verification, freeze the diff for Review in a fresh context without the
implementation conversation. Supply the approved requirements, fixed diff,
relevant sources and raw verification evidence. Review assesses behaviour and
code quality separately; both must pass. Quality findings can require correction
without a behavioural failure. The reviewer reports findings without editing;
the delivery owner makes corrections, rechecks affected behaviour and obtains
independent review of the corrected version.

## Working records

A small plan can stay in chat. Split implementation into independently
verifiable issues when its expected working context needs more room for code,
verification and debugging. Complexity alone does not require separate issues,
and there is no fixed token threshold.

Use existing repository conventions for durable coordination. Otherwise, keep
useful records in ignored `.agent/plans/<name>/PLAN.md`, following the
[working record format](skills/plan/references/records.md). Keep decisions, source
links, evidence and next actions concise. Do not commit local plans, create extra
trackers or delete previous records without permission.

## License

MIT
