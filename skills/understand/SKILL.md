---
name: understand
description: Clarify a software request or investigate unexpected behaviour before planning a change. Use when intent, causes or relevant code are unclear; skip questions already answered by evidence.
---

# Understand

Establish what the user needs, what is known, and what must be learned before
the next decision. Do not select a solution by guessing the user's intent.

## Establish the facts

Read the prompt, relevant conversation, repository instructions, code and
documents. Trace only the paths needed to understand the request. Separate the
observed behaviour, expected behaviour and suggested explanation or remedy.
For a new project, establish the intended user, outcome and constraints instead.

Treat a proposed cause as a hypothesis. Seek observations that distinguish it
from plausible alternatives. Inspect the actual affected interface or consumer;
a passing adjacent check cannot rule out the reported problem. State what each
observation establishes and what remains unknown. Do not turn correlation,
source equality or a plausible explanation into a confirmed cause.

## Resolve uncertainty without a questionnaire

Use available evidence before asking. When the prompt, context, code and
documents cannot establish an answer, choose the appropriate next action:

- Ask the user about unresolved intent, expected behaviour or a consequential
  trade-off before committing to an interpretation. Explain the concrete
  difference the answer makes. Prefer one focused question that unlocks several
  later answers; reassess after the response instead of asking dependent
  questions in advance. Offer meaningful options when they help.
- Investigate technical facts or run an authorized, bounded experiment when
  observation can answer the question. State the question, permitted actions
  and distinguishing result first. Keep prototypes outside production paths.
- Defer a question needed only later. Record what is unknown and which decision,
  implementation step or experiment will require its answer. Do not silently
  turn it into an assumption or approved requirement.

Some answers emerge only through implementation or testing. Bring those unknowns
to Plan so the user can agree a bounded way to learn them. Do not demand answers
to the whole project before the next useful step. Ordinary implementation
choices are agent-owned only when they preserve the agreed behaviour and bounds.

## Establish how success could be observed

Identify the result that would demonstrate the intended outcome, the plausible
wrong result it must distinguish, and the relevant inputs and environment. Name
missing access or evidence. Plan must settle a usable verification approach
before delivery; a test count or a green CI run is not a success definition.

For a requested retrospective, compare independent attempts and successful
counterexamples. Check existing safeguards before proposing another rule; a
repeated instruction is not evidence that reliability improved.

## Finish

Return the established outcome, supporting evidence, unresolved questions and
next decision. Stop a read-only investigation at its requested destination.
When planning is authorized, continue with Plan without a new conversation or
ceremonial handoff. Reuse the existing local plan if one is needed; do not create
an artifact merely because this skill ran. No production edits are authorized
by investigation alone.
