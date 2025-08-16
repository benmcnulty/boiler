# WINDSURF.md

Purpose: concise, repo‑specific instructions for using Windsurf effectively in this stack‑neutral template. Defer to `README.md` as the canonical source for process.

## Canonical Sources
- `README.md`: Collaboration Protocol, Task Charter, Edit‑by‑Diff, Test Plan.
- `AGENTS.md`: repo conventions (structure, commands, style, testing, PRs).
- `CLAUDE.md`: safety rails and commit/PR patterns.

## Workflow In Windsurf
1) Plan: Draft a 2–4 bullet Task Charter (Goal/Context/Scope/Plan).
2) Scope: Select only impacted files/folders; avoid broad workspaces.
3) Compose: Generate small diffs; preview all changes before apply.
4) Implement: Add code under `src/`, tests under `tests/`, docs in `docs/`.
5) Validate: Run/describe test steps; ensure deterministic behavior.
6) Document: Update `README.md`/`AGENTS.md` with any new commands.

## File & Command Conventions
- Layout: `src/`, `tests/`, `docs/`, `scripts/`, `.env.example` (names only).
- Example commands to adopt (document if added):
  - Node: `npm run build`, `npm test`, `npm start`.
  - Python: `pytest`, `uv run app.py` or `python -m <pkg>`, `ruff format && ruff check`.
  - Rust: `cargo build`, `cargo test`, `cargo run`.

## Style & Naming
- Use auto‑formatters (Prettier/Black/rustfmt). Keep lints lightweight (ESLint/Ruff/Clippy).
- Naming: PascalCase (types/classes), camelCase (functions/vars), snake_case (Python), kebab‑case (scripts/dirs).

## Safety Rails
- Keep changes minimal and reversible; ask before adding heavy deps.
- Never commit secrets; use env vars and `.env.example` only.
- Do not modify files outside declared scope.
- Prefer explicit risk notes for API/permission changes.

## Commit & PRs
- Commits: `<type>(<scope>): <concise summary>` with Context/Change/Impact/Docs body.
- PRs: include Task Charter, Edit‑by‑Diff, Test Plan, acceptance checks; link issues; add screenshots for UI.

## PR Checklist
- [ ] Task Charter included
- [ ] Edit‑by‑Diff summary
- [ ] Tests added/updated and passing
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`)
- [ ] Risk note for any dependency/API change
