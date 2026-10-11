# Executable Story Plan

Use the current Superpowers writing-plans format when available. Add the following information without duplicating shared architecture documents. Default to a capable implementer with no conversation history and limited architectural judgment.

## Header

- Story ID, parent Epic, linked requirement IDs, and one observable outcome.
- Authoritative design path and revision; baseline code revision.
- Index link for current status and immediate predecessors.
- Goal, architecture summary, technology context, and relevant global constraints.
- In scope, out of scope, and actions requiring escalation.

## Prerequisites and contracts

Name the exact predecessor outputs consumed: symbols, schema, fixture, decision, or verified behavior. List consumed and produced API signatures/types, errors, ownership and lifecycle rules where relevant. Use authoritative references plus enough excerpts for the worker to operate without hidden chat context. State readiness checks; an interface draft is not proof its runtime producer is available.

## Implementation tasks

For each independently reviewable task:

- List exact files to create, modify, remove, and verify. Name existing symbols; label proposed paths.
- Explain the intended change and exact behavior. Include key pseudocode or implementation snippets wherever prose would leave a design choice unresolved.
- Provide ordered checkbox steps. Fold incidental setup and documentation into the task that needs them.
- Specify meaningful tests/checks, commands, relevant fixtures/environment, and expected results. Test observable behavior and integration risks; do not create tests merely to mirror implementation.
- Identify likely failure cases and their expected handling rather than saying “handle errors.”
- Specify evidence returned to the supervisor and any rollback needs.

Do not require a full implementation dump just to inflate plan detail. Ordinary mechanics can remain concise; contract decisions and tricky algorithms must be explicit. Do not invent files, test runners, credentials, or passing output.

## Acceptance and handoff

Map acceptance criteria to evidence. Give the execution agent the Plan, relevant design/contracts, predecessor evidence, permitted files, constraints, and stop conditions. Require it to report deviations and unresolved blockers.

For Ready plans, resolve implementation-blocking placeholders such as “decide later” or “add appropriate validation.” If blocked, state the exact missing fact, who or what can resolve it, and which tasks cannot start. Every Story still receives a plan file; a blocked plan does not satisfy execution readiness.

The planner checks signature consistency, requirement coverage, dependency completeness, practical verification steps, and file conflicts before handoff. After upstream contracts change, revisit affected plans before execution resumes.
