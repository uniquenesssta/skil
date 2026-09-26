# AI Software Development Guidelines

Use these guidelines for software design, implementation, repair, and verification. [AGENTS.md](AGENTS.md) owns task scope, instruction loading, authorization, tools, and continuity. [AI_PROJECT_RULES.md](AI_PROJECT_RULES.md) owns delivery, naming, and project records. Apply only the parts relevant to the current request.

**Choose the most appropriate solution. Simplicity is a tiebreaker between equally sound designs, not a reason to omit necessary structure or leave a repair incomplete.**

## 1. Understand the Actual Task

- Inspect the relevant code, callers, data flow, dependencies, conventions, and available verification before choosing a design. Expand inspection when evidence reveals an affected dependency or path; do not scan unrelated subsystems merely for completeness.
- Establish the requested outcome, material constraints, impact boundary, and observable completion criteria. Use the current task and confirmed project direction; do not invent future requirements.
- Distinguish facts established by code, logs, tests, or contracts from assumptions and untested hypotheses. Investigate uncertainties that can change the implementation or its correctness.
- Spend more analysis on changes that are costly to reverse or affect compatibility, persistent data, concurrency, or external systems. Keep routine choices proportionate to their consequences.

## 2. Design and Module Boundaries

Evaluate correctness, architectural fit, responsibility boundaries, compatibility, maintainability, testability, reversibility, and expected change. Implement the requested behavior with the supporting structure it actually needs. Do not add speculative extension systems, generalized configuration, or abstractions solely for hypothetical reuse.

### Decide Where Behavior Belongs

- Identify the responsibility that owns each change. Extend an existing module when the behavior shares that responsibility and reason to change; introduce a module when a distinct responsibility, state owner, or dependency boundary makes the implementation clearer and safer to evolve.
- Evaluate decomposition when a file mixes unrelated feature flows, requires conflicting dependencies or test setups, accumulates feature-specific branches, or causes changes in one capability to disturb another.
- File length, caller count, single use, and independent testability are assessment signals, not automatic splitting rules. A single-use component can still own a necessary responsibility; a separately testable helper can still belong with its caller.
- Do not keep unrelated logic together to minimize file count, or create one file per function to appear modular. Keep tightly coupled private details together when they serve the same responsibility and lifecycle.
- Avoid mixing business rules, persistence, transport, UI state, and orchestration unless the architecture establishes a cohesive reason to combine them. Generic names such as `utils`, `helpers`, `common`, `manager`, or `service` do not justify unrelated contents.

### Preserve Structural Integrity

- Keep one authoritative owner for each state, business rule, and side effect. Expose explicit interfaces and a clear dependency direction; avoid circular dependencies, hidden cross-module mutation, and duplicated state or logic.
- Do not add pass-through layers without a concrete architectural purpose. Preserve extension boundaries required by confirmed plans without implementing speculative features.
- When the touched code already mixes responsibilities, evaluate extraction of the affected responsibility and directly required support. Perform it when needed for a sound repair or safe extension within the actual impact boundary; do not use the task to justify an unrelated whole-project rewrite.
- After structural changes, verify affected imports, public interfaces, state ownership, dependency direction, and call paths using the checks defined in Section 4. Necessary structure must not be removed merely to reduce the diff.

## 3. Repair the Complete Affected Chain

- Identify the root cause and its affected upstream and downstream paths, shared logic, state synchronization, error handling, persistence, and compatibility behavior. A symptom disappearing at one entry point is not sufficient when the same cause remains on another confirmed affected path.
- Include same-root issues supported by a reproducible failure, code path, test, or explicit contract. Investigate credible suspicions before treating them as confirmed; sufficient code or contract evidence can justify a repair even when a runtime reproduction is unavailable.
- Fix every confirmed affected point within the task's impact boundary. Do not leave known same-root defects merely to minimize changed lines or files. Perform supporting refactors, interface changes, migrations, and structural repairs when necessary to complete that chain correctly.
- Record unrelated findings for later work instead of silently expanding the current task. Do not combine the repair with unrelated refactors, formatting, comment rewrites, or speculative hardening.
- Preserve behavior, interfaces, data, configuration, build workflows, and runtime compatibility except where the task requires a change. For a necessary breaking or destructive change, establish the reason, affected scope, migration and rollback or recovery approach before implementation; handle authorization through [AGENTS.md](AGENTS.md).
- Handle relevant failure modes at file, network, process, persistence, concurrency, and third-party boundaries. Choose mechanisms for demonstrated requirements and credible failure paths, not imagined capabilities.
- Remove code, imports, files, and temporary workarounds made unnecessary by this repair. Preserve unrelated pre-existing dead code unless it materially affects the repair.
- Every intentional or generated change must trace to the requested result, a confirmed affected path, necessary supporting structure, or verification.

## 4. Verify the Result

Choose evidence appropriate to the change, using the project's existing verification approach and required gates. Do not invent commands, tests, results, or platform capabilities.

| Change | Verification focus |
| --- | --- |
| Text, documentation, or a low-impact local edit | Inspect the actual result, affected links or rendering, and the diff; run applicable project gates. Do not add tests that merely restate the edit. |
| New behavior | Verify the main path, relevant boundaries, and failure cases. Add meaningful tests when they protect the behavior or are required by the project. |
| Bug fix | Reproduce the failure when feasible; otherwise establish other evidence. Verify the original path and confirmed same-root paths, with a regression check appropriate to the risk. |
| Refactor or shared state change | Verify preserved behavior, affected callers, state consistency, interfaces, and dependency boundaries. |
| Platform-specific or external-system behavior | Use the required target environment when available. Separate static checks, builds, simulations, and actual integration or device acceptance. |

- Review the final diff for unintended scope, regressions, incomplete cleanup, accidental generated changes, and omissions across the affected chain.
- Diagnose failing checks before changing code. Repair failures introduced by the change and failures within the current scope. Establish evidence for unrelated pre-existing failures or environment blockers; do not relabel an unexplained failure as pre-existing or expand into unrelated repairs to make all checks green.
- If a required check cannot run, complete feasible relevant alternatives and state what remains unverified, why, and the next concrete verification step. A passing build or substitute check proves only what it exercised.
- Once relevant checks and required gates pass, broaden or repeat verification only for new changes, failures, or a concrete unresolved concern. Do not repeatedly rerun identical successful checks merely to increase confidence.
- Stop optional verification when the completion criteria are met and finish delivery. If required evidence remains unavailable, report the implemented work and the specific acceptance limitation; do not claim full completion or conceal a known failure.

## 5. Communicate the Outcome

- Apply the rules without narrating compliance. Lead with the result, then the changes, relevant verification, material limitations, and any necessary user action.
- Use concise, plain language. Give technical detail when it helps the user or reviewer assess the result; avoid stock phrases, repeated disclaimers, and unnecessary process reports.
- Scale detail to the request: a routine change needs a short report; a requested audit or explanation needs enough evidence to assess its findings. Concision does not justify omitting a known defect or unverified requirement.
- When a rule or capability limit materially blocks or changes the requested work, identify the actual source and its effect. Distinguish an explicit requirement from an implementation judgment.
- Put durable details in the appropriate existing project document under [AI_PROJECT_RULES.md](AI_PROJECT_RULES.md). Keep the final response understandable without requiring the user to read earlier progress messages.
