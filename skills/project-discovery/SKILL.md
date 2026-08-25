---
name: project-discovery
description: Turn a greenfield project idea with little or no code into a bounded destination, evidence plan, explicit assumptions, prioritized unknowns, and first observable-outcome proposal. Use when starting a new project, validating an early product or technical idea, or deciding what must be learned before design can proceed. Use wayfinding instead when the destination is too foggy or large to hold in one discovery session. Do not use for a large feature in an established codebase or to implement production code.
---

# Project Discovery

Convert an idea into the minimum evidence needed to start safely. Treat unknowns as work, not as prerequisites the user must answer.

## Workflow

1. Capture the intended user, problem, destination, observable outcome, known constraints, and explicit non-goals. Accept incomplete input and generate the few questions that could materially change the destination or next safe step.
2. Separate unknowns into:
   - discoverable through research;
   - answerable only by a bounded experiment;
   - product or irreversible decisions requiring the user;
   - reversible choices that can use a recorded default.
3. Rank only the unknowns that threaten the next safe, expensive, or irreversible decision. Mark later uncertainty **Not yet specified**; do not design the whole product.
4. Propose the cheapest evidence-producing next step for each blocking unknown. Route one-question experiments to `$spike`.
5. Propose the smallest observable destination or candidate walking skeleton once the critical uncertainty is low enough, without choosing detailed system or program design.
6. Record candidate observable behaviours, then hand the intent, evidence, decisions, and remaining assumptions to `$solution-design`.

## Artifact

Create or update `.agent/plans/<project-name>/PLAN.md`. Include only:

- intent and non-goals;
- destination and success signal;
- known constraints;
- assumptions with confidence;
- deferred unknowns marked Not yet specified and the step they may block;
- blocking unknowns and proposed experiments;
- evidence and decisions;
- walking-skeleton proposal;
- candidate vertical behaviours;
- current next step.

Keep the living plan concise and current. Do not create stage-specific files;
subsequent skills update the same `PLAN.md`.

## Scope discipline

- Optimize for the minimum viable understanding required for the next decision.
- Research at most the highest-risk few unknowns at once.
- Avoid framework selection, complete architecture, repository scaffolding, or speculative infrastructure unless evidence makes it the next necessary decision.
- Ask only questions that cannot be answered through available evidence and would materially change the outcome.
- Mark useful but non-blocking ideas as deferred; do not expand discovery to resolve them.
- Route work to `$wayfinding` when its destination and decision frontier cannot be represented coherently in one discovery artifact.

## Completion

Stop when the project has one explicit next step: `$wayfinding` for multi-session fog, a bounded spike, a candidate walking-skeleton input to `$solution-design`, or a user decision. Report what remains unknown and why it does not block that step.

## Handoff

Persist the discovery result, evidence, Not yet specified items, blocker, route,
next action, and compact launcher in `PLAN.md`. If one user answer is required,
state what discovery established, explain what the answer unlocks, and ask that
one precise question. Otherwise return the authorized route to the plan driver,
which continues without user intervention. Do not absorb the downstream skill
or print an internal routing block.
