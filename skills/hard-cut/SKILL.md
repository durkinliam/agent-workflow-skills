---
name: hard-cut
description: Enforce one canonical contract by removing obsolete internal shapes and compatibility code. Use only when the user, an approved design, or a Ready issue explicitly declares a hard cut for a schema, API, configuration, route, enum, feature flag, data shape, or architecture change. Compose with delivery and review; do not use as readiness authority or infer it as the default evolution policy.
---

# Hard Cut

Apply an explicitly approved hard cut without preserving speculative
compatibility. Keep the existing lifecycle, issue oracle, and review gates.

## Entry gate

Require the authoritative user decision, approved design, or Ready issue to name:

- `Change/evolution policy: hard-cut`;
- the one canonical target shape; and
- evidence that the affected boundary can change atomically.

Do not infer a hard cut from a request to simplify, rename, refactor, or remove
legacy code. If the policy or target shape is absent, return to the owning design
or issue decision. This skill does not make an issue Ready or expand its scope.

## Inventory the boundary

Before editing, inspect every relevant producer, consumer, fixture, test,
document, configuration path, and deployed or persisted representation. Classify
each old-shape dependency as either replaceable inside the approved change or a
real compatibility boundary.

Stop and replan when evidence reveals any unhandled:

- database or file state that survives the change;
- public API, wire format, queued event, or independently deployed consumer;
- rolling or mixed-version execution;
- rollback dependency; or
- parser, authorization, or security boundary that must reject old input
  deterministically.

Route those cases to an explicit compatible-evolution or migration decision.
Do not hide them behind an alias, fallback, coercion, adapter, or dual-read path.

## Enforce the cut

Within the Ready issue and `$vertical-delivery`:

1. Update all in-scope producers and consumers to the canonical shape.
2. Remove old identifiers, branches, adapters, aliases, fallbacks, coercions,
   fixtures, tests, and documentation that exist only for the old internal shape.
3. Retain negative tests when the current parser, trust, or security contract
   requires deterministic rejection of obsolete input.
4. Search for live references to the old shape, run the focused oracle and
   proportionate broader checks, and inspect the complete diff.

Do not treat simplification as evidence. The boundary inventory and declared
oracle establish whether deletion is safe.

## Review contract

When hard-cut is declared, `$code-review` treats unexplained compatibility code
as an actionable finding. When it is not declared, compatibility remains an
ordinary design decision and this policy supplies no review presumption.
