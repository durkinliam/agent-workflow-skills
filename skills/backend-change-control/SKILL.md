---
name: backend-change-control
description: Bind only the backend seams touched by an approved change to their existing and approved contracts and verification oracle. Use during design, issue planning, delivery, or review when work touches an API, persistence, transactions, background jobs, queues, authorization, clocks, concurrency, or external side effects. This skill classifies scope; it must not invent retries, migrations, compatibility, observability, recovery, or other requirements.
---

# Backend Change Control

Prevent an approved backend change from silently acquiring new semantics while
preserving autonomy over observationally equivalent implementation details.
Compose this policy with the current lifecycle skill; it does not create a new
stage or authorize production edits.

## Inventory only touched seams

Inspect the approved outcome and relevant execution path. Record only applicable
seams; omit the rest:

- request, command, event, or job input contract;
- response, emitted event, or other externally observable result;
- persisted state, schema, transaction, and consistency boundary;
- duplicate delivery, retry, scheduling, clock, ordering, and concurrency
  behaviour;
- authentication, authorization, tenant, and secret boundary;
- external service, filesystem, message broker, or other side effect;
- failure, timeout, cancellation, acknowledgement, and partial-success behaviour.

For each touched seam, state:

| Touched seam | Existing contract and evidence | Approved change | Oracle |
| --- | --- | --- | --- |
| <seam> | <current observable behaviour and source> | <exact authorized delta or unchanged> | <test, request, trace, or observation> |

`Unchanged` is a binding constraint. Absence from the table is not permission to
alter that seam.

## Hold the authority boundary

- Derive current behaviour from code, tests, traces, schemas, or documentation;
  do not infer an ideal backend policy.
- Add a changed contract only when it maps to an approved acceptance criterion
  or explicit approved correctness/safety constraint.
- Treat retries, idempotency, migration, compatibility, retention, recovery,
  logging, metrics, rollout, and rollback as ordinary candidate seams, never
  automatic requirements.
- An implementation selection is local only when all choices are observationally
  equivalent across the table and remain inside the approved delivery envelope.
- If correctness requires changing an unapproved seam, report the executable
  failure path and smallest proposed expansion; do not implement or plan it.

## Verification

Prefer one public feedback point that crosses the material touched seams. Add
lower-layer evidence only when the approved verification budget names a distinct
invariant it owns. Temporary diagnostics may establish current behaviour but
must not remain as production capability unless separately authorized.

Return the completed seam table to the composing skill. Do not create lifecycle
artifacts, acceptance criteria, issues, tests, or follow-up work from this policy.
