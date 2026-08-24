---
name: issue-planning
description: Convert an approved current solution design, or a simple evidence-backed plan, into ordered and independently verifiable vertical issues with a Ready frontier. Use when a broad outcome must become small delivery tasks suitable for one focused agent context. An issue may be Ready while later feature decisions remain unknown. Do not invent issue-local architecture, implement code, or create external tracker issues unless explicitly authorized.
---

# Issue Planning

Turn an approved design or simple plan into executable work without losing scope, evidence, or dependencies.

## Workflow

1. Read the parent design or plan, applicable repository instructions, decisions, and evidence. An approved design may be explicitly provisional for the first slice; do not require the wider feature design to be final.
2. If a material product, system, or program-shape decision required by the next candidate issue remains unresolved, route that decision to `$solution-design` or `$spike`. Do not block the frontier on decisions needed only by later behaviours, and do not require a separate design for a small, obvious change.
3. Identify the walking skeleton or smallest end-to-end behaviour first.
4. Slice subsequent work by observable behaviour or evidenced risk tied to an
   approved outcome, criterion, or correctness/safety constraint, not by
   technical layer. Generic future risk is not issue scope.
5. Preserve agreed contracts and program-design decisions in the affected issue context without copying the whole design. Record the authorization source separately from technical readiness; an approved parent destination may authorize later slices that remain inside its agreed boundary.
6. Order dependencies and identify work that is genuinely independent.
7. Record later behaviours or decisions as **Not yet specified** with the issue or milestone at which they must be resolved.
8. Route unresolved evidence questions to `$spike` and mark only affected issues **Blocked**.
9. Record a change/evolution policy only when an acceptance criterion or
   user-approved constraint explicitly requires contract evolution. Do not infer
   compatibility, migration, preservation, or historical-data work merely
   because an existing shape is changing. Require `$hard-cut` only when the
   authoritative decision explicitly selects it and the issue names the
   canonical target shape and boundary evidence.
10. Mark an issue **Ready** only when it meets every readiness rule below.

A vertical issue may deliberately turn a provisional decision into evidence when
the observable behaviour, safe change boundary, rollback, and oracle are already
defined. State which decision is **Provisional for slice**, what result will
validate or invalidate it, and where the planning consequence will be recorded.
Use `$spike` instead when the production behaviour or safe boundary is itself
unknown. Implementation-as-evidence does not waive readiness.

## Issue format

Use the repository's established format or the durable
[issue record](references/issue-record.md). Each standalone issue must link its
parent plan and evidence, preserve the relevant design constraints, and define
one outcome, bounded scope and non-goals, acceptance criteria, dependencies,
replanning triggers, a change-to-criterion map, and a verification strategy.
Map every expected production, test, configuration, and task-branch artifact
change area to a named acceptance criterion, explicit approved constraint or
non-goal, or evidenced correctness/safety necessity. If an area has no mapping,
remove it from the issue. The strategy must name the
owning seam, expected test delta, focused oracle, trigger for broader checks,
delivery mode, public feedback point when distinct, critical
design-conformance checks, and why the evidence is sufficient. Chat and a
remote tracker item are not substitutes for this current local record.

## Readiness rules

Mark **Ready** only when:

- the durable issue file is current and explicitly records **Ready**;
- the issue owns one coherent observable behaviour;
- decisions and dependencies material to this issue are resolved;
- relevant contracts and program-shape decisions are explicit for complex work;
- expected scope is bounded but may span multiple technical layers;
- one agent can complete it without rediscovering feature architecture;
- at least one reliable oracle exists;
- the verification budget names one owning seam, the expected test delta, and
  when broader checks become necessary;
- non-goals prevent silent expansion.
- every expected change area and test delta has a valid scope-authority mapping;
- any provisional design point exercised by the issue has explicit validating
  and invalidating evidence plus a bounded planning consequence.

Future feature decisions do not block an issue when its outcome, contracts, oracle, and safe change boundary are already explicit. Keep those decisions visible outside the Ready issue instead of copying uncertainty into its implementation context.

Reject horizontal issues such as "build the database layer" when an end-to-end behaviour can be delivered instead. Reject broad refactoring, generic infrastructure, opportunistic cleanup, and speculative preparation.

Do not infer archival, retention, analytics, audit, restoration, reconciliation,
observability, retry, migration, compatibility, historical-data, rollback, or
operational-infrastructure requirements. A reviewer suggestion outside the
approved outcome remains a non-blocking follow-up; do not amend a Ready issue or
create a replacement issue for it without a separate user decision.

Use **Intake → Discovering → Planned → Draft → Ready → In Progress → Verified
→ Done**, with **Blocked** for one precise unresolved prerequisite. Never move
directly from Planned, Draft, or Blocked to In Progress. A material change to
the outcome, scope, dependencies, acceptance criteria, or oracle invalidates
the Ready gate; return the issue to Draft or Blocked and review it again.

Readiness does not grant production authority. Record whether the user approved
this issue or a parent destination whose outcome, boundaries, verification
budget, and stop conditions cover it. Leave an unauthorized issue Ready; do not
move it to In Progress.

## Artifact and external actions

Use the repository's local issue convention. Otherwise create one canonical file
per issue under `docs/plans/<plan-slug>/issues/` only when lifecycle-artifact
writes are explicitly authorized for the current branch,
maintain the ordered issue index in the parent `README.md`, and maintain only the
active plan plus Ready frontier in `docs/agent/index.md`.

Assign stable zero-padded issue IDs and direct parent and dependency links. The
issue file is authoritative for its lifecycle and delivery evidence; the parent
plan and workflow index are concise navigation views. Persist every state
transition in the issue's lifecycle history.

Product or implementation write authority does not authorize these artifacts.
When branch-local lifecycle artifacts are not explicitly authorized, return the
issue inline or use the separately authorized planning location.

Create external tracker issues only as optional coordination mirrors after the local issue exists and only when explicitly authorized. Put the local artifact path or repository link in the mirror; do not let the remote body become a divergent second specification. If branch-local lifecycle-artifact writes are not authorized, return Ready issue drafts in chat or use the separately authorized planning location.

## Completion

Finish with the ordered issue list, dependency notes, Blocked reasons, Ready frontier, Not yet specified decisions, and recommended next issue. Route one Ready issue at a time to `$vertical-delivery`, normally in a focused fresh context.

## Handoff

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may dispatch one Ready issue in a fresh worker and continue the overarching task; do not implement it inside this planning context.

End with: **Stage result** (`Planning ready` or `Planning blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local issue path or inline result); **Evidence**; **Ready frontier**; **Not yet specified**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Preserve issue lifecycle state separately and reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Persist the launcher at the parent plan's `handoffs/next.md` and link it from `docs/agent/index.md` only when lifecycle-artifact writes are explicitly authorized for the current branch; otherwise keep it inline or use the separately authorized planning location. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
