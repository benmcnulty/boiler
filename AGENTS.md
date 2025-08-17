# Repository Guidelines

This file provides concise guidance for any coding agent working in this repository. Agents are capable of operating with just this file and `README.md`, but must respect approval gates below.

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
- Default branch: `main`. Use short‑lived feature branches.

## Security & Configuration Tips
- Do not commit secrets. Use environment variables; add `.env.example` with variable names only.
- Principle of least privilege for scripts and CI. Call out trust‑boundary changes in PRs.

## Approval Gates (must follow)
- Do not add or migrate toolchains, CI, or dependencies without an approved Task Charter and Edit‑by‑Diff.
- Do not change public APIs or repository settings without explicit approval.
- Propose 1–2 options with trade‑offs; implement only after approval.

## Agent Operation

Agents can complete end‑to‑end workflows, while observing approval gates:

### Technology Stack Authority
When no stack is present, any agent may propose to:
1. **Analyze project requirements** and constraints
2. **Select appropriate technology** (see `AGENT-HANDBOOK.md` Stack Decision Matrix)
3. **Implement minimal setup** with basic commands (after approval)
4. **Document choice** in README.md with rationale

### Stack Implementation Examples
See `AGENT-HANDBOOK.md` for minimal file lists, commands, and CI templates.

### Decision Framework
When requirements are unclear, prefer reversible, lightweight options and document assumptions. Seek quick approval before proceeding.

### Self-Validation Protocol
Before any commit, verify:
- [ ] Task Charter scope strictly followed
- [ ] Tests written and documented (explain how to run)
- [ ] Build/lint commands work (document exact commands used)
- [ ] Documentation updated for any behavior changes
- [ ] No secrets committed (use .env.example for variable names)
- [ ] Dependencies minimal and justified

### Multi-Agent Coordination (Optional)
When other agents are present:
- Reference their guidance files for consistency
- Use shared templates and terminology
- Coordinate approach but remain independently capable
- Any agent can complete any task without dependencies

## Agent‑Specific Instructions
- Use edit‑by‑diff, tight file scopes, and the Task Charter from `README.md`
- Update docs alongside code and propose minimal, reversible changes first
- Operate independently for routine tasks; escalate stack/CI/dependency/public‑API changes for approval
- When proposing a technology, document rationale and basic implementation plan
