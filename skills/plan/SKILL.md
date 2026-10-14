---
name: plan
description: Agree a bounded software change and meaningful verification before implementation. Split into issues when context demand warrants it. Use for planning, not production editing.
---

# Plan

Turn established intent and evidence into a plan the user can understand and
approve. Resolve missing intent through Understand; do not fill gaps with guesses.

## Agree the change and its proof

State only what matters for the next implementation:

- the observable outcome and acceptance criteria;
- the smallest useful approach, affected code or modules, constraints and
  non-goals;
- material decisions, their evidence and unresolved points;
- verification, necessary access or operations, and the completion destination.

Explain consequential alternatives with a concrete example and recommendation
when supported. Ask the dependency-unlocking question first. Defer decisions
needed only later with an explicit trigger; do not require a complete future
architecture. For an unknown that implementation must resolve, agree the bounded
experiment, observation and decision it enables before treating it as delivery.

Agree verification during planning, not after the code is written. For each
claim, identify an observation that could distinguish the intended behaviour
from a plausible failure. Establish the necessary environment, real inputs and
interfaces, existing checks, and evidence limits. Specify useful test changes
only when needed to prove an agreed claim. Prefer an existing owning suite;
do not add tests for their own sake or duplicate coverage without a distinct
purpose. A mocked boundary supports the simulated contract, not a claim that
the real integration works. Green CI establishes only what its checks exercise.

If the verification approach is unknown, investigate or agree an experiment.
Missing essential evidence prevents claiming completion. Preserve deliberately
offline or otherwise limited outcomes; do not add unrelated live checks.

## Size work for the implementation context

Use one plan when one context can comfortably hold the relevant requirements,
code, implementation, verification and likely debugging. Complexity or material
risk alone does not require a separate issue.

Create issues when that working context would become crowded. Leave meaningful
headroom for failures and corrections; do not invent a universal token threshold
or promise precise future token usage. Split by independently verifiable
behaviour, with dependencies in order. Each issue carries the approved outcome,
relevant constraints, source links and verification needed to execute without
replaying the planning conversation. Reassess the split if new evidence makes
the expected context substantially larger.

Use the short [record format](references/records.md) when durable coordination
is useful. A small plan may stay in chat. Issues are context boundaries, not a
reason to duplicate the full plan or create technical-layer tickets.

## Establish authority once

Obtain approval of the concrete behaviour, boundaries, verification and destination
before production editing, unless the user's existing instruction already covers
them. Preserve explicit limits on files, tests, spending or operations. Otherwise
allow supporting changes within the agreed modules for the approved behaviour
and code-quality standards; do not demand arbitrary file or test counts.

Readiness means the next implementation has enough evidence and a usable check;
it is distinct from permission. Splitting approved work into issues carries only
the parent authority that actually covers their behaviour and boundaries.
If approval names exact issue revisions, honour that restriction. New behaviour,
changed contracts, wider access or a changed completion standard needs a new
decision. Scope findings cannot authorize themselves.

Continue authorized implementation with Deliver. A planning-only request ends
with the reviewable plan. Make the established outcome, next action and remaining
user decision visible in plain language; do not require the user to route skills.
