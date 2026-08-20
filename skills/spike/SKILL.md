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

Update the authoritative parent artifact and every directly affected standalone
issue when they exist. When project writes are in scope and no convention
exists, record durable evidence under the active parent plan's
`evidence/<question>.md`, link it from its decision, design, or issue, and update
the affected issue state and lifecycle history plus the frontier and next action
in `docs/agent/index.md`. Record:

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

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may resume the parent stage in the overarching task, including in a fresh worker; do not absorb that parent stage into this spike context.

End with: **Stage result** (`Spike resolved`, `Spike inconclusive`, or `Spike blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local path or inline result); **Evidence**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. When project writes are already in scope, persist the launcher at the parent plan's `handoffs/next.md`, link it from `docs/agent/index.md`, and supersede any stale launcher; otherwise keep it inline. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
