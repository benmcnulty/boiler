# Repository Guidelines

This repository is a stack‑neutral starter. Keep changes small, reversible, and aligned with the collaboration protocol in `README.md`.

## Project Structure & Module Organization
- `README.md`: Single source of truth for process and templates.
- Propose code under `src/` and tests under `tests/` when a stack is chosen.
- Use `docs/` for tutorials/how‑tos/reference/explanations (Diátaxis model).
- Place helper automation in `scripts/` (shell or language‑specific), kept idempotent.

## Build, Test, and Development Commands
This repo defines no tooling yet. Add commands via your stack’s package manager or a `Makefile`/`justfile`.
- Example (Node): `npm run build` (build), `npm test` (run tests), `npm start` (dev server).
- Example (Python): `pytest` (tests), `uv run app.py` or `python -m <pkg>` (run), `ruff format && ruff check` (format/lint).
- Example (Rust): `cargo build`, `cargo test`, `cargo run`.
Document chosen commands in `README.md` and mirror in CI later.

## Coding Style & Naming Conventions
- Formatting: use an auto‑formatter for the chosen stack (e.g., Prettier, Black, rustfmt). Enforce before commit.
- Indentation: 2 spaces (web/TS), 4 spaces (Python); keep consistent within a language.
- Naming: `PascalCase` types/classes, `camelCase` functions/vars, `snake_case` for Python modules/tests, `kebab-case` for scripts and directories.
- Linting: adopt a lightweight linter (ESLint/Ruff/Clippy). Treat warnings as errors in CI where practical.

## Testing Guidelines
- Keep tests close to code: `tests/` mirroring `src/`.
- Naming: `<name>.spec.*` or `<name>_test.*` (match stack norms).
- Aim for meaningful coverage (≈80% as a guideline) and deterministic runs.
- Provide a short Test Plan in PRs (happy path, edges, regressions).

## Commit & Pull Request Guidelines
- Git history uses imperative summaries (e.g., “Add …”). Conventional prefixes are optional (`feat`, `fix`, etc.).
- Commits: concise subject; optional body with Context/Change/Impact/Docs.
- PRs: include purpose, scope, acceptance checks, linked issues; add screenshots for UI.

## Security & Configuration Tips
- Do not commit secrets. Use environment variables; add `.env.example` with variable names only.
- Principle of least privilege for scripts and CI. Call out trust‑boundary changes in PRs.

## Agent‑Specific Instructions
- Use edit‑by‑diff, tight file scopes, and the Task Charter from `README.md`.
- Update docs alongside code and propose minimal, reversible changes first.
