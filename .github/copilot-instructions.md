## Purpose

Complete, self-sufficient guidance for GitHub Copilot when working in this repository. Copilot can execute routine workflows using only this file and README.md, while observing approval gates for structural changes.

Short, actionable instructions for AI coding agents working in this repository. Read `README.md` (single source of truth), then `AGENTS.md` and `CLAUDE.md` before proposing edits.

## Independent Operation Capability
Copilot can handle end‑to‑end tasks for existing stacks. For stack/CI/dependency/public‑API changes, propose first and proceed only after approval.

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

## GitHub Integration & External Dependencies

### Current Integration Status
- There are currently no configured integrations or external services discoverable in the repo
- GitHub Actions workflows can be added based on chosen technology stack
- Basic repository security features (Dependabot, CodeQL) should be enabled

### When Adding Integrations
- **Propose via PR**: Include what settings/workflows to enable and why
- **Secrets**: Reference required secret names; do not include values
- **Documentation**: Update README.md and AGENTS.md with configuration details
- **Workflows**: Include minimal `.github/workflows/*.yml` in the PR when approved
Note: Enabling repository features (Branch protection, Dependabot, CodeQL) may require maintainer action; include clear instructions in the PR.

### Recommended GitHub Repository Configuration
```yaml
# Enable these GitHub features when setting up:
- Branch protection rules (require PR reviews)
- Dependabot security updates
- CodeQL security scanning
- GitHub Actions for CI/CD
- Issue and PR templates
- Repository security advisories
```

## Technology Stack Proposals

Copilot may propose and implement technology stacks after approval:

### Stack Decision Framework
1. **Analyze Repository Context**: Review existing files and requirements
2. **Select Appropriate Technology**:
   - **Web/API Projects**: Node.js/TypeScript
   - **Data/ML Projects**: Python
   - **System/CLI Tools**: Rust
3. **Implement Minimal Setup (after approval)**: Basic configuration and folder structure
4. **Document in README.md**: Add commands and rationale
5. **Configure GitHub Actions**: Propose minimal CI/CD; add when approved

### Technology Implementation Examples
See `AGENT-HANDBOOK.md` for the Stack Decision Matrix and minimal CI templates.

### When Requirements Are Unclear
- Prefer reversible, lightweight defaults and document assumptions
- Seek quick confirmation before committing to toolchains or CI

## When something is missing or ambiguous

- If the stack is unspecified for a requested change, independently select from Node/Python/Rust based on project context and implement minimal setup
- Add build/test commands to `README.md` and `AGENTS.md` as the canonical source; include short examples (e.g., `npm run test`, `pytest`)
- Set up appropriate GitHub Actions workflow for chosen technology
- Document all decisions in commit messages and PR descriptions

## Independent Quality Assurance

### GitHub Integration Validation
- [ ] GitHub Actions workflows configured for chosen stack
- [ ] Branch protection rules considered (if applicable)
- [ ] Issue/PR templates align with Task Charter format
- [ ] Security scanning enabled (Dependabot, CodeQL)
- [ ] Repository settings optimized for team workflow

### Self-Validation Protocol
Before any commit:
- [ ] Task Charter scope strictly followed
- [ ] All acceptance checks met independently
- [ ] Tests implemented and GitHub Actions passing
 - [ ] Approval received for any stack/CI/dependency changes
- [ ] Documentation updated following Diátaxis model
- [ ] No secrets committed (GitHub secrets properly configured)
- [ ] Dependencies minimal and security-scanned
- [ ] Commit message follows structured format

### Testing Framework Selection
When choosing testing approaches:
- **Node.js**: Jest (comprehensive) or Vitest (fast) + GitHub Actions
- **Python**: pytest (standard) + GitHub Actions
- **Rust**: Built-in cargo test + GitHub Actions
- **Document choice** in README.md and set up corresponding workflows

### Multi-Agent Coordination (Optional)
When other agents are present:
- Reference other agent files for consistency
- Use shared templates and terminology
- Coordinate via GitHub issues and PRs
- Maintain independent operation capability

## PR checklist for agents (copy into PR description)

- [ ] Task Charter (Goal, Context, Scope, Plan)
- [ ] Edit‑by‑Diff summary attached
- [ ] Tests added/updated and passing locally
- [ ] GitHub Actions configured and passing
- [ ] Docs updated (`README.md`/`AGENTS.md`/`docs/`) for new behaviors or commands
- [ ] Risk note for any dependency or API change
- [ ] Technology stack choice documented (if applicable)
- [ ] GitHub integration optimized
- [ ] Independent verification completed

## GitHub-Specific Workflow Examples

### Complete Feature with GitHub Integration
1. **Create Feature Branch**: `git checkout -b feature/user-auth`
2. **Implement with Testing**: Write code, tests, and documentation
3. **Configure GitHub Actions**: Set up CI/CD for chosen stack
4. **Create PR**: Include Task Charter and Edit-by-Diff
5. **Review Integration**: Verify Actions pass and security scans complete
6. **Merge**: Ensure all quality gates pass

### Stack Setup with GitHub Actions
1. **Choose Technology**: Based on project requirements
2. **Create Basic Structure**: src/, tests/, configuration files
3. **Set up GitHub Workflow**: Appropriate .github/workflows/*.yml
4. **Test Integration**: Verify Actions run successfully
5. **Document Commands**: Update README.md with build/test/deploy steps
6. **Create Initial PR**: Document setup decisions and rationale
