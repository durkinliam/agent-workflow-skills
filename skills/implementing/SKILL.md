---
name: implementing
description: Standards for editing code or configuration. Use before making any code changes, fix or refactor, however small.
---

- Tests must take their expected results from agreed requirements, contracts or reference values, never from what the code currently outputs; that's an agent marking its own homework.
- Every added or changed test must earn its place: it protects a named requirement or regression, and no other test already catches that break. A test added for comfort is the agent marking its own homework.
- Before reporting done, prove it for each one: break the behaviour it protects on purpose, confirm the test fails, then restore the code. Fix a test that still passes; remove one whose failures another test always catches too. Give each break and its failure to the reviewer as evidence.
- Work isn't done until there's evidence that tells success apart from a plausible failure.
- Work is reviewed by a fresh agent in a clean context, without the implementation conversation. Give it the requirements, the diff and the raw verification evidence, and let it read the surrounding source and run checks itself.
- If independent review isn't available, report it as outstanding; never imply it happened.
