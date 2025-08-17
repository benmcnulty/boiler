# Boiler

## Template Repo Starting Point for Best Practices Agentic Coding

# Boiler — Agent‑Ready Template Repo

> **Purpose**: a clean, language‑agnostic starting point that teaches coding agents (and humans) how to work here. This file is the single source of truth; agents should derive their own tool‑specific instructions from it.

---

## TL;DR
- Keep changes **small and reversible**; explain intent before edits.
- Always update **tests** and **docs** with code changes.
- Prefer **edit‑by‑diff** or clearly scoped file edits.
- Use **structured commit messages** that reveal intent and risk.
- When unsure, ask for **one clarifying detail** and propose a minimal plan.

---

## Project Overview
Briefly describe *what this project does* and *who it’s for*. Keep stack‑neutral. Example:

> This repository hosts a service/application/library scaffold. The stack is intentionally unspecified. Fill in your chosen language, framework, and tooling as the project evolves.

**Non‑goals**: Avoid hard‑wiring a specific framework, CI/CD, or vendor. Keep guidance portable.

---

## Collaboration Protocol (for humans & agents)
**Every task follows the same rhythm:**

1) **State intent**
   - *Goal*: what outcome is desired?
   - *Constraints*: time/complexity limits, style/compatibility requirements.
   - *Scope*: which files/areas are in vs. out.
   - *Acceptance checks*: how we know it’s done.

2) **Plan the change**
   - List impacted files and predicted side‑effects.
   - Choose the smallest viable change. Prefer additive over destructive changes when possible.

3) **Propose the diff**
   - Share a short summary and an edit‑by‑diff (or tightly scoped file edits).
   - Call out risks, migrations, or breaking changes.

4) **Tests & docs**
   - Add/adjust tests appropriate to the stack.
   - Update docs *as you code* (see Documentation Model below).

5) **Commit & review**
   - Use a structured, intent‑revealing commit message.
   - Open a PR with the acceptance checks listed and verified.

> **Safety rails**: Do not modify files outside the declared scope. Do not add heavy dependencies or change public APIs without explicit confirmation in the plan.

---

## Reusable Task Templates
Use and adapt these verbatim in issues, PRs, or agent prompts.

### A. Task Charter
```text
Task: <one‑line goal>
Context: <why now / related issue / constraints>
Scope: <files / modules in and out>
Plan: <smallest viable steps>
Acceptance checks:
- [ ] Behavior matches description
- [ ] Tests pass and cover the new/changed behavior
- [ ] Docs updated (Tutorial / How‑to / Reference / Explanation)
Risk/Notes: <migration, perf, security, a11y, i18n>
```

### B. Edit‑by‑Diff Skeleton
```diff
*** Summary: <what changes and why>
*** Files impacted: <list>
*** Risks: <breaking change? data migration?>

--- a/<path/to/file.ext>
+++ b/<path/to/file.ext>
@@
- <existing code>
+ <proposed code>
```

### C. Test Plan (stack‑neutral)
```text
Intent: <what is being validated>
Levels: unit / service / integration / e2e (pick what fits this repo)
Cases:
- Happy path: <inputs → outputs>
- Edge cases: <boundaries, error handling>
- Regressions: <reference issue/PR if any>
Determinism: <how flakiness is avoided>
```

### D. Commit Message Pattern
```text
<type>(<scope>): <concise summary>

Context: <why>
Change: <what changed>
Impact: <user‑visible effects / breaking changes>
Docs/Tests: <updated/added>
```
> Use Conventional‑style prefixes if you like (`feat`, `fix`, `docs`, etc.), but any consistent, descriptive scheme is acceptable.

---

## Documentation Model (Diátaxis)
Organize docs by **user need** rather than file type. Keep this structure even in small projects:

- **Tutorials** – end‑to‑end learning journeys.
- **How‑to guides** – specific tasks (short and prescriptive).
- **Reference** – factual API/configuration details.
- **Explanation** – architecture, decisions, trade‑offs.

Agents should create or update the relevant doc type whenever behavior changes.

---

## Testing Guidance (agnostic)
- Prefer **fast, deterministic** tests close to the code they check.
- Clearly separate test levels (unit/service/integration/e2e) and name them accordingly.
- Avoid global mutable state and time‑dependent flakiness.
- Document any retries, quarantines, or known flakes in the PR description.

