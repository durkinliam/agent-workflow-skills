---
name: context-handoff
description: Create a concise, source-linked handoff that lets a fresh agent context, harness, worktree, or collaborator continue work without replaying the conversation. Use at a material phase boundary, before a fresh implementation or review context, when context has become polluted, or when work changes owner or environment. Do not use when the next task can reconstruct state cheaply from one authoritative issue or design artifact.
---

# Context Handoff

Treat project artifacts as durable state and the current conversation as disposable working memory.

## Choose the boundary

Prefer continuing when the work is focused, related, and comfortably understood. Prefer a handoff when:

- the next phase has a different objective or reviewer;
- one substantial vertical issue will start in a fresh context;
- exploration, logs, or failed approaches now dilute the relevant evidence;
- work moves to another person, harness, repository, or worktree;
- compaction would have to reconstruct several authoritative sources.

Do not wait for context exhaustion. Handoff at the nearest coherent boundary.

## Build the handoff

Reference authoritative sources instead of duplicating their content. Include only:

```md
# Handoff: <task>

## Objective and current stage
<observable outcome, current lifecycle stage, status>

## Read order
<AGENTS files, design, issue, decision, and evidence links in order>

## Repository state
<repository, branch/worktree, base and head, material changed files or commits>

## Established decisions
<decision + reason + authoritative source>

## Constraints and non-goals
<only those needed by the next context>

## Execution class and model
<judgment or evidence; explicit model and reasoning effort; authority boundary>

## Evidence
<exact checks and results; concise failure details; skipped checks>

## Open state
<blocking item, Not yet specified items relevant to the next step, risks>

## Next action
<exactly one action and the suggested skill>
```

Exclude exploration history, superseded plans, long successful command output, secrets, and facts discoverable cheaply from the linked sources. State uncertainty rather than smoothing it into a confident summary.

Retain any compact continuation launcher only in the active `PLAN.md` or agent
context. Make it self-contained by naming the authorized destination, repository,
authoritative handoff, and stopping conditions. Do not include it in a handoff
returned to the user or ask the user to copy it into another context.

## Verify portability

Before finishing:

1. Confirm every referenced path, issue, commit, base, and head exists.
2. Confirm the next context can identify the authoritative intent and verification oracle without this conversation.
3. Distinguish established facts from assumptions and implementer claims.
4. Keep the handoff shorter than the sources it indexes.
5. Confirm the execution class matches the work: use `gpt-5.6-sol` at `medium`
   for implementation, review, decisions, or final disposition; use
   `gpt-5.6-luna` at `xhigh` or bounded `max` only for non-writing evidence
   work. Treat a combined review-and-oracle assignment as Sol review work.

When an active plan exists, compact established state into its `PLAN.md`, update
the current issue when issue-local state changed, and record the launcher in the
plan's next-action section. Otherwise return the handoff inline without the
launcher. Do not create a separate handoff file or preserve conversation history.
A material decision belongs once in `PLAN.md`, not in the launcher.

## Completion

Return the compact handoff state to the active plan driver. For a delegated
route, retain the execution class, model, reasoning effort, authority boundary,
and stop condition; never route to Terra. If the route is authorized and
unblocked, the driver starts the intended fresh worker without user intervention.
If one user decision or permission is unavoidable after every independent route
is evaluated, state what is established, explain why the answer is needed, and
ask one precise question. Do not continue downstream work in this context or
print an internal routing block.
