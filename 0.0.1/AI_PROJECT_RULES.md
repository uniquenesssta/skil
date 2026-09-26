# Supplemental Project Rules

These rules cover delivery, file naming, and project records. [ALL_AI_CODE.md](ALL_AI_CODE.md) owns engineering design, compatibility, repair scope, module boundaries, and verification; do not duplicate those rules here. [AGENTS.md](AGENTS.md) owns loading, task execution, tools, authorization, and continuity. Use its precedence rules when applying project-specific exceptions.

## 1. Deliver a Complete Change

- Prefer the smallest complete deliverable that can be applied to an identified project baseline and then built, imported, or run as required. A patch may depend on that baseline; it does not need to run by itself.
- Include every necessary addition, modification, deletion, rename, dependency or lockfile change, migration, and application instruction. Copying only modified files is insufficient when other operations are required.
- In a repository workflow, a commit or pull request can be the deliverable when the task calls for it. Do not create a separate archive or installer unless requested or needed for use. Commit and publish only within the task's authorization.
- Provide a full package when a baseline-based change cannot be applied reliably or cannot preserve project integrity; state the concrete reason. Preserve the user's requested delivery format when it can meet the outcome.
- If dependencies, runtime requirements, or the build process change, describe the actual change and required user action. Otherwise, omit an unnecessary environment report. Follow the compatibility and migration requirements in [ALL_AI_CODE.md](ALL_AI_CODE.md).

## 2. Files and Naming

- Use concise, responsibility-based names in the feature or layer that owns the behavior. Apply module placement and decomposition criteria from [ALL_AI_CODE.md](ALL_AI_CODE.md).
- Avoid overlapping implementations, duplicate configurations, substitute files, and copied backups. Use version control or the project's designated history mechanism.
- Do not rename existing paths without a concrete need. For necessary renames, update all affected references, imports, scripts, documentation, and build paths; verify case-sensitive paths where applicable.
- Do not append incidental dates, version numbers, or suffixes such as `Final`, `New`, or `Copy` to implementation filenames. Explicitly requested version directories, release artifacts, migration names, or established project conventions are valid exceptions; they do not justify duplicate active implementations.

## 3. Project Records

- Maintain one canonical change record. By default, use the project's root `README.md` and its existing change section; add one consistent `Change Log` section when needed. If the project already designates a formal changelog or release process, retain that authority and link to it from README rather than creating a second competing record.
- Record meaningful version updates, enhancements, bug fixes, and documentation changes that affect use or execution. Update records for actual project changes, not for every conversation, read-only review, tool call, or repeated successful check.
- Keep README entries concise and outcome-focused: what changed, the resulting behavior, and necessary adoption or migration actions. Do not put an exhaustive implementation history or verification transcript into README.
- Keep architecture details in the appropriate architecture document and implementation or acceptance progress in the relevant task document. Update them when the change affects their truth; link to detailed evidence instead of copying it into several places.
- Do not create additional changelogs, fix logs, README variants, or reports without a task need. Preserve existing formal documents; create a required document only when there is no suitable existing location.
- Keep session continuity records focused on resuming work, using [AGENTS.md](AGENTS.md). They do not replace the canonical change record, task acceptance evidence, or version control.
