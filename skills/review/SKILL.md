---
name: review
description: Independently review a fixed software diff for approved behaviour and code quality. Requires fresh context; report findings without editing.
---

# Review

Assess behaviour and code quality separately. Both must pass.

## Establish independence and scope

Initial and correction reviews require GPT-6 Astra at Extra High effort in a fresh
context. For a spawned reviewer, explicitly set `fork_turns="none"`,
`model="gpt-6-astra"` and `reasoning_effort="xhigh"`. Confirm actual settings;
report mismatches so delivery can arrange a suitable reviewer. Do not substitute
settings or treat a role change in the implementation conversation as independent.

Receive only the approved outcome, criteria, constraints and non-goals, a fixed
base/head or captured diff, relevant sources and raw verification evidence.
Exclude implementation history, reasoning, defences and expected verdicts.
Confirm the current source and review boundary.

Do not edit source, documentation or plans. Run permitted checks when useful;
keep outputs in agreed disposable locations. State actual isolation limits:
instructions alone do not enforce read-only access. Delivery records the report
and makes corrections.

## Assess behaviour

Check each approved outcome and constraint against the diff, surrounding contracts,
instructions and tests. Trace affected interfaces and consumers, including combined
behaviour across issues.

Check that tests add meaningful evidence or regression protection and ground
expectations independently of implementation output. Use execution evidence to
assess test-first practice; a final diff cannot establish sequence. Evaluate
exceptions and changes to assertions, fixtures, snapshots or tolerances. Do not
demand tests for their own sake or reject useful later tests solely for timing.

Verify what checks actually establish at the necessary environment, inputs and
boundary. Passing commands, tests, mocks, source comparisons and CI can coexist
with incorrect behaviour. Reproduce focused checks when useful and permitted.
Distinguish defects from missing evidence; respect deliberately limited outcomes.

## Assess code quality

- Require plain, accurate names; avoid jargon, vague names and clever abbreviations.
- Question a third copy of logic. Share only when responsibilities belong together
  and would change together; similar text alone does not justify abstraction.
- Require cohesive files, classes and functions with clear control flow, not
  arbitrary line counts. Layers need a useful responsibility beyond forwarding.
- Require code a new engineer can understand. Comments may explain reasons or
  external constraints, not compensate for confusing names or structure.
- Keep affected documentation, instructions and examples accurate.

Quality findings need a concrete confusing or wasteful structure, not an invented
behavioural failure. Stay within changed code and directly affected documentation.

## Report

For behaviour and quality separately, return **pass**, **changes required**, or
**evidence missing**. Each finding needs a location, violated criterion, evidence,
consequence and smallest correction. Separate optional preferences from required
fixes; do not invent findings.

Include the reviewed diff identity, checks and limits. If a fix exceeds scope,
report the failure and smallest expansion for the user to decide.

For correction review, use a fresh context with the brief, reviewed version,
findings and new diff. Independently check corrections and affected behaviour;
retain valid unchanged evidence. Prior approval does not cover changed code
automatically. Return findings to delivery without implementing them.
