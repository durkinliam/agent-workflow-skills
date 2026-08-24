# Agent Workflow Skills

Fourteen composable skills for evidence-backed software discovery, design,
planning, delivery, and review. They are written for Codex and follow the
portable Agent Skills `SKILL.md` format used by the Skills CLI.

## Install

List the available skills:

```sh
npx skills add durkinliam/agent-workflow-skills --list
```

Install every skill:

```sh
npx skills add durkinliam/agent-workflow-skills --all
```

Install one skill:

```sh
npx skills add durkinliam/agent-workflow-skills --skill problem-discovery
```

## Skills

| Skill | Purpose |
|---|---|
| `workflow-adviser` | Select the cheapest safe route for a coding request. |
| `wayfinding` | Map a large destination whose delivery route remains uncertain. |
| `project-discovery` | Bound and investigate a greenfield project idea. |
| `problem-discovery` | Identify the underlying problem behind an ambiguous symptom. |
| `feature-discovery` | Map existing feature paths, contracts, seams, and risks. |
| `spike` | Resolve one important uncertainty with bounded evidence. |
| `solution-design` | Turn intent and evidence into a reviewable solution design. |
| `issue-planning` | Create an ordered, independently verifiable vertical frontier. |
| `vertical-delivery` | Implement and verify exactly one Ready vertical issue. |
| `context-handoff` | Transfer durable state to a fresh context or owner. |
| `code-review` | Independently review a fixed diff without implementing fixes. |
| `integration-review` | Review multiple verified slices as one coherent feature. |
| `hard-cut` | Remove an obsolete internal contract when a hard cut is approved. |
| `test-ownership` | Assign each behavioural invariant to one canonical test layer. |

Each skill's complete activation guidance and operating contract is in its
`skills/<name>/SKILL.md` file.

## Scope firewall

The skills treat an approved outcome and its acceptance criteria as delivery
authority. Every production, test, configuration, and task-branch artifact
change must map to a named acceptance criterion, an explicit approved constraint
or non-goal, or demonstrated correctness or safety necessity of the approved
behaviour. Conventions select among in-scope implementations; preservation,
consistency, completeness, symmetry, and future-proofing do not create scope.

Blocking review findings must name that authority, demonstrate an observable
failure or concrete executable failure path, and identify the smallest in-scope
correction. Other observations are non-blocking follow-ups requiring a separate
user decision. A demonstrated incorrect or unsafe outcome remains blocking when
its smallest correction crosses the boundary, but the reviewer still cannot
amend the Ready issue. Product-write authority does not authorize lifecycle
artifacts on the current branch.

## License

MIT
