---
name: wayfinding
description: Map a large greenfield project or existing feature whose destination is meaningful but whose route is too uncertain for one discovery or design session. Use for multi-session fog where important product, evidence, prototype, or architecture decisions must be resolved progressively before a safe vertical frontier is visible. Do not use for a well-bounded feature, ordinary implementation planning, or production delivery.
---

# Wayfinding

Turn a foggy effort into a durable map of decisions without pretending to know the whole route.

## Establish the map

1. Name one destination, observable success signal, constraints, and non-goals. Stop if the destination itself requires a user decision.
2. Record established facts and decisions once, linking their primary evidence rather than copying it.
3. Mark unexplored territory **Not yet specified**. Do not invent questions merely to make the map look complete.
4. Create a decision item only when the question can be stated precisely and its answer changes the route, design, or next safe step.
5. Give each item one evidence mode:
   - repository or external research;
   - `$spike` for a bounded runnable question;
   - interactive or visual prototype through `$spike` when experience must be seen;
   - user decision for a product or irreversible trade-off;
   - recorded default for a reversible choice.
6. Record blocking edges and identify the current decision frontier: items whose prerequisites are satisfied now.

When several material human decisions on the frontier share one scenario, work
them as one bounded **decision packet**. Present the coupled decisions, viable
options or combinations, their different consequences, and a recommendation
only when the evidence supports one. Name viable alternatives and genuine close
calls; do not invent probability scores or require separate answers when one
scenario-level answer can resolve several items. A packet is a conversation
shape, not a new durable artifact or lifecycle stage, and it must not include
items with unsettled prerequisites.

Use the repository's planning convention when available. Otherwise maintain
`docs/plans/<name>/wayfinding/map.md`, store durable decisions once in the
parent plan's `decisions/` directory, and link the active plan from
`docs/agent/index.md` only when lifecycle-artifact writes are explicitly
authorized for the current branch. The map and project
index are indexes: link evidence and decisions instead of restating them.
Create remote tracker items only as optional coordination mirrors after the
local artifacts exist and only when explicitly authorized.

Product or implementation write authority does not authorize these artifacts.
Without explicit branch-level lifecycle-artifact authority, return the map
inline or use a separately authorized planning location.

## Resolve the frontier

- Resolve at most one coherent non-research decision packet in one focused context; it may close several coupled decision items. Parallelize only independent research with no shared write surface.
- Record the conclusion, evidence, assumptions changed, and planning consequence before closing an item.
- Add newly visible questions without expanding unrelated scope.
- Do not implement production features or convert the map directly into layer-based tasks.
- Re-evaluate the frontier after each decision. A later decision may remain open while an earlier vertical outcome becomes safe to design.
- Stop resolving discussion-only items when a bounded prototype, spike, or sufficiently reversible vertical slice can produce the missing evidence more cheaply. High-fan-out, data, security, compatibility, operational, and difficult-rollback choices still require prior evidence or human judgment.

## Exit

Hand off to `$project-discovery` for greenfield intent, `$problem-discovery` when an existing-system symptom still lacks an established underlying problem, or `$feature-discovery` when the problem is established but more repository evidence is needed. Hand off to `$solution-design` as soon as the destination and enough decisions are established to design one safe, feedback-producing vertical frontier; the whole map need not be clear. Preserve later items as Not yet specified with the future behaviour they may block.

If the effort becomes small and obvious, stop using the map rather than preserving ceremony.

## Handoff

Return control after this skill's bounded responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may continue the overarching task, including in a fresh worker; do not absorb the downstream skill into this wayfinding context.

End with: **Stage result** (`Map ready` or `Map blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local map path or inline result); **Evidence**; **Decision frontier**; **Not yet specified**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. Persist the launcher at the parent plan's `handoffs/next.md` and link it from `docs/agent/index.md` only when lifecycle-artifact writes are explicitly authorized for the current branch; otherwise keep it inline or use the separately authorized planning location. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
