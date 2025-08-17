# WINDSURF.md

Complete, self-sufficient guidance for Windsurf when working in this repository. Windsurf can execute routine workflows using this file and `README.md`, while observing approval gates for structural changes.

Purpose: concise, repo‑specific instructions for using Windsurf effectively in this stack‑neutral template. Defer to `README.md` as the canonical source for process.

## Independent Operation Capability
Windsurf can handle end‑to‑end tasks for existing stacks. For stack/CI/dependency/public‑API changes, propose first and proceed only after approval.
- **Architecture Analysis**: Understanding existing codebases and requirements
- **Technology Selection**: Choosing and implementing appropriate stacks
- **Full Development**: Planning, coding, testing, documentation, PRs
- **Quality Assurance**: Testing, validation, and safety verification

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

## Technology Stack Proposals

Windsurf may propose and implement technology stacks after approval:

### Stack Selection Process
1. **Analyze Requirements**: Review project context and constraints
2. **Choose Technology**: Select based on project type:
   - **Web/API**: Node.js/TypeScript
   - **Data/ML**: Python
   - **Systems/CLI**: Rust
3. **Implement Setup (after approval)**: Create minimal configuration and structure
4. **Document Commands**: Update README.md and AGENTS.md
5. **Verify Implementation**: Test basic workflow

### Technology Implementation Templates
See `AGENT-HANDBOOK.md` for minimal file lists, commands, and CI templates.

### When Stack Choice Is Unclear
- Prefer reversible, lightweight defaults; document assumptions
- Seek quick confirmation before committing to toolchains or CI

## Safety Rails
- Keep changes minimal and reversible; ask before adding heavy deps
- Never commit secrets; use env vars and `.env.example` only
- Do not modify files outside declared scope
- Prefer explicit risk notes for API/permission changes
- Operate independently for routine tasks; escalate stack/CI/dependency/public‑API changes for approval

## Commit & PRs
- Commits: `<type>(<scope>): <concise summary>` with Context/Change/Impact/Docs body.
- PRs: include Task Charter, Edit‑by‑Diff, Test Plan, acceptance checks; link issues; add screenshots for UI.

## Independent Quality Assurance

### Self-Validation Process
1. **Scope Verification**: Confirm changes are within declared Task Charter scope
2. **Testing Validation**: Implement and run tests, document exact commands
3. **Documentation Updates**: Ensure README.md, AGENTS.md, and docs/ are current
4. **Security Review**: No secrets, minimal dependencies, safe permissions
5. **Build Verification**: Confirm build/lint commands work as documented

### Testing Framework Decisions
When selecting testing approaches:
- **Node.js**: Jest (full-featured) or Vitest (fast)
- **Python**: pytest (standard) or unittest (built-in)
- **Rust**: Built-in cargo test
- **Document rationale** in commit message or PR description

### Multi-Agent Coordination (Optional)
When other agents are present:
- Reference other agent files for consistency
- Use shared templates and terminology  
- Coordinate approach but remain independently capable
- Any agent can complete any task without dependencies

## PR Checklist
- [ ] Task Charter included
- [ ] Edit‑by‑Diff summary
- [ ] Tests added/updated and passing
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`)
- [ ] Risk note for any dependency/API change
 - [ ] Approval received for any stack/CI/dependency or public‑API change
- [ ] Technology choice documented (if applicable)
- [ ] Independent verification completed
- [ ] Build/test commands verified and documented
