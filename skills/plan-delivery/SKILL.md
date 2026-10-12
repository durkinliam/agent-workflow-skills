---
name: plan-delivery
description: Carry an explicitly authorized manifest of multiple Ready issue revisions through its agreed destination, including required verification and review. Use to execute or resume approved multi-issue work. Keep each delivery worker on one issue. Do not use for a single issue, planning-only requests, or an unapproved backlog.
---

# Plan Delivery

Own continuation across approved issues. A worker finishing one issue returns
control here; it does not complete the user's destination.

## Establish authority and current state

Read the current parent plan, exact issue revisions, dependencies and linked
evidence. Use the repository's existing local planning convention; otherwise use
ignored `.agent/plans/<plan-slug>/PLAN.md` and `issues/`. Keep coordination there,
not in a second tracker or handoff file.

Record the finite manifest actually authorized by the user: issue IDs and
revisions, destination, required verification/review, allowed operations and
budgets. Approval of a destination alone does not authorize every issue that
could help reach it. Ready is technical status, not permission. New issues,
materially revised criteria or revisions, and extra operations need their own
authority. A broader program envelope must be explicit; never infer one.

On resume, reconcile current files and issue state with recorded diff identities,
review dispositions, verification and operation receipts. Confirm that evidence
still covers the current revision and implementation. Do not repeat a completed
side effect. If its outcome is unknown, use only an authorized readback; do not
retry a write to discover whether it succeeded. Missing evidence is a concrete
gap, not permission to assume completion.

## Drive the covered work

1. Select the next covered Ready revision in the parent's order whose dependencies
   are satisfied. For an already started or verified covered revision, resume its
   remaining authorized steps from current evidence. Preserve completed work.
2. Apply `$vertical-delivery` to exactly that issue. Use a focused worker when
   available and appropriate; otherwise perform that one-issue route in the
   current context. Keep only one repository writer active. Give any worker the
   authoritative issue, owned surface, constraints, oracle and stop conditions.
   State a supported model, explicit reasoning effort no higher than medium, and
   judgment authority in the actual dispatch; apply that cap recursively.
3. Inspect the returned files, diff and verification evidence, not just the
   worker's summary. Update the canonical issue and parent state. A worker's
   terminal reply transfers control back to the driver without a user prompt.
4. Obtain any required `$code-review` in a fresh context that did not implement
   the fixed diff. Consume its evidence and disposition. Fix only authorized
   in-scope findings, then obtain the required fresh review of the changed diff.
   A boundary finding cannot amend the issue. Never describe self-review as
   independent; if the required context is unavailable, report the capability
   blocker and retain the verified work.
5. Continue the next covered revision without asking the user to invoke a skill,
   copy a launcher or approve unchanged work again. Perform integration review
   and operational steps only when required and authorized by the manifest.
   An approval for local verification does not authorize publication or rollout.

Use each repository's own runtime, wrappers, modules and approved verification
commands. Do not import another project's framework, provider, operating system,
credential store or deployment procedure. Available native execution and review
capabilities may vary; the workflow does not require a particular tool or UI.

## Boundaries and completion

Continue ordinary investigation and in-scope failures under the existing budget.
Stop the affected route for missing permission, credentials, external evidence
or required capability; a user-owned decision; or invalidated readiness, scope,
budget or oracle. Report the exact gap and smallest needed decision. Reordering
around a blocker is allowed only within the manifest's dependency and ordering
constraints, never to bypass a gate.

An exhausted approved frontier does not authorize new planning, slicing or
implementation. Return unfinished destination work with its precise authority or
readiness gap. Planning-only requests remain with `$issue-planning`; a single
Ready issue remains with `$vertical-delivery`.

Complete only when all covered work and required destination checks are
satisfied. Persist evidence, remaining gaps and the next action in the canonical
plan and issues. Report the outcome, actual checks, skipped checks and limits
naturally; keep routing fields internal. Do not create a goal, external tracker,
or additional artifact merely to keep execution moving.
