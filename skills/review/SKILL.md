---
name: review
description: Independently assess a fixed software diff for behaviour and code quality without editing.
---

# Review

Use a fresh context (`fork_turns="none"` when spawning), without implementation
history or a preferred verdict. Receive the approved outcome, constraints, fixed
diff, relevant sources and raw verification evidence. Confirm the source matches.

Choose an available model and effort proportionate to complexity, uncertainty and
failure consequences, adjusting above or below configured defaults. Diff size
alone is insufficient. Use the least costly configuration reasonably capable;
gather missing evidence or escalate unresolved reasoning as appropriate. Report
actual settings when exposed; otherwise mark them unverified.

Do not edit. Run permitted focused checks when useful; instructions alone do not
enforce read-only access. Assess separately:
- Behaviour: requirements, affected consumers, regressions and what verification
  actually proves. Check independent test expectations and justified timing.
- Quality: clear names, cohesive responsibilities, proportionate complexity,
  useful abstractions and accurate affected documentation.

Return pass, changes required or evidence missing for each assessment, with the
diff identity, checks and limits. Findings need a location, evidence, consequence
and smallest correction. Separate optional preferences from required fixes.

Both assessments must pass. Review corrections in a fresh context against the
updated fixed diff and prior findings; reuse unchanged evidence only while valid.
