---
name: deliver
description: Implement or resume approved software work, verify its outcome, and obtain independent review. Use after intent and scope are settled.
---

# Deliver

Complete the authorized destination, keeping implementation, corrections and
verification together while the context remains useful.

## Confirm the contract

Read the current plan or chat agreement, instructions, code and checks. Confirm
outcome, boundaries, blockers, permitted operations and completion evidence;
honour explicit revisions and budgets. Resolve unclear intent through Understand
and changed decisions through Plan. Readiness does not grant permission.

On resume, check what changed and was verified; reuse valid evidence. Do not repeat
an external action whose outcome is unknown; inspect an authorized readback or
report the gap.

## Implement and verify

Write and run worthwhile tests before the corresponding production change by
default. For fixes or new behaviour, show where practical that they expose the
defect or missing behaviour, not an unrelated setup failure. Behaviour-preserving
changes may pass before and after. Prefer the owning suite; add tests only for
meaningful evidence or regression protection.

Exploration, later discoveries and incorrect tests can justify exceptions. Explain
the timing and independent basis for expectations: an agreed requirement, contract
or reference calculation. Later tests may protect existing behaviour; write them
before any newly required production correction by default. Exceptions alone do
not require approval or expand scope. Never derive expectations solely from current
output or adjust assertions, fixtures, snapshots or tolerances just to pass.

Implement the smallest clear change. Use plain, accurate names and cohesive
responsibilities. Question a third copy of logic; share only when clearer. Avoid
forwarding-only layers and comments that compensate for confusing code. Update
affected documentation. Behaviour and code quality both count toward acceptance.

Run agreed checks at the relevant boundary and inspect actual results. Use real
inputs and interfaces where the claim requires them. State what tests, mocks,
offline fixtures and CI leave unverified; obtain the required evidence.

Fix in-scope failures. If the agreed check cannot prove the outcome, explain the
gap and resolve verification through Plan; never weaken checks. For necessary
scope changes, report the failure and smallest proposed expansion for a decision.

## Continue

Finish and record each issue's implementation and verification before its next
authorized dependent step. When context requires a fresh worker, pass source links,
requirements, revision, checks, blockers and next action, not the exploratory
transcript. Keep one repository writer unless disjoint surfaces were agreed.

Continue unchanged authorized work without renewed approval. Stop only for missing
authority, access, essential evidence or decisions, invalidated boundaries, or
exhausted safe routes. Wait for changed or terminal state instead of repeated
polling. Do not create a goal or extra tracker just to continue.

## Review and finish

Freeze the verified diff and send it to Review in a fresh context. For initial and
correction reviewers, explicitly set `fork_turns="none"`, `model="gpt-6-astra"`
and `reasoning_effort="xhigh"` (GPT-6 Astra, Extra High). If unavailable, report the
limitation; do not substitute settings or call self-review independent.

Supply the approved brief, constraints, fixed diff, sources and raw evidence,
without implementation reasoning or a preferred verdict. For multiple issues,
review a coherent boundary including combined behaviour.

Fix findings, recheck affected behaviour and obtain independent correction review
against the reviewed version. Retain unchanged evidence only while valid.

Complete when verification, both review assessments and the authorized destination
are satisfied. Report outcomes, checks, skipped work and limits. Publication,
merge and rollout require authority beyond implementation alone.
