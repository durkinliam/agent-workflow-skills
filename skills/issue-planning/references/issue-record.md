# Durable issue record

Use this for an ignored local
`.agent/plans/<plan-slug>/issues/<number>-<slug>.md` file. It is the source of
truth for readiness and delivery; `PLAN.md` indexes it and chat messages only
announce its state.

```md
# <stable-id>: <short outcome>

- Status: `Intake | Discovering | Planned | Draft | Blocked | Ready | In Progress | Verified | Done`
- Parent plan: [<plan title>](../PLAN.md)
- Dependencies: <none or stable IDs with direct links>
- Authorization: <approved issue or parent destination reference, exact approved
  issue revision, or pending>

## Outcome
<One observable user, system, or operational behaviour.>

## Parent plan and evidence
- Plan: <link/path and revision or date>
- Facts/contracts: <relevant files, tests, traces, or research>
- Critical prerequisites: <evidence, unresolved dependency, or explicitly
  provisional-for-slice; label offline evidence and destination assumptions>
- Fixed decisions: <approved decisions this issue must preserve>
- Permitted implementation selections: <observationally equivalent local choices
  the implementer may make, or none>
- Change/evolution policy: <hard-cut | compatible evolution | migration | not applicable; include the canonical target shape and boundary evidence when hard-cut>
- Assumptions: <assumption, confidence, owner>
- Not yet specified: <later decision, the issue or milestone that needs it, or none>

## Scope
- Expected change areas: <exact files, modules, components, or interfaces>
- Change budget: <maximum new production files, test files/cases, dependencies,
  schemas, interfaces, configuration, and lifecycle artifacts; use zero unless
  explicitly authorized>
- Out of scope: <adjacent work explicitly excluded>
- Forbidden expansion: <behaviours and decision classes this delivery may not add>
- Delivery ownership: <one agent can complete this without rediscovering architecture or making a material direction>

## Change-to-criterion map
- <production/test/configuration/artifact change area> → <acceptance criterion,
  explicit approved constraint, or non-goal>
- <remove any change area that has no valid mapping>

## Acceptance criteria
- [ ] <observable success condition>
- [ ] <failure or edge condition when relevant>

## Verification strategy
- Verification seam: <one canonical interface or observation boundary>
- Behavioural invariant: <implementation-independent claim being proved>
- Expected test delta: <none, or exact suites/files and maximum cases permitted>
- New test files: <exact maximum, normally zero>
- Oracle: <exact command, test, observation, log/event, or visual check>
- Verification allowance: <predictable timing and finite observations, deadline,
  and stop condition within the proposed approval envelope, or not applicable>
- Broader checks only if: <risk or evidence trigger; never merely because code changed>
- Mode: <test-first | spike-then-test | implementation-then-test | manual/visual>
- Public feedback point: <external behaviour to exercise, or same as oracle>
- Design-conformance check: <critical constraint to inspect, or none>
- Sufficiency: <why this proves the criteria>

## Dependencies
- <issue, decision, or spike — state and relevance>

## Replanning triggers
- <evidence that invalidates the scope, contract, assumption, or oracle>
- <need for any change outside the approved envelope, including an additional
  requirement, decision, dependency, schema, interface, test invariant, or seam>

## Gate record
- Readiness reviewed by: <agent/person and timestamp>
- Gate result: <Ready | not Ready>
- Authorization source: <approved issue/parent reference or pending>
- Missing/blocked items: <none or exact list>

## Delivery log
- Started: <agent/person and timestamp>
- Evidence observed: <commands/results, decisions, deviations>
- Verification result: <pass/fail and exact output/link>
- Diff reviewed: <agent/person and timestamp>
- Final status and handoff: <status and next owner/action>

## Lifecycle history

| Date | From | To | Reason / evidence |
| --- | --- | --- | --- |
```

Mark an issue `Ready` only when each field needed to establish its outcome, parent
evidence, fixed decisions, permitted implementation selections, scope, change
budget, dependencies, acceptance criteria, oracle, ownership, and replanning
triggers is explicit and current and every expected change area and test delta
has a valid change-to-criterion mapping. If one is absent, conflicting, stale,
or unverifiable, use `Draft` or `Blocked`.

Concrete evidence that an unmapped change is necessary creates a boundary
finding for the user. It does not authorize the planner or implementer to add the
change to this issue.

Readiness and authorization are separate. Approval binds to the recorded issue
revision. Parent approval covers only the Ready issue IDs and revisions present
when approval was given unless it explicitly defines a bounded program envelope
that permits later issues. A newly generated or revised issue is not automatically
authorized. Move only one authorized Ready issue to `In Progress` per agent/task.
A material change to
outcome, scope, dependencies, acceptance criteria, or oracle invalidates the gate:
return the issue to `Draft` (or `Blocked`) and obtain a new review. Mark `Verified`
only after the stated oracle passes and the complete diff has been inspected.

The numeric prefix is a stable creation-order identity, not priority. Change
delivery order only in the parent `PLAN.md`. Do not create future, backlog,
review, or handoff artifacts beside the issue. Report adjacent ideas inline and
persist only approved-plan scope. Keep the issue through terminal plan
verification; post-rollout deletion of the containing plan directory remains a
manual local action unless the user explicitly authorizes it.
