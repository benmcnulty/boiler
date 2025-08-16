## Purpose

Short, actionable instructions for AI coding agents working in this repository. Read `README.md` (single source of truth), then `AGENTS.md` and `CLAUDE.md` before proposing edits.

## High-level summary

- This repo is intentionally stack‑neutral. There are currently no language-specific sources, build configs, or package manifests.
- `README.md` contains the Collaboration Protocol, Task Charter, Edit‑by‑Diff skeleton, and Test Plan guidance — treat it as canonical.

## What to read first (order matters)

1. `README.md` — collaboration protocol and templates (Task Charter, Edit‑by‑Diff, Test Plan).
2. `AGENTS.md` — practical repo conventions and where to place code (`src/`, `tests/`, `docs/`).
3. `CLAUDE.md` — agent-focused constraints and safety rails.

## Key, discoverable repo rules (do these every time)

- Keep changes small and reversible; always state intent before edits (Task Charter).
- Use edit‑by‑diff style for proposed changes. Reference the Edit‑by‑Diff skeleton from `README.md` in PR body.
- When adding code, prefer `src/` for implementation, `tests/` for tests, and `docs/` for Diátaxis documentation.
- Default branch is `main`. Use feature branches for work in progress.

## Project-specific patterns and examples

- No build or test commands are present yet; if you add tooling, document commands in `README.md` and mirror them in `AGENTS.md`.
- Commit message pattern: use the repository template from `CLAUDE.md` / `AGENTS.md`:
  `<type>(<scope>): <concise summary>` with Context/Change/Impact/Docs sections in the body.
- Task Charter example to include in PRs: Goal, Context, Scope, Plan, Acceptance checks (copy from `README.md`).

## Workflows agents should follow when making a change

1. Read `README.md` Task Charter and prepare a 2–4 bullet Task Charter for the change.
2. Create an edit‑by‑diff describing exactly which files change and why (use the repo's Edit‑by‑Diff skeleton).
3. Implement the smallest viable change. Add `src/`, `tests/`, and `docs/` entries as appropriate.
4. Add or update tests close to the code (`tests/` mirroring `src/`).
5. Update `README.md`/`AGENTS.md` with any new commands or conventions introduced.
6. Submit a PR on a feature branch with the Task Charter, Edit‑by‑Diff, Test Plan, and acceptance checks.

## Safety & constraint rules (enforced)

- Do not add heavy or global dependencies without explicit approval; document reason and migration risk in the PR.
- Never commit secrets. If a secret is needed, add variable names to `.env.example` and document storage expectations.
- Do not modify files outside the declared scope in the Task Charter.

## Integration points & external deps

- There are currently no configured integrations or external services discoverable in the repo. If you add any, update `README.md` and `AGENTS.md` with: configuration keys, expected network flows, and `.env.example` entries.

## When something is missing or ambiguous

- If the stack is unspecified for a requested change, propose 1–2 reasonable stacks (Node/Python/Rust) and a minimal plan (files to add, commands to document). Ask the maintainer for approval before adding toolchains.
- If build or test commands are unclear, add them to `README.md` and `AGENTS.md` as the canonical source; include short examples (e.g., `npm run test`, `pytest`).

## PR checklist for agents (copy into PR description)

- [ ] Task Charter (Goal, Context, Scope, Plan)
- [ ] Edit‑by‑Diff summary attached
- [ ] Tests added/updated and passing locally
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`) for new behaviors or commands
- [ ] Risk note for any dependency or API change

---
If any section above is unclear or a decision (stack, test runner, CI) is required, tell me which parts to propose and I will produce a minimal Task Charter and Edit‑by‑Diff to get approval.
