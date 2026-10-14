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

The skills use a portable format and can be installed for multiple agents.
Understand, Plan and implementation are not tied to a particular model or
operating system. Independent review has a specific requirement: **GPT-6 Astra
(`gpt-6-astra`) at Extra High effort (`xhigh`)**. This applies to initial and
correction reviews, including the review step required by Deliver. Work started
with Claude or another implementation agent needs access to that reviewer to
complete the workflow.

Skill discovery, invocation, tool access and permissions depend on the agent
and harness. Delivery needs repository access and the tools required for the
agreed checks. Review needs the required model and effort in a fresh context
without the implementation conversation. If the current harness cannot provide
that combination, arrange a suitable separate session and pass only the review
brief, fixed diff, relevant sources and verification evidence.

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

Plan tests only for meaningful evidence or regression protection, preferably in
the owning suite. Write and run worthwhile tests before the corresponding
production change by default. For fixes or new behaviour, show where practical
that they expose the defect or missing behaviour, rather than an unrelated setup
failure. Behaviour-preserving changes may pass before and after. Ground expected
results in agreed requirements, contracts or reference calculations, never solely
in current implementation output.

Exploration, later discoveries and incorrect tests can justify timing exceptions.
Explain the timing and independent basis for expectations. Later tests may protect
existing behaviour; write them before any newly required production correction
by default. Exceptions alone do not require approval or expand scope. Never
adjust assertions, fixtures, snapshots or tolerances merely to make tests pass.

After verification, freeze the diff for Review using the model and effort
specified under [Compatibility](#compatibility). For both initial and correction
reviews, use a fresh context without the implementation conversation. For a
spawned reviewer, explicitly set `fork_turns="none"`, `model="gpt-6-astra"` and
`reasoning_effort="xhigh"`. Confirm the actual model, effort and context before
reviewing. If the requirements cannot be met, report the limitation; do not
silently substitute another model or effort, or treat self-review as independent.

Supply the approved requirements, fixed diff, relevant sources and raw
verification evidence. Review uses execution evidence to assess test-first
practice; a final diff cannot establish sequence. It evaluates justified timing
exceptions and changes to test expectations without rejecting useful later tests
solely for their timing. Review assesses behaviour and code quality separately;
both must pass. Quality findings can require correction without a behavioural
failure. The reviewer reports findings without editing; the delivery owner makes
corrections, rechecks affected behaviour and obtains independent review of the
corrected version with the same required settings.

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
