# Repository instructions for agents

## Purpose

This repository is the source of truth for the PlaneGuardian game design. Treat it as a professional, living design specification: preserve the intent behind a system, record important decisions, and keep changes easy to review.

These instructions apply to the entire repository unless a more specific `AGENTS.md` is added below a subdirectory.

## Working principles

- Write in English and use clear, studio-ready Markdown.
- Preserve the distinction between immutable design pillars and provisional implementation ideas.
- Explain both what a system does and why it exists.
- Do not silently turn open questions into settled decisions.
- Use repository-relative links and keep headings stable when practical.
- Prefer focused edits over broad rewrites. Preserve the author's voice and existing ideas.
- Add a numbered record under `Decisions/` when a foundational choice is accepted. Never reuse a decision number.
- Update `CHANGELOG.md` when a patch materially changes the design or repository structure.
- Do not commit generated `repository_snapshot.zip` archives.

## Document locations

- `GDD/PlaneGuardian_GDD.md` is the main, integrated game design document.
- `Decisions/` records settled choices and their rationale.
- `Lore/`, `Economy/`, `Procedural/`, and `Art/` hold supporting material that would make the main GDD unwieldy.

## Snapshot and Canvas workflow

Use this collaboration sequence:

1. The user uploads `repository_snapshot.zip` from the repository root.
2. Inspect the archive in an isolated workspace. Never extract it over an existing repository, and reject unsafe archive paths.
3. Identify the document being changed and move its working contents into a Canvas so the user and agent can revise it together.
4. Treat the uploaded snapshot as the immutable patch baseline. Make the agreed edits in the working copy.
5. Validate Markdown links, filenames, decision numbering, and the relationship between the main GDD and supporting documents.
6. Produce one Git-compatible unified patch relative to the repository root. The patch must not contain `repository_snapshot.zip`, `.git/`, editor state, or unrelated generated files.
7. Provide the patch as a downloadable file. Also provide the current `Apply-PlaneGuardianPatch.ps1` helper when it is not already available to the user or when the helper itself changes.
8. In the final response, always include an exact, copy/pasteable PowerShell command that calls the patch-sequence helper with the exact downloaded patch filename. Assume the script and patch have been copied into the repository root and the command is run there. Use this form:

   ```powershell
   ./Apply-PlaneGuardianPatch.ps1 -PatchPath "<exact-patch-filename>.patch"
   ```

9. Briefly summarize what the patch changes and mention any validation that could not be performed.

The PowerShell helper applies and stages the patch, untracks the generated snapshot archive if necessary, commits the staged changes, and creates a fresh `repository_snapshot.zip` from `HEAD`.

## Patch requirements

- Generate patches with paths prefixed by `a/` and `b/` so `git apply` works from the repository root.
- Include moves as Git-recognizable renames when possible.
- Ensure `git apply --check <patch>` succeeds against the uploaded snapshot baseline.
- Keep each patch focused on the requested change.
- Never include secrets, local absolute paths, or machine-specific configuration.
