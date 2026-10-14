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

By default, write or update worthwhile tests against the agreed expected
behaviour before the corresponding production change, and run them first.
For a bug fix or new behaviour, establish where practical that the test exposes
the relevant defect or missing behaviour; an unrelated setup failure is not
that evidence. Behaviour-preserving changes may legitimately pass before and
after. Add tests only for meaningful evidence or regression protection, using
the existing owning suite where practical.

Justified exceptions include bounded exploration, a later-discovered edge case,
or correction of an incorrect test. Explain why the test comes later and the
independent basis for its expected result, such as an agreed requirement,
documented contract or reference calculation. A later test may protect behaviour
the code already handles. When a discovery requires a production correction,
write the worthwhile test before that correction by default. Existing scope and
approval boundaries still apply; an exception does not itself require approval.

Do not derive expectations merely from the implementation's output, or change
assertions, fixtures, snapshots or tolerances just to make tests pass. Justify
test edits against the expected behaviour independently of the implementation.

Make the smallest clear implementation of the agreed behaviour. Use plain,
accurate names and clear responsibilities. Question a third occurrence of the
same logic; extract only when sharing improves clarity. Avoid forwarding-only
layers and explanations that compensate for confusing code. Update documentation
affected by the change. Code quality is part of acceptance alongside behaviour.

Run the agreed checks at the boundary they are meant to prove. Inspect actual
results, not merely exit codes or green CI. Use real inputs and interfaces where
the approved claim depends on them. Passing tests alone do not prove that the
code works as expected. Identify what tests, mocks or offline fixtures leave
unverified and gather the evidence needed for the agreed outcome. Do not weaken
a check to make it pass.

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

After verification, freeze the diff and send it to Review using GPT-6 Astra
(`gpt-6-astra`) at Extra High effort (`xhigh`) in a fresh context without the
implementation conversation. For a spawned reviewer, explicitly set
`fork_turns="none"`, `model="gpt-6-astra"` and `reasoning_effort="xhigh"`.
Use these settings for initial and correction reviews. If the required model,
effort or fresh context is unavailable, report the limitation rather than
silently substituting or treating self-review as independent.

Supply the approved outcome, criteria, constraints, repository sources and raw
verification evidence, not a preferred verdict or explanation defending the
implementation. For multiple issues, agree a coherent review boundary that also
checks their combined behaviour.

The reviewer reports findings; implementation fixes them. Recheck affected
behaviour and have an independent reviewer assess corrections against the fixed
reviewed version. Keep unchanged evidence only when it still applies.

Complete when the agreed verification, both review assessments and the authorized
destination are satisfied. Report the actual outcome, checks, skipped work and
remaining limits. Publication, merge and rollout require authority covering those
actions; implementation approval alone does not grant it.
