---
name: review
description: Independently assess a fixed software diff for approved behaviour and code quality. Use in a fresh context without implementation history; report findings without editing the change.
---

# Review

Make two separate assessments: whether the change delivers the approved outcome,
and whether its code is clear and maintainable. Both must pass.

## Use an independent context

Use GPT-6 Astra (`gpt-6-astra`) at Extra High effort (`xhigh`) for initial and
correction reviews. Start a fresh session or agent without the implementation
conversation, prior reasoning, an implementer's defence, or an expected verdict.
For a spawned reviewer, explicitly set `fork_turns="none"`,
`model="gpt-6-astra"` and `reasoning_effort="xhigh"`.

Confirm the actual model, effort and context before reviewing. If they do not
meet these requirements, report the limitation so delivery can arrange a suitable
reviewer; do not silently substitute another model or effort. A role change inside
the same conversation is not independence; do not call self-review independent.

Receive only the authoritative brief (approved outcome, acceptance criteria,
constraints and non-goals), a fixed base/head or equivalent captured diff,
relevant repository sources, and raw verification evidence. The brief conveys
requirements, not the earlier reasoning trajectory. Establish the actual current
source and review boundary before judging it.

Do not edit source, documentation or planning records. Run permitted checks when
useful; any generated outputs must stay within their agreed disposable locations.
Report the actual permission/isolation limit rather than claiming enforced
read-only access from an instruction alone. The delivery owner records the report
after review and handles corrections.

## Assess approved behaviour

Inspect the fixed diff, surrounding contracts, repository instructions and tests.
Check each approved outcome, acceptance criterion and constraint. Follow relevant
paths through the affected interfaces and consumers; for a multi-issue change,
check that the pieces work together.

Check that test changes provide meaningful evidence or regression protection,
with expectations grounded independently of the implementation's output. Assess
the test-first default using available execution evidence; a final diff alone
cannot establish sequence. Check the justification for exceptions and for edits
to assertions, fixtures, snapshots or tolerances. Later tests can be worthwhile;
do not reject them solely for their timing or demand tests for their own sake.

Examine what verification actually proves. A successful command, mock, source
match, passing test suite or green CI result can coexist with incorrect
user-visible behaviour. Passing tests alone do not establish the agreed outcome.
Check the necessary environment, inputs and observation. Reproduce a focused
check when permitted and useful. Distinguish an observed defect from missing
evidence, and preserve any deliberately limited completion destination.

## Assess code quality

- Use simple, accurate names that explain purpose in plain language. Avoid
  unnecessary jargon, vague names, clever abbreviations and misleading simplicity.
- An implementation and one copy can be acceptable. Question a third occurrence
  of the same logic: would one shared implementation be clearer? Do not introduce
  an abstraction merely because text looks similar; consider whether the pieces
  represent the same responsibility and should change together.
- Require clear, simple responsibilities within files, classes and functions.
  Judge cohesion and understandable control flow, not arbitrary line counts.
- Question classes or functions whose sole purpose is forwarding to another
  layer. Require a useful responsibility beyond delegation.
- Unclear code is unacceptable. A new engineer should understand it by reading
  the implementation. Comments may explain a non-obvious reason or external
  constraint; they must not compensate for confusing names or structure.
- Check affected documentation, instructions and examples against the final
  behaviour. Missing or misleading updates need correction.

These are independent acceptance criteria. A quality finding does not need an
invented behavioural failure. Identify the concrete confusing or wasteful
structure and the smallest useful correction. Stay focused on changed code and
directly affected documentation; do not turn review into unrelated cleanup.

## Return a decision

Report behaviour and code quality separately as pass, changes required, or
evidence missing. Give actionable findings with a file/location, the violated
criterion, evidence, consequence and smallest correction. Separate optional
preferences from required fixes; do not invent findings to justify the review.

If a necessary correction crosses the approved scope, report the failure and
smallest proposed expansion for the user to decide. The reviewer cannot authorize
it. Include the reviewed diff identity, checks performed and remaining limits.

For a correction review, use a fresh context with the approved brief, previously
reviewed version, concrete findings and new diff. Inspect the correction and its
affected behaviour independently; retain valid unchanged evidence rather than
repeating the entire process automatically. Prior approval does not automatically
cover changed code. Return findings to delivery without implementing them.
