---
name: deliver
description: Implement an approved software plan or its context-sized issues, verify the agreed behaviour, and obtain independent review. Use for authorized delivery or resumption, not unresolved design.
---

# Deliver

Complete the authorized destination, keeping implementation, corrections and
immediate verification together while the context remains useful.

## Start from the approved work

Read the current plan or chat contract, relevant repository instructions, code
and existing verification. Confirm the outcome, boundaries, unresolved blockers,
permitted operations and evidence required for completion. Honour any explicit
issue revisions or budgets. Resolve missing intent through Understand or changed
decisions through Plan; do not guess or turn technical readiness into permission.

On resume, establish what actually changed and what was verified. Reuse valid
evidence. Do not repeat an external action whose outcome is unknown; inspect its
result through an authorized readback or report the gap.

## Implement and verify

Make the smallest clear implementation of the agreed behaviour. Use plain,
accurate names and clear responsibilities. Question a third occurrence of the
same logic; extract only when sharing improves clarity. Avoid forwarding-only
layers and explanations that compensate for confusing code. Update documentation
affected by the change. Code quality is part of acceptance alongside behaviour.

Run the agreed checks at the boundary they are meant to prove. Inspect actual
results, not merely exit codes or green CI. Use real inputs and interfaces where
the approved claim depends on them. Identify what mocks or offline fixtures
leave unverified. Do not add tests simply because code changed, or weaken a check
to make it pass. Put needed coverage in the existing owning suite where practical.

Fix in-scope failures and code-quality problems. If implementation reveals that
the approved observation cannot prove the outcome, make the evidence gap explicit
and resolve the verification change through Plan. Do not silently substitute a
weaker check. A newly discovered need cannot enlarge scope: explain the concrete
failure and smallest proposed change when another decision is required.

## Continue without unnecessary handoffs

For a split plan, finish the current issue's implementation and verification,
record concise evidence, then continue the next authorized dependent step.
Use a fresh implementation context when context demand warrants it. Pass source
links, approved requirements, current revision, checks, blockers and next action;
exclude the exploratory transcript. Keep one repository writer active unless
disjoint write surfaces were explicitly agreed.

No new approval is needed for unchanged authorized work. Stop only for a real
authority, evidence, access or decision gap, an invalidated boundary, or exhausted
safe routes. Wait for changed or terminal state rather than repeatedly polling
through model calls. Do not create a goal or extra tracker to continue execution.

## Review and finish

After verification, freeze the diff and send it to Review in a fresh context
without the implementation conversation. Supply the approved outcome, criteria,
constraints, repository sources and raw verification evidence, not a preferred
verdict or explanation defending the implementation. For multiple issues, agree
a coherent review boundary that also checks their combined behaviour.

The reviewer reports findings; implementation fixes them. Recheck affected
behaviour and have an independent reviewer assess corrections against the fixed
reviewed version. Keep unchanged evidence only when it still applies.

Complete when the agreed verification, both review assessments and the authorized
destination are satisfied. Report the actual outcome, checks, skipped work and
remaining limits. Publication, merge and rollout require authority covering those
actions; implementation approval alone does not grant it.
