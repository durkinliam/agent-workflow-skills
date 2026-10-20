---
name: plan
description: Turn established software intent and research into a reviewable implementation plan; no production edits.
---

# Plan

Read the outcome, research and relevant source. Resolve gaps that could change
the design; agree bounded experiments for implementation-dependent unknowns.

Produce a concise plan:
- Outcome, acceptance criteria, boundaries and non-goals.
- Design: responsibilities, interfaces, data flow and consequential choices.
- Ordered implementation steps tied to the criteria.
- Verification: distinguishing checks, inputs, environment, access and limits.
- Remaining decisions and completion destination.

Explain important alternatives with a concrete example and recommendation.
Plan useful tests before production changes by default; allow justified exceptions.
Resolve essential verification gaps rather than treating mocks or CI as proof of
an unexercised integration.

Keep small changes together. Split only when implementation and debugging need
separate contexts, using independently verifiable slices. Defer later decisions
until needed. Reuse existing approval; obtain any missing agreement before Deliver.

After substantial exploration, default to a fresh implementation context with
the approved plan, research brief and source references, not the conversation.
Use one concise working record where useful; see [records](references/records.md).
For planning-only requests, stop with the proposed plan.
