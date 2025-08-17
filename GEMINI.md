# GEMINI.md

Complete, self-sufficient guidance for the Gemini CLI agent when working in this repository. Gemini can execute routine workflows using only this file and README.md, while observing approval gates for structural changes.

## Purpose
Provide concise, actionable rules so a Gemini CLI–backed agent can be productive here without introducing heavy dependencies or breaking the repo's stack‑neutral intent.

## Independent Operation Capability
Gemini CLI can handle end‑to‑end tasks for existing stacks. For stack/CI/dependency/public‑API changes, propose first and proceed only after approval.
- **Technology Selection**: Choose and implement appropriate stacks
- **Full Development Cycle**: Planning, coding, testing, documentation, PRs
- **Quality Assurance**: Testing, validation, and safety verification
- **Emergency Decisions**: Resolve ambiguous situations without external input

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

## Technology Stack Proposals

Gemini CLI may propose and implement technology stacks after approval:

### Stack Decision Authority
1. **Analyze project needs** using available CLI inspection tools
2. **Select appropriate technology**:
   - **Web/API Projects**: Node.js/TypeScript
   - **Data/ML Projects**: Python
   - **System/CLI Tools**: Rust
3. **Implement minimal setup** with essential commands (after approval)
4. **Document choice** in README.md and commit message

### Technology Implementation Examples
See `AGENT-HANDBOOK.md` for minimal file lists, commands, and CI templates.

### When Requirements Are Unclear
- Prefer reversible, lightweight defaults and document assumptions
- Seek quick confirmation before committing to toolchains or CI

## Safety & constraints
- Do not add global/heavy dependencies without explicit approval in the Task Charter
- Never commit secrets; use `.env.example` entries for any required variables
- Keep changes small and reversible; add migration notes for any breaking change
- Operate independently for routine tasks; escalate stack/CI/dependency/public‑API changes for approval

## Gemini CLI specifics (guidance, not prescriptive)
- Use `--dry-run`, `--preview`, or equivalent flags when available to show intended changes.
- When invoking local scripts, prefer descriptive output and provide the exact commands you ran in the PR.
- If Gemini produces suggested code, validate it locally (run linters/tests) before committing.

## Independent Quality Verification

### Self-Validation Protocol
Before committing, verify:
- [ ] Task Charter scope strictly followed
- [ ] All acceptance checks met independently
- [ ] Tests implemented and documented (specify exact commands used)
- [ ] Build/development commands work (provide exact CLI output)
- [ ] Documentation updated following Diátaxis model
- [ ] No secrets or unnecessary dependencies added
- [ ] Commit message follows structured format
 - [ ] Approval received for any stack/CI/dependency or public‑API change

### Testing Framework Selection
When choosing testing approaches:
- **Node.js**: Jest (comprehensive) or Vitest (lightweight)
- **Python**: pytest (standard) or unittest (built-in)
- **Rust**: Built-in cargo test framework
- **Document choice rationale** in commit message

### Multi-Agent Coordination (Optional)
When other agents are present:
- Reference other agent files for consistency
- Use shared templates and terminology
- Coordinate approach but remain independently capable
- Any agent can complete any task without dependencies

## PR checklist (copy into PR description)
- [ ] Task Charter included
- [ ] Edit‑by‑Diff attached
- [ ] Tests added/updated and passing locally (describe how you ran them)
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`)
- [ ] Risk notes for any dependency/API change
- [ ] Technology stack choice documented (if applicable)
- [ ] Independent verification completed

## Gemini CLI Workflow Examples

### Complete Feature Implementation
```bash
# 1. Plan with dry-run
gemini --dry-run "implement user authentication"

# 2. Generate with preview
gemini --preview "add login/logout functionality"

# 3. Implement with verification
gemini apply && npm test && npm run lint

# 4. Document exact commands used in PR
```

### Stack Setup Workflow
```bash
# 1. Analyze project requirements
gemini analyze "determine appropriate technology stack"

# 2. Implement chosen stack
gemini --dry-run "setup Node.js/TypeScript project"
gemini apply

# 3. Verify implementation
npm run build && npm test

# 4. Document in README.md and commit
```
