---
name: planning
description: Create a plan from the current session's shared understanding between the agent and the user. A plan should be considered a parent task, issues should be considered child tasks of the parent.
---

- Synthesise the shared understanding already known from this session. Don't repeat settled discovery; if planning exposes a gap that would materially change the plan, reopen only that gap.
- Understand the current state of the project, if you haven't already, via exploration before starting the planning process.
- Use the questioning skill when asking the user anything.

# Process

1. Create a plan file at ./.agent/plans/<plan-name>/PLAN.md, using a short description of the task as the new directory <plan-name>. The body should match the **Parent** format.

2. Compile child tasks given the parent, splitting by independently verifiable outcome, whatever the size. Each child task must be verifiable on its own. A single child task is fine when splitting creates no useful boundary. Child tasks should be saved locally at ./.agent/plans/<plan-name>/tasks/<task-name>.md using the **Child** format. Child tasks should use a short description of the task plus a number, e.g. `01-update-README`.

3. Ensure the child tasks are linked within the parent PLAN.md.

## Parent

<h1> Title </h1>

<main>

<h3> Problem statement heading </h3>

A short description of the problem statement, including the main points of the shared understanding between the agent and the user. Any key evidence which underpins the overall understanding should be added too.

<h3> Scope </h3>

What is in scope and what is explicitly excluded.

<h3> Acceptance Criteria </h3>

List the acceptance criteria

<h3> Done means </h3>

Where the work ends, e.g. local changes, reviewed, PR opened, merged or deployed.

<h3> Linked Tasks </h3>

List all child tasks in an implementation order. They should highlight whether they're dependent or block on another child task. Where there's no dependency highlighted, the child task is deemed that it can be implemented in parallel if desired by the user.

</main>

## Child

<h1> Title </h1>

<main>

<h3> Problem statement heading </h3>

A short description of the problem statement, including the main points of the shared understanding between the agent and the user. Any key evidence which underpins the overall understanding should be added too.

<h3> Serves </h3>

The parent acceptance criteria this child task contributes to.

<h3> Verification </h3>

A clear, verifiable statement needs to be defined, this is an ultimate oracle for the child task. Without the tasks being verified against this statement, the child task cannot be deemed complete.

</main>
