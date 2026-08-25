---
name: feature-discovery
description: Inspect an existing codebase to establish objective, evidence-backed understanding of a large or uncertain feature, including execution paths, contracts, seams, blockers, and risks. Use before solution design when repository facts or feature feasibility are unclear. Do not use for greenfield projects, to choose the solution architecture, or to implement the feature.
---

# Feature Research and Discovery

Compress repository truth into the minimum evidence needed for solution design.

## Workflow

1. Restate the requested destination, observable outcome, constraints, and non-goals. Generate the few questions that could materially change the destination or next safe step. Record proposed implementation details as hypotheses, not facts.
2. Form a neutral query plan: what must be learned about current behaviour, relevant subsystems, contracts, and feasibility before design can begin.
3. Read applicable repository instructions and sources of truth.
4. Trace the directly relevant execution path, tests, data flow, and existing extension points. Prefer running code and current implementation over stale documentation.
5. Expand inspection only when evidence identifies a dependency that can block the feature. Do not audit the repository.
6. Identify important interfaces and seams, including external contracts, persistence, messaging, authorization, and failure behaviour when relevant, without selecting a design.
7. Separate:
   - established repository facts;
   - contradictions with the request or documentation;
   - assumptions;
   - user decisions;
   - evidence gaps requiring `$spike`.
8. Mark later uncertainty **Not yet specified** with the stage or behaviour it may block.
9. Hand the evidence to `$solution-design`; route a feature too large or foggy for one coherent discovery artifact to `$wayfinding`. Do not propose implementation issues or production abstractions.

## Artifact

Create or update `.agent/plans/<feature-name>/PLAN.md`. Record:

- outcome and non-goals;
- neutral research questions;
- current execution path and relevant files;
- existing interfaces, seams, and conventions;
- external contracts and failure semantics;
- facts, contradictions, assumptions, decisions, and blockers;
- deferred unknowns and the future step they may block;
- feasible extension points and constraints without choosing between them;
- risks and current next step.

Keep only current findings, frontier, relevant Not yet specified items, and next
action. Do not create a separate research artifact.

## Scope discipline

- Optimize for the minimum objective evidence needed to make design decisions.
- Discourage implementation opinions during research; do not let the ticket's proposed solution bias the findings.
- Cite existing interfaces and patterns as evidence, not as automatic design choices.
- Do not propose repository-wide refactoring, generic infrastructure, future-proofing, or unrelated cleanup.
- Stop once solution design can proceed or one named blocker has been routed to a spike or user decision.

## Completion

Finish with a concise handoff: research location, evidence established, contradictions, blocking decisions, and whether the next action is `$wayfinding`, `$spike`, or `$solution-design`.

## Handoff

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may continue the overarching task, including in a fresh worker; do not absorb the downstream skill into this discovery context.

End with: **Stage result** (`Discovery ready` or `Discovery blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local path or inline result); **Evidence**; **Not yet specified**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (`PLAN.md`, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Record the active launcher in `PLAN.md`'s next-action section when a plan exists; otherwise keep it inline. Do not create a separate handoff file. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
