---
name: project-discovery
description: Turn a greenfield project idea with little or no code into a bounded destination, evidence plan, explicit assumptions, prioritized unknowns, and first observable-outcome proposal. Use when starting a new project, validating an early product or technical idea, or deciding what must be learned before design can proceed. Use wayfinding instead when the destination is too foggy or large to hold in one discovery session. Do not use for a large feature in an established codebase or to implement production code.
---

# Project Discovery

Convert an idea into the minimum evidence needed to start safely. Treat unknowns as work, not as prerequisites the user must answer.

## Workflow

1. Capture the intended user, problem, destination, observable outcome, known constraints, and explicit non-goals. Accept incomplete input and generate the few questions that could materially change the destination or next safe step.
2. Separate unknowns into:
   - discoverable through research;
   - answerable only by a bounded experiment;
   - product or irreversible decisions requiring the user;
   - reversible choices that can use a recorded default.
3. Rank only the unknowns that threaten the next safe, expensive, or irreversible decision. Mark later uncertainty **Not yet specified**; do not design the whole product.
4. Propose the cheapest evidence-producing next step for each blocking unknown. Route one-question experiments to `$spike`.
5. Propose the smallest observable destination or candidate walking skeleton once the critical uncertainty is low enough, without choosing detailed system or program design.
6. Record candidate observable behaviours, then hand the intent, evidence, decisions, and remaining assumptions to `$solution-design`.

## Artifact

Prefer the repository's existing planning convention. Otherwise maintain
`docs/plans/<project-name>/README.md` when project writes are in scope and link
the active plan from `docs/agent/index.md`. Include only:

- intent and non-goals;
- destination and success signal;
- known constraints;
- assumptions with confidence;
- deferred unknowns marked Not yet specified and the step they may block;
- blocking unknowns and proposed experiments;
- evidence and decisions;
- walking-skeleton proposal;
- candidate vertical behaviours;
- current next step.

Keep the index concise: link the project artifact and record only current stage, frontier, Not yet specified items, and next action. If the user asks only for discussion or repository writes are not in scope, return the same structure in chat instead of writing a file.

## Scope discipline

- Optimize for the minimum viable understanding required for the next decision.
- Research at most the highest-risk few unknowns at once.
- Avoid framework selection, complete architecture, repository scaffolding, or speculative infrastructure unless evidence makes it the next necessary decision.
- Ask only questions that cannot be answered through available evidence and would materially change the outcome.
- Mark useful but non-blocking ideas as deferred; do not expand discovery to resolve them.
- Route work to `$wayfinding` when its destination and decision frontier cannot be represented coherently in one discovery artifact.

## Completion

Stop when the project has one explicit next step: `$wayfinding` for multi-session fog, a bounded spike, a candidate walking-skeleton input to `$solution-design`, or a user decision. Report what remains unknown and why it does not block that step.

## Handoff

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may continue the overarching task, including in a fresh worker; do not absorb the downstream skill into this discovery context.

End with: **Stage result** (`Discovery ready` or `Discovery blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local path or inline result); **Evidence**; **Not yet specified**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. When project writes are already in scope, persist the launcher at the parent plan's `handoffs/next.md`, link it from `docs/agent/index.md`, and supersede any stale launcher; otherwise keep it inline. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
