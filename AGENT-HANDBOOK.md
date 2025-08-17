# Agent Handbook (Common)

Authoritative, shared guidance for all agents. Use this to avoid duplication across individual agent files.

## Canonical Sources
- `README.md`: Collaboration Protocol, Task Charter, Edit‑by‑Diff, Test Plan.
- `AGENTS.md`: Repository conventions (structure, style, testing, PRs).
- This file: Stack choices, CI templates, testing selection, unified checklists.

## Approval Gates
- Get explicit approval before adding/migrating toolchains, CI workflows, dependencies, public APIs, or repo settings.
- Propose 1–2 options with brief trade‑offs and a minimal plan; implement after approval.

## Stack Decision Matrix
- Node.js/TypeScript
  - Use for: web frontends, Node services, general APIs.
  - Minimal files: `package.json`, `tsconfig.json`, `src/`, `tests/`.
  - Commands: `npm run build`, `npm test`, `npm start`, `npm run lint`.
- Python
  - Use for: data/ML, scripts, APIs (FastAPI/Django).
  - Minimal files: `pyproject.toml`, `src/`, `tests/`.
  - Commands: `pytest`, `python -m <pkg>` or `uv run app.py`, `ruff format && ruff check`.
- Rust
  - Use for: CLIs, systems/perf‑critical services.
  - Minimal files: `Cargo.toml`, `src/`, `tests/`.
  - Commands: `cargo build`, `cargo test`, `cargo run`, `cargo clippy`.

## CI Templates (minimal)
- Node.js
```yaml
name: Node.js CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: '18' }
      - run: npm ci
      - run: npm test
      - run: npm run lint
```
- Python
```yaml
name: Python CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: '3.11' }
      - run: pip install -e .[dev] || true
      - run: pytest -q
      - run: ruff format --check && ruff check
```
- Rust
```yaml
name: Rust CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: dtolnay/rust-toolchain@stable
      - run: cargo build --locked
      - run: cargo test --locked
      - run: cargo clippy -- -D warnings
```

## Testing Framework Selection
- Node.js: Jest (full‑featured) or Vitest (fast).
- Python: pytest (standard) or unittest (built‑in).
- Rust: built‑in `cargo test`.
Document the choice and add at least one happy‑path and one edge‑case test.

## Unified PR Checklist
- [ ] Task Charter (Goal, Context, Scope, Plan)
- [ ] Edit‑by‑Diff summary attached
- [ ] Tests added/updated and passing locally
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`)
- [ ] Risk note for any dependency/API change
- [ ] CI configured (if applicable) and passing
- [ ] Approval received for stack/CI/dependency/public‑API changes

## Quality Gates (all changes)
- Default branch: `main`; use short‑lived feature branches.
- Keep changes small and reversible; avoid secrets; prefer least privilege.
- Mirror documented commands in CI to prevent drift.
