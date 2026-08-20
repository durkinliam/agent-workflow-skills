---
name: code-review
description: Perform an independent, read-only review of a fixed diff against repository standards and approved intent. Use after a material vertical issue or before merge when correctness, safety, efficiency, legibility, design conformance, or test quality needs scrutiny. Run in a fresh context that did not implement the change; add an independent reviewer or specialist oracle for high-risk work when proportionate. Never implement fixes in the review context.
---

# Independent Code Review

Review the artifact, not the implementer's account of it.

## Fix the review surface

Establish before reviewing:

- repository, applicable instructions, and current state;
- base and head commit or an equivalent immutable diff boundary;
- parent design, issue, acceptance criteria, decisions, and non-goals;
- claimed verification evidence and skipped checks.

If the diff boundary or intended behaviour cannot be established, report that as a blocker instead of reviewing a moving or reconstructed target.

Start from a fresh context that did not implement the change. Context separation reduces trajectory bias; for security, permissions, money, migrations, concurrency, major architecture, or similarly consequential work, prefer an additional independent reviewer or specialist tool when available and proportionate.

Observe and report the review context's actual sandbox and permission profile;
requested read-only isolation is not evidence that it was enforced. With
enforced read-only isolation, proceed. With a broader observed policy, proceed
only when hard isolation is not required, explicitly forbid edits, record the
broader policy as residual risk, and have the plan driver capture and verify
exact before-and-after repository and review-artifact state. If isolation is
unobservable or any mutation occurs, reject the result as a read-only review.
The reviewer returns its report without persisting it; the plan driver may
write the durable review artifact only after the review context has ended.

## Review independently

Inspect the actual diff, affected code, surrounding contracts, and relevant tests. Do not accept summaries as evidence. Review two axes separately:

1. **Standards**
   - correctness, safety, failure behaviour, and compatibility;
   - readability, unnecessary complexity, coupling, duplication, and change locality;
   - performance or resource behaviour where material;
   - test quality, false-positive risk, missing negative cases, and conformance
     with a declared `$test-ownership` decision for changed coverage;
   - when the issue explicitly declares `$hard-cut`, unexplained old-shape
     aliases, fallbacks, coercions, adapters, dual-shape tests, or legacy
     branches; do not apply that presumption without the declaration;
   - repository instructions and established conventions.
2. **Intent**
   - acceptance criteria and observable outcome;
   - product, system, and program-design conformance;
   - agreed contracts, non-goals, and issue boundary;
   - unexplained deviations or behaviour implemented ahead of its issue.

Run proportionate focused checks when authorized and useful. Summarize successful output compactly; preserve details for failures and findings.

## Report findings

Report only actionable findings, ordered by severity, with precise file, symbol, line, command, or evidence references:

- **Blocker:** likely incorrect, unsafe, incompatible, or contrary to required intent;
- **Material:** meaningful maintainability, efficiency, test, or design-conformance risk;
- **Minor:** bounded improvement worth addressing before merge;
- **No finding:** do not invent criticism to justify the review.

For each finding state the observed evidence, consequence, and smallest acceptable correction. Keep uncertainty explicit. Separate standards findings from intent findings even when one defect affects both.

When review-artifact writes are in scope and no repository convention exists,
have the plan driver store the returned review under the active parent plan's
`reviews/<scope>-code-review.md`, link it from the canonical local issue, and
update only the review status and next action in `docs/agent/index.md`. Do not
use remote review summaries as the sole durable evidence.

## Disposition

Return one disposition:

- **Approve:** no actionable findings;
- **Approve with accepted risks:** only explicitly accepted non-blocking risks remain;
- **Changes required:** at least one unaccepted Blocker, Material, or Minor finding remains.

Route a ready fix to `$vertical-delivery`, an invalid issue boundary to `$issue-planning`, a missing or invalid design decision to `$solution-design`, and one unresolved evidence question to `$spike`. Never modify code in this review context.

After **Approve** or **Approve with accepted risks**, choose exactly one onward route from the canonical local state: the next Ready issue to `$vertical-delivery`; an exhausted frontier that still needs slicing to `$issue-planning`; a completed multi-slice feature with material integration risk to `$integration-review`; otherwise `none` with completion. Do not infer the route from the diff alone.

Any subsequent implementation change invalidates **Approve** or **Approve with
accepted risks**. Establish the new fixed review surface and obtain a fresh
independent review before relying on approval again.

## Handoff

Return control after this independent review responsibility ends. Set **Control** to `driver` when **To** is an executable authorized route or authorized scheduled wake-up, `user` only when a required user decision or permission prevents safe continuation, or `none` when the destination is complete and no onward route remains. The active plan driver may dispatch fixes, integration review, or the next Ready issue and continue the overarching task; this reviewer remains read-only.

End with: **Stage result** (`Review approved`, `Review findings`, or `Review blocked`); **Destination status** (`In Progress`, `Paused`, or `Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill, `direct`, `scheduled`, `user`, or `none`); **Artifact** (local review path or inline result); **Base/Head**; **Evidence**; **Findings**; **Blocking item** (one precise prerequisite and owner, or `none`); and exactly one **Next action** (or `none` only when the destination is complete). Reserve destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**. Keep `Next action` terse. For a skill, `direct`, or `scheduled` route, provide a compact launcher naming the authorized destination, repository, authoritative artifact, and stop conditions; the active plan driver consumes it without user intervention when executable, or at the recorded wake-up when scheduled. For `user`, provide one precise decision or evidence request. For `none`, write `Next prompt: none`. When project writes are already in scope, persist the launcher at the parent plan's `handoffs/next.md`, link it from `docs/agent/index.md`, and supersede any stale launcher; otherwise keep it inline. Keep it under 1,500 characters and link authoritative artifacts rather than replaying them.