> If a testing framework is not yet chosen, propose one with a brief trade‑off note. Keep the default lightweight.

---

## Accessibility & UX Notes
- Use semantic structures and describe meaningful interactions in docs.
- When adding UI, include basic keyboard/interaction notes and any ARIA roles you intend to use.
- Provide alt text for images and captions for essential media.

---

## Security & Safety Notes
- Keep changes minimal by default; call out permission or trust boundary changes.
- Prefer principle of least privilege in configs and scripts.
- Avoid committing secrets. If a secret is required, document the variable name only and the secure storage location.

---

## Git & Review Etiquette
- Default branch is **main**.
- Use feature branches for work in progress; keep PRs small and focused.
- Link related issues; include the **Task Charter**, **Edit‑by‑Diff**, and **Test Plan** in the PR description.
- Reviewers verify acceptance checks and clarity of commits before merging.

---

## Agent Independence & Coordination

### Universal Agent Quick Start
**Any agent (single or multiple) should:**
1. Read this README.md as the canonical source
2. Use Task Charter, Edit-by-Diff, and Test Plan templates from above
3. Follow the 5-step Collaboration Protocol for every change
4. Maintain stack neutrality unless a stack is explicitly approved

### Agent-Specific Guidance Files
Each agent has a dedicated file with complete, self-sufficient guidance:
- **Claude Code**: `CLAUDE.md` - Full workflow with TodoWrite integration
- **GitHub Copilot**: `.github/copilot-instructions.md` - Complete GitHub integration
- **Cursor**: `.cursorrules` - Standalone Composer workflows and context management
- **Codex/General**: `AGENTS.md` - Universal conventions and safety rails
- **Gemini**: `GEMINI.md` - CLI-focused dry-run and preview workflows
- **Windsurf**: `WINDSURF.md` - File scoping and change composition

### Multi-Agent Coordination (Optional)
When multiple agents are available:
- Cross-reference other agent files for consistency
- Use shared terminology and template formats
- Coordinate but respect approval gates for structural changes (stack/CI/dependencies/public APIs)
- Agents can complete routine tasks independently; escalate structural decisions

### Technology Stack Decision Framework
When choosing a stack (agents propose; maintainers approve), follow the process below and use the common reference:

- See `AGENT-HANDBOOK.md` for the Stack Decision Matrix (Node/Python/Rust), minimal files/commands to add, and CI templates.
- Process summary:
  1) Propose 1–2 options with trade‑offs and a minimal plan
  2) Get approval before adding toolchains/CI/dependencies
  3) Implement minimally, then document commands in README and CI
  4) Keep choices reversible where possible

### Universal Quality Gates
Before any commit (any agent can verify):
- [ ] All files within declared Task Charter scope
- [ ] Tests added/updated for new/changed behavior
- [ ] Documentation updated following Diátaxis model
- [ ] No secrets or unnecessary heavy dependencies
- [ ] Commit message follows structured format
- [ ] Changes maintain stack neutrality where possible
 - [ ] Approval received for any stack/CI/dependency or public‑API change

### Template Adaptation for New Repositories
When using this as a boilerplate:
1. Copy all agent files (CLAUDE.md, .cursorrules, etc.)
2. Update project-specific sections while preserving protocols
3. Add chosen stack commands to README.md and AGENTS.md
4. Maintain this README.md as canonical source for all repos

---

## Glossary (project‑agnostic)
- **Edit‑by‑diff**: propose changes as unified diffs to make scope and intent explicit.
- **Acceptance checks**: the smallest list of verifiable outcomes that define “done.”
- **Deterministic test**: a test with the same result on repeated runs given the same inputs and environment.

---

## License & Contributions
Choose a license appropriate for your work (e.g., permissive, copyleft, or private). If you accept contributions, add a short `CONTRIBUTING.md` later that mirrors the **Collaboration Protocol** and **Task Templates** in this README.

---

## Changelog
Maintain a human‑readable `CHANGELOG.md` (do not paste raw git logs). Summarize notable changes, link PRs, and mark breaking changes clearly.

---

## Meta
This README is the contract for collaboration. If a tool or process is introduced, align it with this document or update this document first.
