---
name: issue-planning
description: Convert an approved current solution design, or a simple evidence-backed plan, into closed-world, independently verifiable vertical issues with a Ready frontier. Use when an approved outcome must become small delivery tasks suitable for one focused agent context. An issue may be Ready while later feature decisions remain unknown. Decompose and narrow approved behaviour; do not add requirements, invent issue-local architecture, implement code, or create external tracker issues unless explicitly authorized.
---

# Issue Planning

Turn an approved design or simple plan into executable work without losing scope, evidence, or dependencies.

Planning is closed-world. It may decompose, order, and narrow approved behaviour,
but every issue outcome, acceptance criterion, production capability, and test
invariant must cite an approved parent clause or evidenced correctness/safety
constraint of that behaviour. A newly discovered desirable or necessary
behaviour is a boundary finding for the user, not another issue in the authorized
frontier. Planning cannot promote an assumption, convention, reviewer suggestion,
or implementation idea into scope.

## Workflow

1. Read the parent design or plan, applicable repository instructions, decisions, and evidence. An approved design may be explicitly provisional for the first slice; do not require the wider feature design to be final.
2. If a material product, system, or program-shape decision required by the next candidate issue remains unresolved, route that decision to `$solution-design` or `$spike`. Do not block the frontier on decisions needed only by later behaviours, and do not require a separate design for a small, obvious change.
3. Identify the walking skeleton or smallest end-to-end behaviour first.
4. Slice subsequent work by observable behaviour or evidenced risk tied to an
   approved outcome, criterion, or correctness/safety constraint, not by
   technical layer. Generic future risk is not issue scope.
5. Preserve agreed contracts and program-design decisions in the affected issue context without copying the whole design. Record the authorization source separately from technical readiness. Parent approval covers only the Ready issue IDs and revisions present at approval unless it explicitly defines a bounded program envelope for later issues.
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
11. When the issue touches an API, persistence boundary, transaction, background
    job, queue, authorization boundary, clock, concurrency path, or external side
    effect, compose `$backend-change-control`. Record only the seams actually
    touched; its inventory cannot add requirements.

A vertical issue may deliberately turn a provisional decision into evidence when
the observable behaviour, safe change boundary, and oracle are already defined,
and any recovery or rollback requirement is explicitly approved. State which decision is **Provisional for slice**, what result will
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
change area to a named acceptance criterion or explicit approved constraint or
non-goal. Concrete evidence that another change is necessary creates a boundary
finding; it does not authorize the planner to add that change. If an area has no
mapping, remove it from the issue. The strategy must name the
owning seam, expected test delta, focused oracle, trigger for broader checks,
delivery mode, public feedback point when distinct, critical
design-conformance checks, and why the evidence is sufficient. Chat and a
remote tracker item are not substitutes for this current local record.
The issue must also freeze an approved delivery envelope: fixed decisions,
permitted implementation selections, exact change surface, explicit change
budget, forbidden expansion, exact test allowance, and stop conditions.

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
- the delivery envelope is enumerable enough to detect an unauthorized file,
  dependency, interface, schema, behavioural invariant, or test change;
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

Readiness does not grant production authority. Approval binds to the recorded
issue revision. Parent approval authorizes only the Ready issue IDs and revisions
present at approval unless the user explicitly approved a bounded program
envelope permitting later issues. Newly planned or materially revised issues are
not automatically authorized. Leave an unauthorized issue Ready; do not move it
to In Progress.

## Artifact and external actions

Create one canonical file per issue under
`.agent/plans/<plan-slug>/issues/` and maintain the ordered issue
table, Ready frontier, Not yet specified decisions, and next action in
`.agent/plans/<plan-slug>/PLAN.md`.

Assign stable zero-padded issue IDs in creation order and direct parent and
dependency links. IDs are identity, not priority; change execution order only in
`PLAN.md`. The issue file is authoritative for its lifecycle and delivery
evidence; the plan table is navigation, not a duplicate specification. Persist
every state transition in the issue's lifecycle history.

Create only vertical issues inside the approved plan. Report adjacent ideas and
scope-creep discoveries to the user inline; do not persist them as future work,
a backlog, or another issue.

Create external tracker issues only as optional coordination mirrors after the local issue exists and only when explicitly authorized. Put the local artifact path in the mirror; do not let the remote body become a divergent second specification.

## Completion

Finish with the ordered issue list, dependency notes, Blocked reasons, Ready frontier, Not yet specified decisions, and recommended next issue. Route one Ready issue at a time to `$vertical-delivery`, normally in a focused fresh context.

## Handoff

Persist the ordered issue list, dependency state, Ready frontier, Not yet
specified items, blocker, route, next action, and compact launcher in `PLAN.md`
and the canonical issues. If one user decision or authorization is required,
state what is Ready, explain what the answer changes, and ask one precise
question. Otherwise the plan driver dispatches the next authorized Ready issue
in a fresh worker without asking the user to invoke a prompt. Do not implement
the issue in this planning context or print an internal routing block.
