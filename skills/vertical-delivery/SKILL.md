---
name: vertical-delivery
description: Implement and verify exactly one Ready vertical issue in a focused context using the smallest defensible change, immediate evidence, strict scope control, and replanning when material assumptions fail. Use when the issue has one observable outcome, bounded scope, acceptance criteria, and a reliable oracle. Local reversible implementation choices may be made and recorded. Do not use for broad discovery, unresolved issue-local architecture, multiple issues, or open-ended refactoring.
---

# Vertical Delivery

Deliver one observable behaviour and stop.

## Readiness gate

Before editing, confirm:

- one current durable issue file explicitly recorded as **Ready**;
- one coherent outcome;
- direct links to the parent design or plan and relevant decisions;
- linked dependencies are Verified or Done, or the issue records an explicit evidence-backed alternative;
- explicit scope and non-goals;
- observable acceptance criteria;
- a viable verification oracle;
- an approved verification budget naming one seam, the expected test delta, and
  the trigger for broader checks;
- user authorization of this issue or a parent destination whose agreed boundary
  still covers it; and
- a change-to-criterion map covering every expected production, test,
  configuration, and task-branch artifact change area.

Treat requests, backlog entries, and conversational handoffs as candidate input,
not readiness authority. If the durable issue is absent, stale, Draft, or
Blocked, make no production edit. Route unresolved design to
`$solution-design`, issue boundaries or a missing gate to `$issue-planning`, or
one named uncertainty to `$spike`. Do not stop for a reversible local choice
that preserves the issue's contracts, scope, and oracle; choose the smallest
conventional option and record it.

Before the first production edit, persist **Ready → In Progress** in the
explicitly authorized lifecycle-artifact location and update its parent-plan
index. Product-write authority does not authorize those files on the ticket
branch. Work on only that issue.

For a substantial issue, start from the issue and linked authoritative artifacts in a focused fresh context. Use `$context-handoff` only when related state cannot be reconstructed cheaply from those sources.

## Plan the slice

1. Inspect the relevant implementation and tests.
2. Map each intended production, test, configuration, and task-branch artifact
   change area to a named acceptance criterion, explicit approved constraint or
   non-goal, or evidenced correctness/safety necessity. Remove any unmapped area.
3. Identify any design decision marked **Provisional for slice**, the evidence this issue must produce, and the result that would validate or invalidate it.
4. Choose the cheapest reliable verification mode:
   - test-first when behaviour is stable and automatable;
   - spike-then-test when the contract is unknown;
   - implementation-then-test when rapid feedback must establish the shape first;
   - manual or visual verification when automation is not yet proportionate.
5. Treat the approved verification budget as authoritative. A zero test delta is
   valid when an existing oracle is sufficient. When tests will change, state the behavioural invariant and oracle, then use
   `$test-ownership` before editing tests to select the owning layer and
   canonical suite.
6. When the Ready issue declares `Change/evolution policy: hard-cut`, compose
   `$hard-cut` throughout delivery and stop if its boundary inventory exposes a
   migration or compatibility dependency.
7. Prefer existing interfaces, patterns, and infrastructure only to choose
   among in-scope implementations. Consistency never authorizes additional work.

## Implement and verify

1. Implement the smallest end-to-end change that makes the outcome true.
2. Avoid later issues, speculative abstractions, unrelated cleanup, and broad refactoring.
3. Run the focused oracle immediately.
4. Fix failures caused by the slice without broadening its outcome.
5. Exercise the public feedback point when it is distinct from the automated test oracle.
6. Run broader checks only when the approved trigger or observed risk warrants
   them, then inspect the complete diff.
7. Compare observed results with every provisional decision exercised by the slice. Mark it **Validated by evidence**, **Invalidated**, or still **Provisional for slice**, cite the evidence, and record the planning consequence. Keep unrelated later decisions **Not yet specified**.
8. Review critical code and tests for design conformance, readability,
   unnecessary coupling, duplication, and unexpected cross-boundary changes.
   Correct defects inside the approved mapping; record other quality preferences
   as non-blocking follow-ups and do not expand the diff for them.
9. Surface material implementation trade-offs or design deviations for human or peer review when task risk warrants it.
10. Summarize successful checks compactly; retain full output only for failures or evidence that materially affects the next decision.

Do not ask the user about ordinary investigation, reversible implementation
choices, failing checks, or adjacent discoveries. Continue autonomously within
the approved contract. Return to the user only when permission, credentials,
external evidence, or authority are missing; an unapproved material decision or
destructive/operational action is required; or evidence invalidates the agreed
outcome, scope, contract, change budget, or oracle.

When delegated execution reveals material judgment, risk, misclassification,
or a wider blast radius than the Ready issue established, stop that execution
lane and return the concrete evidence to the plan driver for immediate
escalation. Do not force a retry first. Allow one corrected attempt only when
the evidence shows that the parent specification itself was defective and the
correction preserves the Ready outcome, scope, contracts, acceptance criteria,
and oracle; otherwise invalidate readiness and replan.

## Replanning rule

Stop and return the issue to Draft or Blocked when evidence materially changes
its outcome, scope, dependencies, acceptance criteria, or oracle; invalidates an
assumption; crosses an unplanned contract or data seam; removes the oracle; or
requires substantial unrelated work. Persist the invalidated gate and lifecycle
transition. Do not replan for ordinary implementation detail that remains
within the agreed boundary. Report:

1. concrete blocker;
2. evidence;
3. invalid assumption;
4. smallest enabling change or revised issue;
5. recommended next action.

Never expand or amend the Ready issue in this delivery context. If evidence
proves additional behaviour is required, stop and return the acceptance
criterion or approved correctness/safety constraint, observable failure or
concrete executable failure path, and smallest proposed correction to the user
as a separate scope decision. Do not treat unrelated follow-up work as blocking
when the declared behaviour is already correct and safe.

## Task management

Update the standalone canonical issue, its lifecycle history, the parent-plan
index, and the link-only `docs/agent/index.md` only in the explicitly authorized
lifecycle-artifact location, with status, exact verification
results, decisions, design-evidence state changes, design deviations, invalidated
assumptions, and follow-ups. Re-evaluate the next Ready frontier when the slice
validates or invalidates a decision that later work depends on.
Mark **Verified** only when acceptance criteria, the stated oracle, applicable
design-conformance checks, and complete diff inspection pass. Do not mark an
issue Done merely because implementation stopped; Done means the parent plan no
longer requires delivery work for it, normally after its evidence is consumed
by integration review. For material changes, route the fixed diff to
`$code-review` before Done. Keep adjacent improvements as non-blocking follow-up
suggestions; never absorb them into the Ready issue. Mirror
status remotely only when explicitly authorized.

## Completion

Report files changed, behaviour proved, design conformance or deviations, exact checks and results, remaining risks, skipped checks, and design/issue updates. Do not continue improving the surrounding code after the issue is Verified.

## Handoff

Return control after this issue's bounded delivery responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may dispatch review or the next Ready issue in a fresh worker and continue the overarching task; this delivery worker must stop after its one issue.

End with: **Stage result** (`Issue verified`, `Issue blocked`, or `Replan required`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local issue path or inline result); **Evidence**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Preserve issue lifecycle state separately and reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Persist the launcher at the parent plan's `handoffs/next.md` and link it from `docs/agent/index.md` only when lifecycle-artifact writes are explicitly authorized for the current branch; otherwise keep it inline or use the separately authorized planning location. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
