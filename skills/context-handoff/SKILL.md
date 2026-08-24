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

## Evidence
<exact checks and results; concise failure details; skipped checks>

## Open state
<blocking item, Not yet specified items relevant to the next step, risks>

## Next action
<exactly one action and the suggested skill>

## Continuation prompt
<compact copy-pasteable launcher for the next context>
```

Exclude exploration history, superseded plans, long successful command output, secrets, and facts discoverable cheaply from the linked sources. State uncertainty rather than smoothing it into a confident summary.

Keep the continuation launcher under 1,500 characters. Make it self-contained by
naming the authorized destination, repository, authoritative handoff, and stopping
conditions. Do not copy evidence, route inventories, or acceptance criteria that the
linked handoff already contains.

## Verify portability

Before finishing:

1. Confirm every referenced path, issue, commit, base, and head exists.
2. Confirm the next context can identify the authoritative intent and verification oracle without this conversation.
3. Distinguish established facts from assumptions and implementer claims.
4. Keep the handoff shorter than the sources it indexes.

Use the repository's handoff convention. Otherwise, when lifecycle-artifact
writes are explicitly authorized for the current branch and an active parent plan exists, write the active handoff to
that plan's `handoffs/next.md` and link it from `docs/agent/index.md`. If no
active plan exists, use `.agent/handoffs/<task>.md`. Return the same structure
in chat when writes are not in scope. Delete or supersede the temporary file or
active link after consumption; move any durable decision into the active parent
plan's `decisions/` directory rather than leaving it solely in a handoff.

Product or implementation write authority does not authorize a handoff artifact
on the current branch. Without explicit branch-level lifecycle-artifact
authority, return the handoff inline or use a separately authorized planning
location.

## Completion

Return the handoff artifact to the active plan driver. Do not continue the downstream implementation or review in this worker context; the driver may start the intended fresh worker and continue the same overarching task without user intervention when the route is authorized and unblocked.

Set **Control** to `driver` when **To** is an executable authorized route or an authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. Before assigning `user`, confirm that the plan driver has evaluated every independent destination route and that none remains safely executable.

End with: **Stage result** (`Handoff ready` or `Handoff blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local handoff path or inline result); **Evidence**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` when the destination is complete). Reserve destination `Complete` for a passed terminal audit; never use it merely because this handoff is finished.

Then add **Continuation artifact** (normally the handoff artifact, otherwise `inline` or `none`) and **Next prompt**. Keep `Next action` terse; it is not the prompt. For a skill, `direct`, or `scheduled` route, provide the handoff's compact launcher; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Link authoritative artifacts rather than replaying them, and keep the launcher under 1,500 characters.
