# Durable issue record

Use this in the repository's authorized tracker, planning document, or checked-in
task file. It is the source of truth for readiness and delivery; chat messages only
announce its state.

```md
# <stable-id>: <short outcome>

- Status: `Intake | Discovering | Planned | Draft | Blocked | Ready | In Progress | Verified | Done`
- Parent plan: [<plan title>](../README.md)
- Dependencies: <none or stable IDs with direct links>
- Authorization: <approved issue or parent destination reference, or pending>

## Outcome
<One observable user, system, or operational behaviour.>

## Parent plan and evidence
- Plan: <link/path and revision or date>
- Facts/contracts: <relevant files, tests, traces, or research>
- Decisions: <links; identify reversible defaults>
- Change/evolution policy: <hard-cut | compatible evolution | migration | not applicable; include the canonical target shape and boundary evidence when hard-cut>
- Assumptions: <assumption, confidence, owner>
- Not yet specified: <later decision, the issue or milestone that needs it, or none>

## Scope
- Expected change areas: <bounded files, components, or interfaces>
- Out of scope: <adjacent work explicitly excluded>
- Delivery ownership: <one agent can complete this without rediscovering architecture or making a material direction>

## Change-to-criterion map
- <production/test/configuration/artifact change area> → <acceptance criterion,
  explicit approved constraint or non-goal, or evidenced correctness/safety
  necessity>
- <remove any change area that has no valid mapping>

## Acceptance criteria
- [ ] <observable success condition>
- [ ] <failure or edge condition when relevant>

## Verification strategy
- Verification seam: <one canonical interface or observation boundary>
- Expected test delta: <none | modify existing | add one canonical test>
- Oracle: <exact command, test, observation, log/event, or visual check>
- Broader checks only if: <risk or evidence trigger; never merely because code changed>
- Mode: <test-first | spike-then-test | implementation-then-test | manual/visual>
- Public feedback point: <external behaviour to exercise, or same as oracle>
- Design-conformance check: <critical constraint to inspect, or none>
- Sufficiency: <why this proves the criteria>

## Dependencies
- <issue, decision, or spike — state and relevance>

## Replanning triggers
- <evidence that invalidates the scope, contract, assumption, or oracle>

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
evidence, scope, dependencies, acceptance criteria, oracle, ownership, and
replanning triggers is explicit and current and every expected change area and
test delta has a valid change-to-criterion mapping. If one is absent, conflicting, stale,
or unverifiable, use `Draft` or `Blocked`.

Readiness and authorization are separate. Move only one Ready issue to `In
Progress` per agent/task, and only after the user has approved that issue or a
parent destination whose boundaries and stop conditions still cover it. A material change to
outcome, scope, dependencies, acceptance criteria, or oracle invalidates the gate:
return the issue to `Draft` (or `Blocked`) and obtain a new review. Mark `Verified`
only after the stated oracle passes and the complete diff has been inspected.
