---
name: test-ownership
description: Assign a behavioural invariant to the lowest sufficient test layer and an existing canonical suite before tests are edited, then consolidate weaker duplicates safely. Use during delivery or review when adding, moving, duplicating, or deleting regression coverage across unit, integration, and end-to-end tests. Repository conventions override generic placement rules.
---

# Test Ownership

Give each behavioural invariant one clear primary owner before adding or
consolidating coverage. Compose this policy with the current Ready issue,
`$vertical-delivery`, and `$code-review`; do not create another lifecycle stage.
Do not invoke this policy when the approved expected test delta is zero. Tests
are evidence, not an automatic deliverable for every code change.

## Establish ownership before editing

After the issue's invariant and oracle are explicit, but before changing tests:

1. State the behavioural invariant in implementation-independent terms.
2. Identify the seam whose failure would violate it.
3. Read the repository's test conventions and existing nearby suites.
4. Select the lowest layer that proves the invariant reliably:
   - unit when a focused component or pure rule owns the behaviour;
   - integration when the boundary or collaboration is part of the failure;
   - end-to-end when only user-visible wiring proves the behaviour.
5. Prefer the existing canonical suite for that owner over a new ticket-shaped
   file or parallel fixture hierarchy.
6. Keep the change inside the approved test delta. If proving the invariant
   requires another seam or broader coverage, invalidate the verification budget
   and replan instead of adding tests opportunistically.

Name tests for the behaviour they protect, not an incident or issue number.
Repository architecture and conventions override the generic layer heuristic.
They select where an already-authorized test change belongs; they do not
authorize moving, deleting, consolidating, or adding other coverage for
consistency alone.

## Permit deliberate overlap only

Keep multi-layer coverage only when each test names a distinct failure mode or
contract seam, such as calculation, serialization, and user-visible wiring.
Do not duplicate the same assertion merely to increase apparent coverage.

## Prove regression value

When proportionate, show that new regression coverage fails against the
defective behaviour and passes against the accepted behaviour using red/green,
a controlled revert, fault injection, or an equivalent counterfactual. When
that proof is unsafe or disproportionately expensive, record the alternative
evidence and residual uncertainty in the issue rather than fabricating a red
state.

## Consolidate safely

Consolidate, move, or delete existing coverage only when the Ready issue
explicitly includes it or evidence shows it is the smallest necessary correction
for the approved oracle to be reliable. Otherwise leave existing coverage in
place and record any improvement as a non-blocking follow-up.

Before moving or deleting a suspected duplicate, verify that it does not protect
another implementation, adapter, public contract, configuration, or failure
mode. After consolidation:

- run the owning suite's focused checks;
- run proportionate broader checks for every affected layer; and
- inspect the diff for lost assertions, fixtures, and failure-path coverage.

Prefer one strong canonical test over several weaker duplicates only when the
evidence shows their protected behaviour is genuinely the same.

## Review contract

For changed tests, `$code-review` verifies the stated invariant, owning layer,
canonical suite, regression evidence, distinct purpose of any multi-layer
coverage, and deletion safeguards. Missing ownership evidence is actionable
only when it causes an observable coverage failure for the approved invariant or
makes its declared oracle unreliable. Duplication, brittleness, or consistency
alone is a non-blocking follow-up outside the issue.
