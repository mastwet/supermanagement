# Architecture design

Use these sections as prompts, not a demand for irrelevant prose. Mark inapplicable concerns briefly. Resolve architecture before deriving implementation Stories.

## Design content

1. **Outcome and scope:** requirement IDs, observable acceptance, constraints, exclusions, authorized decisions, and unresolved questions.
2. **Current implementation:** inspected files/symbols, reusable capabilities, actual coupling, and baseline revision. Clearly distinguish proposed additions.
3. **Chosen approach:** smallest adequate design, meaningful alternatives, reason for each new abstraction/dependency, and the cheaper option considered.
4. **Boundaries and contracts:** responsibility and dependency direction per component; exact important types/signatures or schema; ownership, ordering, lifecycle, errors and cancellation where relevant. Show a compact diagram only if it clarifies relationships.
5. **End-to-end behavior:** normal path, important failure paths, resource cleanup, configuration, compatibility, and migration/rollback when the change requires them.
6. **Performance and economy:** likely hot paths and algorithmic/I/O costs, user-specified budgets, measurements needed, reused/deleted code, and justified additions. Label estimates. Avoid unsupported numeric budgets and LOC quotas.
7. **Verification and delivery seams:** acceptance evidence, integration boundaries, and enabling work needed before independent implementation can begin.

## Design readiness

- Can a worker implement each boundary without choosing the overall architecture?
- Are important contracts coherent across their consumers and producers?
- Does every new capability serve an authorized requirement?
- Is complexity justified by current needs rather than hypothetical scale?
- Are uncertainty and repository evidence distinguished?

If a central question cannot be answered from available evidence, identify a bounded investigation with a concrete output. Do not make downstream Stories Ready until that output has been incorporated.
