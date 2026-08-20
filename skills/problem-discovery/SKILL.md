---
name: problem-discovery
description: Investigate an ambiguous symptom, issue report, surprising result, or proposed fix in an existing system to identify the underlying user, product, data, or software problem before choosing a remedy. Use when the prompt may mistake a symptom for a cause, when observed behavior conflicts with user expectations but the failure mode is unclear, or when domain knowledge could distinguish competing explanations. Return evidence-backed problem theses and discriminating next steps. Do not use when the problem and outcome are already established, for greenfield project discovery, to answer one already-bounded question, or to implement a fix.
---

# Problem Discovery

Turn an issue-shaped prompt into the strongest problem statement the available
evidence supports. Stay read-only and solution-neutral.

## Establish the inquiry

1. Restate separately:
   - the observed symptom and affected user or operation;
   - the user's suspected cause or requested fix;
   - the expected behavior and why the difference matters;
   - known scope, recency, frequency, and counterexamples.
2. Treat causes, labels such as “bug,” and proposed remedies as hypotheses. Do
   not require the user to phrase the true problem correctly.
3. Identify the few unknowns that could change the problem classification or
   the next safe route. Defer implementation questions.

## Investigate

1. Read applicable repository instructions and sources of truth.
2. Reproduce or inspect the symptom when safe and proportionate. Trace only the
   code, tests, documentation, configuration, data lineage, runtime evidence,
   and recent changes needed to explain it.
3. Compare actual behavior with every available expectation source: tests,
   contracts, product copy, documentation, configuration, historical decisions,
   and the user's domain model. Do not assume any one source is correct.
4. Generate competing explanations before converging. Consider at least:
   - implementation or integration defect;
   - invalid, stale, transformed, or mismatched data;
   - configuration, environment, or operational-state difference;
   - product-policy or model-coherence mismatch;
   - correct behavior presented or documented misleadingly;
   - incorrect or incomplete user expectation.
   Discard categories contradicted by evidence; do not manufacture alternatives.
5. Seek discriminating evidence, not a repository-wide audit. Prefer checks that
   raise one thesis while lowering another.
6. Ask the user one precise domain or use-case question only when available
   evidence cannot answer it and the response would materially change thesis
   ranking or routing. Explain which alternatives the answer distinguishes.

## Synthesize theses

Return exactly one thesis when evidence clearly converges. Put materially tested
but contradicted explanations under **Rejected hypotheses**, not in the ranked
thesis list. Otherwise return two or at most three ranked viable theses; do not
pad the list with weak alternatives. For each thesis include:

- **Problem thesis:** the underlying problem, not merely the visible symptom;
- **Classification:** defect, data, operations/configuration, product policy,
  presentation/documentation, expectation, or mixed;
- **Confidence:** high, medium, or low, with the reason;
- **Supporting evidence:** concrete source references and observations;
- **Contradicting evidence:** meaningful evidence against it, or `none found`;
- **Falsifier/discriminator:** the cheapest observation or answer that would
  materially lower or separate it;
- **Consequence:** who or what is affected and why it matters.

State the reconstructed problem in one sentence. Explicitly distinguish facts,
inferences, assumptions, and unresolved user knowledge. If no thesis is yet
defensible, say so and name the missing discriminating evidence; do not promote a
plausible story to a finding.

## Route without solving

Choose exactly one next route:

- `direct` for a small, low-consequence correction with an obvious boundary and
  oracle;
- `$issue-planning` when a high-confidence bounded bug or correction needs a
  durable Ready issue;
- `$feature-discovery` when a likely feature area is identified but its execution
  paths, contracts, seams, or feasibility remain broadly unclear;
- `$wayfinding` when the symptom spans enough systems, product questions, or
  decision dependencies that no honest problem thesis can be reached in one
  coherent discovery session;
- `$spike` when one named experiment or evidence question can discriminate the
  remaining theses;
- `$solution-design` when the problem is established but product, model,
  interface, or system policy must be chosen;
- `user` when one domain or irreversible product decision is indispensable.

Do not propose a backlog, select an architecture, edit production files, or
present a remedy as approved. A brief candidate-remedy direction may clarify why
the route differs, but keep it subordinate to the thesis.

## Artifact

Use the repository's planning convention. Otherwise, when project writes are in
scope, create or update `docs/plans/<problem-name>/research/problem-discovery.md`,
link it from the parent plan, and keep `docs/agent/index.md` link-only. Record the
symptom, expectation, inquiry boundary, evidence, ranked theses, discriminators,
user answers, reconstructed problem, and route. If the user requested analysis
only or writes are not in scope, return the same evidence in chat.

## Completion and handoff

Stop when one strong thesis supports an honest route, a small ranked set exposes
the cheapest discriminator, or one precise user answer is required.

End with: **Stage result** (`Problem established`, `Theses ranked`, or `Problem
discovery blocked`); **Destination status** (`In Progress`, `Paused`, or
`Complete`); **Control** (`driver`, `user`, or `none`); **To** (one skill,
`direct`, `user`, or `none`); **Artifact** (local path or inline result);
**Evidence**; **Problem thesis** (one sentence or `not yet established`);
**Blocking item** (one precise prerequisite and owner, or `none`); and exactly
one **Next action** (or `none` only when the destination is complete). Reserve
destination `Complete` for a passed terminal audit.

Then add **Continuation artifact** (path, `inline`, or `none`) and **Next prompt**.
For a skill or direct route, provide a compact launcher naming the authorized
destination, repository, authoritative artifact, and stop conditions. For
`user`, ask the single discriminating question and name the theses it separates.
For `none`, write `Next prompt: none`. When project writes are already in scope,
persist the launcher at the parent plan's `handoffs/next.md`, link it from
`docs/agent/index.md`, and supersede stale launchers. Keep it under 1,500
characters and link authoritative evidence rather than replaying it.
