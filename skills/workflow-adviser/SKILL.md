---
name: workflow-adviser
description: Classify an initial or resumed coding request and recommend exactly one cheapest safe starting route from direct work, one installed lifecycle skill, or one user decision. Use explicitly when the user asks which workflow skill to start with, or implicitly only when multiple lifecycle entry skills plausibly overlap. Do not use when the user already named a suitable skill, the route is obvious, or work is already inside a skill handoff. Give advice only and do not perform the work, create artifacts, or invoke the recommended skill.
---

# Workflow Adviser

Choose the cheapest route that can proceed safely. Route by information state, uncertainty, and consequence rather than prompt length or total destination size.

## Classify cheaply

Use the request and already-loaded skill descriptions. Do not inspect the repository, browse, call MCPs, or load full skills unless one minimal read-only check of a user-named local path is necessary to distinguish direct work from discovery.

Test routes in this order:

1. **direct** — one small, obvious, low-consequence outcome; relevant location
   and current behaviour can be established cheaply; the change can be bounded,
   reversible, and convention-following; no material design uncertainty exists;
   and one focused oracle is apparent. Do not use for
   material API, schema, data, migration, authorization, money, concurrency,
   deployment, compatibility, operational, or cross-boundary risk.
2. **`$vertical-delivery`** — one Ready issue already supplies outcome, scope, decisions, acceptance criteria, dependencies, non-goals, and oracle.
3. **`$spike`** — one precise evidence, experiment, or prototype question blocks progress.
4. **`$context-handoff`** — related work must move to a fresh context, owner, harness, repository, or worktree.
5. **`$code-review`** — a fixed material diff needs independent standards-and-intent review.
6. **`$integration-review`** — multiple verified slices have material cross-slice or operational risk.
7. **`$issue-planning`** — an approved design or simple evidence-backed plan is sufficient, but no issue yet satisfies the complete Ready contract or the outcome still needs vertical slicing.
8. **`$solution-design`** — intent and relevant evidence are sufficient, but material product, system, contract, or current-frontier program decisions remain.
9. **`$problem-discovery`** — an existing-system symptom, issue report, or proposed fix may not identify the underlying problem; competing causal, product, data, or expectation theses must be tested before choosing a remedy or feature area.
10. **`$feature-discovery`** — the problem and likely feature area are established, but the existing repository must be understood before design because execution paths, seams, or feasibility are unclear.
11. **`$project-discovery`** — an incomplete greenfield idea can be bounded coherently in one discovery session.
12. **`$wayfinding`** — a meaningful destination has multi-session decision fog and no safe vertical frontier is yet visible.
13. **user** — one product or irreversible decision is required even to choose an honest route.

Do not recommend `$wayfinding` merely because the eventual system is large. Do not recommend a lifecycle skill when direct work is already safe, but do not use `direct` to bypass a supplied Ready issue or proportionate controls for material work. If a user explicitly names a suitable skill, skip this adviser and use it.

Recommending `direct` does not authorize production editing. If the execution
contract is not yet approved, the internal launcher may authorize only the
minimum investigation needed to present that contract, then stop for user
approval. If the prompt already contains approval, the launcher may proceed
through delivery.

## Return only advice

Retain the selected route, prompt evidence, one blocker or none, exact next
action, and compact launcher as internal routing state. When an active plan
exists, persist that state in its next-action section; this advice-only skill
does not create an artifact.

If one user decision or permission is required, state the recommended route so
far, explain what the answer changes, and ask that one question. Otherwise give
the route recommendation naturally and return it to the active plan driver. The
driver may begin an authorized route or resume an authorized schedule without
asking the user to invoke a prompt. Do not perform the downstream route inside
this adviser context or print the internal routing fields.
