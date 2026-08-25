---
name: spike
description: Answer one important technical, product, design, planning, delivery, or review uncertainty with bounded research, a throwaway experiment, or a minimal prototype, then record the evidence and its consequence for the parent stage. Use whenever one named question cannot be resolved reliably from current evidence, including when it emerges during implementation. Do not use to implement a production feature or explore several unrelated questions.
---

# Bounded Spike

Buy one piece of information as cheaply as possible.

## Establish the contract

Before acting, state:

- **Question:** the single uncertainty being resolved;
- **Why it matters:** the decision or issue it blocks;
- **Boundary:** time, systems, files, data, and actions in scope;
- **Evidence:** the observable result that will answer the question;
- **Disposition:** whether any code is throwaway, demonstrative, or potentially reusable.

If these cannot be stated, return the work to its parent stage rather than beginning an open-ended investigation.

## Execute

1. Prefer existing documentation or a focused read-only check when it can answer the question.
2. Otherwise create the smallest isolated experiment. Keep it outside production paths and clearly mark it disposable.
   - When prose cannot answer an interaction or product-feel question, prefer an interactive prototype or a few comparable visual variants and record the selected direction as evidence.
3. Do not add production abstractions, harden unrelated code, or answer adjacent questions.
4. Capture raw evidence: commands, responses with secrets removed, timings, errors, screenshots, or test results as applicable.
5. Compare the evidence with the prior assumption.

## Record the result

Update the active `.agent/plans/<plan-slug>/PLAN.md` and every directly affected
issue. Record concise evidence and its planning consequence in that authority.
Use `evidence/<question>.md` only when substantial raw material cannot be
summarized safely, and link it from the plan or issue. Record:

- question and conclusion;
- raw evidence location or concise reproduction steps;
- assumption confirmed or invalidated;
- decision enabled;
- remaining uncertainty;
- recommended next action.

Do not silently promote spike code into production. Recommend deletion, retention as a fixture/example, or deliberate rewriting.

## Completion

Stop as soon as the named question is answered or the boundary is exhausted. Return one of: **answered**, **inconclusive with evidence**, or **blocked by a specific prerequisite**. Route the result to the stage that raised it: `$problem-discovery`, `$project-discovery`, `$feature-discovery`, `$wayfinding`, `$solution-design`, `$issue-planning`, `$vertical-delivery`, `$code-review`, or `$integration-review`.

## Handoff

Persist whether the spike answered the question, its evidence, blocker, route,
next action, and compact launcher in `PLAN.md` and affected issues. If one user
answer or permission is required, state the conclusion reached so far, explain
the remaining uncertainty, and ask one precise question. Otherwise return the
result to the parent stage, which may continue in a fresh worker without user
intervention. Do not print an internal routing block or absorb the parent stage.
