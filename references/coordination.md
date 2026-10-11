# Dependency and delivery supervision

## Project index

Maintain one compact index. Use stable IDs and relative links to existing architecture and Story plans.

| Story | Epic / requirement | Outcome | Immediate predecessors and required output | Plan | Status | Evidence / blocker |
| --- | --- | --- | --- | --- | --- | --- |

Also record authorized scope/decisions, topological waves, shared-file conflicts, and significant changes. Add an owner only when one exists. Do not invent dates, durations, progress percentages, or critical-path timing.

## DAG semantics

An edge `A -> B` means B requires a stated accepted output of A. Record immediate predecessors, not every ancestor. Keep a transitive edge only if it conveys a separate real input contract, and explain why. Validate unique IDs, known endpoints, no self-dependencies and no cycles. Every Story appears in the dependency model, including independent roots.

Derive topological waves by repeatedly taking remaining nodes whose predecessors have been removed. If nodes remain with none selectable, report the cycle rather than invent an order. Runtime readiness additionally requires accepted predecessor evidence; belonging to wave two alone does not make a Story Ready.

Parallel eligibility requires fulfilled prerequisites, settled contracts, compatible file ownership and integration capacity. Two independent Stories modifying the same file can require serialization without a logical DAG edge. Resolve shared edits through ownership or scheduling and record the conflict separately.

Use compact Mermaid for a useful dependency diagram. A table suffices for a single Story. Compute a time-based critical path only when grounded effort/duration estimates exist; otherwise describe dependency depth and bottlenecks.

### Example: optional export feature

- `S1` defines and implements the export contract.
- `S2` implements a CSV backend using S1.
- `S3` adds the UI entry using S1.
- `S4` validates the integrated export behavior using S2 and S3.

Waves: `{S1}`, `{S2, S3}`, `{S4}`. If S2 and S3 both edit the application registry, resolve ownership before parallel execution. If S2 changes the contract, revisit S1's architecture decision and S3/S4's plans; do not silently continue with inconsistent signatures.

## State and evidence

- **Planned:** Story and plan exist; not yet execution-ready.
- **Ready:** sufficiently concrete plan, settled contracts, and accepted prerequisite outputs; execution is within current authorization.
- **In progress:** an assigned worker is actively implementing it.
- **Review:** implementation and evidence are available for assessment.
- **Done:** acceptance evidence checked and required integration satisfied.
- **Blocked:** record missing prerequisite/decision/environment and previous state.

Use transitions based on evidence, not optimism. A failed acceptance check returns work to In progress or Blocked. Independent roots may be Ready immediately. A local unit check does not replace required build-matrix, migration, or end-to-end evidence.

At Epic completion verify the combined outcome and requirement coverage; do not infer it solely from individually completed Stories. Report remaining integration work explicitly.

## Change control

For any change: classify impact, locate affected contracts/Stories, traverse downstream dependencies, update affected plans and index, and invalidate stale readiness or evidence. Preserve still-valid evidence and historical decisions. Pause affected active work before it depends on stale instructions; allow unaffected work to continue.

| Change | Supervisor action |
| --- | --- |
| Local implementation correction within requirements, public contracts, acceptance and cost envelope | Revise autonomously, document briefly, update affected plans and reverify relevant behavior. |
| Internal shared-contract correction within approved architecture | Check every consumer and dependent plan, coordinate active work, then revise autonomously if no public boundary or material cost changes. |
| New feature, changed public interface or acceptance, major architecture shift, material cost increase | Present concrete options and impact for user decision before implementing that change. |
| Unknown cost/impact that might cross an approved boundary | Investigate cheaply; keep affected work Blocked until resolved or decided. |

Do not turn one corrected plan into blanket permission for unrelated refactoring. Do not lower acceptance to mark work Done. Do not manufacture tracker mutations or background execution from a general request for oversight.

## Resume and reporting

On resumption read the index, relevant plans, and current code/tracker evidence. Reconcile actual changes before assigning work. Report briefly: verified outcomes, current blockers, deviations requiring decisions, and next Ready Stories. Update existing artifacts; avoid a new status document each turn.
