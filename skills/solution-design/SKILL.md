---
name: solution-design
description: Turn established product intent and sufficient evidence into a concise, reviewable solution design covering product outcomes, system contracts, program shape, and candidate vertical behaviours. Use after discovery or wayfinding, or directly when a feature spans material design decisions, contracts, or multiple behaviours. The design may expose and route unknowns while leaving later decisions explicit. Do not use for small obvious changes, issue drafting, or implementation.
---

# Solution Design

Convert intent and evidence into the decisions worth resolving before
implementation, while using safe implementation to answer questions more
cheaply than prose when possible.

## Entry gate

Require enough to make the next material design decision safely:

- an observable product outcome and success signal;
- relevant repository evidence when a codebase exists;
- known constraints, non-goals, assumptions, and the current decision frontier.

Route a named unresolved evidence question to `$spike`. Route broad missing product intent to `$project-discovery`, a multi-session foggy destination to `$wayfinding`, and missing repository understanding to `$feature-discovery`. Resume the same design after the evidence arrives.

For an existing system, require cited evidence for the relevant execution path and extension points before defining program shape. Do not invent modules, ownership, or contracts when repository evidence is absent.

## Calibrate the design

- For a small, obvious change with no material design decision, skip this skill.
- For medium work, combine product, system, and program design in one concise artifact.
- For large, cross-boundary, or high-stakes work, make each view explicit and reviewable.

Default to a short design containing only decisions a human should review before issue planning. Omit routine implementation mechanics unless they carry contract, failure, security, or maintainability risk. Do not generate ceremony merely because a template exists.

Do not infer archival, retention, analytics, audit, restoration, reconciliation,
observability, retry, migration, compatibility, historical-data, rollback, or
operational-infrastructure requirements. Include one only when a named outcome
or acceptance criterion, explicit user-approved constraint, or concrete
correctness/safety failure path makes it part of the current decision frontier.
Otherwise leave it out or present it as a separate user decision; completeness,
preservation, symmetry, and future-proofing are not design authority.

Design to the current decision horizon. Define only the product, system, and program shape needed to make the first vertical frontier safe and coherent. Keep later boundaries, infrastructure, file trees, and ownership provisional or Not yet specified unless current evidence makes an early commitment necessary.

## Shape material decisions

Classify each open point before asking the user:

- discoverable fact: investigate it;
- reversible local choice: choose the smallest conventional option and record it
  only when consequential;
- material product or hard-to-reverse trade-off: put it to the user;
- uncertainty better answered by observable behaviour: route a bounded prototype,
  spike, or vertical slice.

Group coupled human decisions that share one scenario into a bounded **decision
packet**. A packet may resolve several branches together, but must not include a
decision whose prerequisites remain unsettled. Present the scenario, viable
options or combinations, material consequences, and the evidence that favors
one. Give a recommendation when one is defensible, name viable alternatives,
and say when the options are genuinely close. Do not invent probability scores,
force a single recommendation, or turn the packet into an exhaustive
questionnaire. Accept an answer across the whole packet, play back the resulting
interpretation briefly, and ask only about ambiguity that still changes the next
safe step.

Compare the cost of clarification with the expected cost of reversal. Stop
discussion when a bounded, observable, sufficiently reversible slice can answer
the remaining uncertainty more cheaply. Discuss first when a wrong choice would
have high fan-out or material data, security, compatibility, operational, or
rollback consequences.

## Workflow

1. Surface the few open decisions whose answers materially change the next safe, expensive, or irreversible step. Resolve them through evidence, an agent-owned reversible default, a decision packet, or an empirical feedback slice.
2. Separate established facts, user decisions, reversible defaults, assumptions, alternatives, and **Not yet specified** decisions. Record which future behaviour each deferred decision may block. Do not silently choose a material or irreversible trade-off that only the user can own.
3. Define the product view: user problem, observable outcome, success signal, workflow, constraints, and non-goals. Prefer a mockup or compact example when prose cannot establish alignment.
4. Define only the system view causally required by the current approved
   frontier. Cover relevant boundaries, contracts, schemas, data flow,
   authorization, failure semantics, compatibility, operations, rollout, or
   rollback only when the scope-authority rule above admits them. Do not settle
   later production topology or preservation behaviour merely to complete the
   view.
5. Define the program view for the current frontier at the level needed to prevent expensive surprises:
   - call-path or control-flow outline;
   - file-tree changes and ownership boundaries;
   - important types, method signatures, and state transitions;
   - testing seams and failure paths.
6. Create a structural outline of the walking skeleton and name subsequent observable vertical behaviours without prematurely designing their internals. Reject layer-by-layer sequencing. For large, cross-boundary, or high-risk work, make Structure an explicit review checkpoint; otherwise keep it in the design.
7. Give each behaviour a public feedback point: test, runtime interaction, log, event, visual state, or other reliable oracle. State which provisional decisions or assumptions the first slice will test and what evidence would validate or invalidate them.
8. Review the product, system, and program decisions for mental alignment at the current decision horizon. Confirm that unresolved later decisions do not block the first vertical frontier. Do not outsource material trade-offs to the model or require agreement about questions the first slice can answer safely.
9. At a consequential commitment boundary, optionally request a fresh independent consult. Supply the proposed decision, outcome, constraints, evidence, relevant paths, alternatives, and the one question that could change the plan. Require exactly **proceed**, **change**, or **stop**, plus the decisive reason and largest remaining risk. Treat the result as advisory evidence; it does not transfer decision authority or approve a user-owned trade-off.
10. Hand the approved current design to `$issue-planning`; do not write tactical implementation steps or production code. Return to this design when later evidence invalidates it or reaches a deferred decision.

Use small diagrams, pseudocode, call trees, file-tree diffs, and contract examples when they communicate more efficiently than prose.

## Artifact

Update the design section of `.agent/plans/<feature-name>/PLAN.md`. Include only
applicable sections:

- outcome, success signal, constraints, and non-goals;
- evidence and decisions;
- product workflow or mockup;
- system contracts and failure behaviour;
- current-frontier program shape and explicitly provisional later structure;
- walking skeleton and candidate vertical behaviours;
- verification and operational strategy;
- assumptions, accepted risks, blockers, and Not yet specified decisions with their decision horizon;
- a decision-evidence state for each material open or empirical point:
  **Provisional for slice**, **Validated by evidence**, **Invalidated**, or **Not
  yet specified**, plus the evidence or future feedback point that controls it;
- current next step.

Keep `PLAN.md` concise enough to review. Summarize established evidence rather
than replaying research. Record a material decision once in the plan and rejected
alternatives only when their reason constrains later work. Replace superseded
design text after preserving its current consequences; do not create separate
design or decision files.

## Completion

Stop when at least one coherent vertical frontier can be planned safely and will
produce useful feedback, even if its design is explicitly provisional and later
decisions remain Not yet specified. Otherwise stop when one precise evidence or
user-decision blocker prevents that frontier. Do not keep questioning merely to
make the wider design appear final.

## Handoff

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may continue the overarching task, including in a fresh worker; do not absorb issue planning or implementation into this design context.

End with: **Stage result** (`Design ready` or `Design blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local path or inline result); **Evidence**; **Vertical frontier**; **Not yet specified**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (`PLAN.md`, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Record the active launcher in `PLAN.md`'s next-action section when a plan exists; otherwise keep it inline. Do not create a separate handoff file. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
