# GEMINI.md

Guidance for the Gemini CLI agent when working in this repository.

## Purpose
Provide concise, actionable rules so a Gemini CLI–backed agent can be productive here without introducing heavy dependencies or breaking the repo's stack‑neutral intent.

## Read first (order matters)
1. `README.md` — canonical Collaboration Protocol (Task Charter, Edit‑by‑Diff, Test Plan).
2. `AGENTS.md` — repo conventions and file layout (`src/`, `tests/`, `docs/`).
3. `CLAUDE.md` and `.github/copilot-instructions.md` — agent safety rails and agent-specific expectations.

## Key rules for Gemini CLI flows
- Always start with a 2–4 bullet Task Charter (Goal, Context, Scope, Plan) and include it in PR descriptions.
- Prefer edit‑by‑diff proposals. If Gemini CLI can produce unified diffs, include them verbatim in the PR body.
- When using Gemini CLI to run code modifications, use the tool's dry‑run or preview flags before applying patches.
- Place implementation in `src/`, tests in `tests/`, docs in `docs/` and list any new commands in `README.md` and `AGENTS.md`.

## Example workflows (safe defaults)
- Inspect: read `README.md`, `AGENTS.md`, `CLAUDE.md`.
- Plan: produce Task Charter (2–4 bullets) and Edit‑by‑Diff summary.
- Generate: produce a single unified diff and run a preview (dry run).
- Validate: update tests in `tests/` and describe how you ran them in the PR.
- Submit: open a PR on a feature branch and include the PR checklist from `README.md`.

## Safety & constraints
- Do not add global/heavy dependencies without explicit approval in the Task Charter.
- Never commit secrets; use `.env.example` entries for any required variables.
- Keep changes small and reversible; add migration notes for any breaking change.

## Gemini CLI specifics (guidance, not prescriptive)
- Use `--dry-run`, `--preview`, or equivalent flags when available to show intended changes.
- When invoking local scripts, prefer descriptive output and provide the exact commands you ran in the PR.
- If Gemini produces suggested code, validate it locally (run linters/tests) before committing.

## PR checklist (copy into PR description)
- [ ] Task Charter included
- [ ] Edit‑by‑Diff attached
- [ ] Tests added/updated and passing locally (describe how you ran them)
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`)
- [ ] Risk notes for any dependency/API change

---
If you want, I can also add a tiny `examples/` entry that demonstrates a dry‑run + apply cycle using a real Gemini CLI command you prefer; tell me which CLI flags you rely on and I'll add an example section.
