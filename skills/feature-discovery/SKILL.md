---
name: feature-discovery
description: Inspect an existing codebase to establish objective, evidence-backed understanding of a large or uncertain feature, including execution paths, contracts, seams, blockers, and risks. Use before solution design when repository facts or feature feasibility are unclear. Do not use for greenfield projects, to choose the solution architecture, or to implement the feature.
---

# Feature Research and Discovery

Compress repository truth into the minimum evidence needed for solution design.

## Workflow

1. Restate the requested destination, observable outcome, constraints, and non-goals. Generate the few questions that could materially change the destination or next safe step. Record proposed implementation details as hypotheses, not facts.
2. Form a neutral query plan: what must be learned about current behaviour, relevant subsystems, contracts, and feasibility before design can begin.
3. Read applicable repository instructions and sources of truth.
4. Trace the directly relevant execution path, tests, data flow, and existing extension points. Prefer running code and current implementation over stale documentation.
5. Expand inspection only when evidence identifies a dependency that can block the feature. Do not audit the repository.
6. Identify important interfaces and seams, including external contracts, persistence, messaging, authorization, and failure behaviour when relevant, without selecting a design.
7. Separate:
   - established repository facts;
   - contradictions with the request or documentation;
   - assumptions;
   - user decisions;
   - evidence gaps requiring `$spike`.
8. Mark later uncertainty **Not yet specified** with the stage or behaviour it may block.
9. Hand the evidence to `$solution-design`; route a feature too large or foggy for one coherent discovery artifact to `$wayfinding`. Do not propose implementation issues or production abstractions.

## Artifact

Create or update `.agent/plans/<feature-name>/PLAN.md`. Record:

- outcome and non-goals;
- neutral research questions;
- current execution path and relevant files;
- existing interfaces, seams, and conventions;
- external contracts and failure semantics;
- facts, contradictions, assumptions, decisions, and blockers;
- deferred unknowns and the future step they may block;
- feasible extension points and constraints without choosing between them;
- risks and current next step.

Keep only current findings, frontier, relevant Not yet specified items, and next
action. Do not create a separate research artifact.

## Scope discipline

- Optimize for the minimum objective evidence needed to make design decisions.
- Discourage implementation opinions during research; do not let the ticket's proposed solution bias the findings.
- Cite existing interfaces and patterns as evidence, not as automatic design choices.
- Do not propose repository-wide refactoring, generic infrastructure, future-proofing, or unrelated cleanup.
- Stop once solution design can proceed or one named blocker has been routed to a spike or user decision.

## Completion

Finish with a concise handoff: research location, evidence established, contradictions, blocking decisions, and whether the next action is `$wayfinding`, `$spike`, or `$solution-design`.

## Handoff

Persist the discovery result, evidence, Not yet specified items, blocker, route,
next action, and compact launcher in `PLAN.md`. If one user answer is required,
state what is known, explain what remains blocked, and ask that one precise
question. Otherwise return the authorized route to the plan driver, which may
continue in a fresh worker without user intervention. Do not absorb the
downstream skill or print an internal routing block.
