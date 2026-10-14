---
name: plan
description: Plan a bounded software change and meaningful verification before implementation. Split issues when context requires it; no production editing.
---

# Plan

Turn established intent and evidence into an approvable plan. Resolve unclear
intent through Understand.

## Define the change and verification

State:

- Observable outcome and acceptance criteria.
- Smallest useful approach, affected modules, constraints and non-goals.
- Material decisions, evidence and unknowns.
- Verification, required access or operations, and completion destination.

Explain consequential alternatives with a concrete example and supported
recommendation. Ask the question that unlocks later decisions first. Defer later
decisions with a resolution trigger. For implementation-dependent unknowns, agree
a bounded experiment, distinguishing observation and resulting decision.

For each claim, identify evidence that distinguishes success from plausible
failure: environment, real inputs, interfaces and checks. State what tests, mocks
and CI leave unverified and how to observe the agreed outcome. A simulated
contract does not prove the real integration.

Plan tests only for meaningful evidence or regression protection. Prefer the
owning suite; avoid duplicate coverage without a distinct purpose. Ground expected
results in agreed behaviour. Plan worthwhile tests before production changes by
default; explain known exceptions and allow justified discoveries during delivery.

Investigate unknown verification or agree an experiment. Missing essential
evidence prevents completion. Preserve explicitly offline or limited outcomes.

## Size the work

Keep one plan when requirements, code, checks and likely debugging fit comfortably
in one context. Otherwise split by independently verifiable behaviour, ordering
dependencies and leaving room for corrections. Risk alone does not require issues;
do not invent token thresholds or precise usage forecasts.

Each issue carries its outcome, relevant constraints, source links and checks
without duplicating the plan or replaying the conversation. Avoid splits by
technical layer. Reassess if new evidence substantially increases context needs.
Use the [record format](references/records.md) for useful durable coordination;
small plans may stay in chat.

## Establish authority once

Before production edits, obtain approval for behaviour, boundaries, verification
and destination unless existing instructions cover them. Honour explicit file,
test, spending, operation and issue-revision limits. Otherwise allow supporting
changes within agreed modules; do not impose arbitrary file or test counts.

Readiness is not permission. Issues inherit only applicable parent authority.
New behaviour, changed contracts, wider access or a changed completion standard
requires a user decision; findings cannot authorize expansion.

Continue authorized implementation with Deliver. For planning-only requests,
return the reviewable plan. State the next action and remaining user decision
without making the user route skills.
