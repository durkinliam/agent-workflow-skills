# Working records

Use existing repository conventions when they serve the task. Otherwise keep
durable coordination in ignored `.agent/plans/<name>/PLAN.md`. A small plan can
remain in chat. Create `issues/` only when implementation context needs splitting.

## Plan

- Outcome and acceptance criteria.
- Approach, affected modules, constraints and non-goals.
- Decisions and source evidence; unresolved questions with their resolution trigger.
- Verification: observation, inputs/environment, checks, limitations and permitted operations.
- Approval and completion destination; explicit user limits, if any.
- Current status, evidence and next action; issue order only when issues exist.

## Issue, when needed

- One observable outcome and link to the parent authority.
- Relevant code, constraints and dependencies.
- Verification and any issue-specific limits or unresolved blocker.
- Status, evidence and next action.

Use simple states such as planned, in progress, verified and complete; record a
blocker when one exists. Verified means the agreed checks support their claims;
complete also requires the agreed independent review and destination. Keep an
explicit approval reference separate from status.

Replace stale working summaries rather than appending conversation transcripts.
Keep evidence with its owner; attach substantial raw evidence only when useful.
Do not create separate handoff, review or backlog files. Report adjacent ideas
inline. Never commit the local plan package or delete earlier plans without
permission. These records support continuation, not additional workflow stages.
