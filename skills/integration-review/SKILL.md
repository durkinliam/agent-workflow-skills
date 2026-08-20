---
name: integration-review
description: Independently review a completed walking skeleton or multiple verified vertical issues as one coherent feature against parent intent, cross-slice contracts, evidence, failure behaviour, and operational requirements. Use when integration risk is material before release or feature completion; skip for a trivial single slice already covered by code review and CI. Run in a fresh read-only context and never implement fixes there.
---

# Integration Review

Check whether individually verified slices form the intended complete behaviour without repeating per-diff code review or reopening broad design work.

## Independence and proportionality

- Start in a fresh context that did not implement the feature. Review actual artifacts and repository state, not the implementer's narrative.
- Confirm material slices have passed `$code-review` or record the missing review evidence.
- Add an independent reviewer or specialist oracle for security, permissions, money, migrations, concurrency, major architecture, or similarly consequential risk when available and proportionate.
- Skip this skill when one small slice has no meaningful cross-slice or operational integration risk.

Observe and report the review context's actual sandbox and permission profile;
requested read-only isolation is not evidence that it was enforced. With
enforced read-only isolation, proceed. With a broader observed policy, proceed
only when hard isolation is not required, explicitly forbid edits, record the
broader policy as residual risk, and have the plan driver capture and verify
exact before-and-after repository and review-artifact state. If isolation is
unobservable or any mutation occurs, reject the result as a read-only review.
The reviewer returns its report without persisting it; the plan driver may
write the durable review artifact only after the review context has ended.

## Review inputs

Read the parent project or feature design or plan, standalone issue artifacts
recorded as **Verified**, relevant decisions, final diff or branch changes, and
verification evidence. Treat each issue file as the authority for its lifecycle
and evidence. Identify missing or non-Verified inputs explicitly rather than
reconstructing requirements from implementation alone.

## Review axes

1. **Intent:** Does the combined feature satisfy the original observable outcome and non-goals?
2. **Continuity:** Do the slices connect end to end without gaps, duplicate ownership, or incompatible assumptions?
3. **Design conformance:** Does the implementation preserve the agreed product, system, and program shape, or explicitly justify deviations?
4. **Contracts:** Are external interfaces, schemas, migrations, events, and compatibility requirements coherent?
5. **Maintainability:** Are ownership, coupling, duplication, control flow, and change locality acceptable for the agreed design?
6. **Failure behaviour:** Are retries, idempotency, partial failure, recovery, and data consistency handled to the agreed level?
7. **Verification:** Does evidence cover the critical path through public behaviour, not merely internal units?
8. **Operations:** Are configuration, secrets, logging, metrics, rollout, rollback, and runbook needs addressed when relevant?
9. **Scope:** Did delivery introduce unrelated refactoring, speculative infrastructure, or deferred behaviour accidentally?

## Findings

Prioritize concrete findings with file, symbol, issue, command, or evidence references. Classify each as:

- **Blocker:** required before the feature can be considered complete;
- **Follow-up:** valuable but outside the agreed completion boundary;
- **Accepted risk:** explicitly understood and tolerable;
- **No finding:** do not invent work to fill a category.

Do not recommend broad cleanup without a demonstrated failure or maintenance risk tied to the feature.

When review-artifact writes are in scope and no repository convention exists,
have the plan driver store the returned result under the active parent plan's
`reviews/integration.md`, link it from the parent design and local issue set,
and update only disposition, frontier, and next action in
`docs/agent/index.md`.

## Verification and disposition

Run proportionate end-to-end checks when authorized and available. Summarize successful checks compactly and retain failure detail. Never modify code in this review context. Return one disposition:

- **Ready:** intent and required evidence are satisfied;
- **Ready with accepted risks:** explicit non-blocking risks remain;
- **Not ready:** one or more concrete blockers remain.

After the review context ends, have the plan driver update the review artifact,
parent-plan index, affected issue lifecycle records, and link-only workflow
index when those writes are in scope. Route invalid or
missing design decisions to `$solution-design`, issue-boundary blockers to
`$issue-planning`, one-question evidence gaps to `$spike`, and a newly Ready fix
to `$vertical-delivery`.

Any subsequent implementation change invalidates **Ready** or **Ready with
accepted risks**. Establish the new integrated review surface and obtain a
fresh independent review before relying on approval again.

## Handoff

Return control after this independent review responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may dispatch a bounded fix or complete the destination and continue the overarching task; this reviewer remains read-only.

End with: **Stage result** (`Review approved`, `Review findings`, or `Review blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local review path or inline result); **Evidence**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. When project writes are already in scope, persist the launcher at the parent plan's `handoffs/next.md`, link it from `docs/agent/index.md`, and supersede any stale launcher; otherwise keep it inline. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
