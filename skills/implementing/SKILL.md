---
name: implementing
description: Standards for editing code or configuration. Use before making any code changes, fix or refactor, however small.
---

- Tests must take their expected results from agreed requirements, contracts or reference values, never from what the code currently outputs; that's an agent marking its own homework.
- Work isn't done until there's evidence that tells success apart from a plausible failure.
- Work is reviewed by a fresh agent in a clean context, without the implementation conversation. Give it the requirements, the diff and the raw verification evidence, and let it read the surrounding source and run checks itself.
- If independent review isn't available, report it as outstanding; never imply it happened.
