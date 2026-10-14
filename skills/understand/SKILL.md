---
name: understand
description: Clarify software intent or investigate unexpected behaviour before planning. Use when the outcome, cause or relevant code is unclear.
---

# Understand

Establish the intended outcome, evidence and unknowns needed for the next decision.
Do not guess intent or choose a solution prematurely.

## Establish the facts

Read relevant context, instructions, code and documents; trace only affected paths.
Separate observed behaviour, expected behaviour and proposed causes or remedies.
For a new project, establish the user, outcome and constraints.

Test suspected causes against alternatives at the affected interface or consumer.
State what observations prove and leave unknown. Correlation, matching source and
passing adjacent checks do not confirm a cause or rule out the reported problem.

## Resolve uncertainty

Use evidence first, then:

- Ask about unresolved intent, expected behaviour or consequential trade-offs.
  Explain what the answer changes. Ask the question that unlocks later answers
  first, then reassess; offer options when useful.
- Investigate technical facts. Before an authorized experiment, state its question,
  permitted actions and distinguishing result. Keep prototypes outside production.
- Defer later questions with an explicit resolution trigger; do not turn unknowns
  into requirements. Bring implementation-dependent unknowns to Plan for an agreed
  experiment, without demanding answers to the whole project.

Routine implementation choices are agent-owned within agreed behaviour and bounds.

## Identify meaningful evidence

Identify an observation that distinguishes success from plausible failure, its
inputs and environment, and missing access or evidence. Plan must settle usable
verification before delivery; test counts or green CI alone do not define success.

For retrospectives, compare independent attempts and successful counterexamples.
Check existing safeguards before adding rules; repetition does not prove improvement.

## Finish

Report the outcome, evidence, unknowns and next decision. Stop at the requested
destination or continue authorized planning with Plan. Reuse records when useful;
no artifact or handoff is required. Investigation alone does not authorize
production edits.
