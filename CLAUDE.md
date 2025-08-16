# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is "Boiler" - an agent-ready template repository designed as a clean, language-agnostic starting point for best practices in agentic coding. The repository serves as a scaffold that can evolve into any stack (language, framework, tooling) while maintaining consistent collaboration protocols.

**Key principle**: This is intentionally stack-neutral. No specific language, framework, or tooling is hard-wired. The project should be filled in with chosen technologies as it evolves.

## Architecture & Structure

Currently minimal structure:
- `README.md` - Contains the complete collaboration protocol and task templates (single source of truth)
- `.git/` - Git repository
- No package managers, build tools, or language-specific files yet

The README.md serves as the comprehensive guide for all collaboration patterns, task templates, and development practices.

## Development Workflow

### Collaboration Protocol
Every task follows this rhythm (from README.md):

1. **State intent** - Goal, constraints, scope, acceptance checks
2. **Plan the change** - List impacted files, choose smallest viable change
3. **Propose the diff** - Share summary and edit-by-diff, call out risks
4. **Tests & docs** - Add/adjust tests and update docs as you code
5. **Commit & review** - Use structured commit messages, verify acceptance checks

### Safety Rails
- Do not modify files outside declared scope
- Do not add heavy dependencies or change public APIs without explicit confirmation
- Keep changes small and reversible
- Always explain intent before edits

### Task Templates
Use the reusable templates from README.md:
- **Task Charter**: structured goal/context/scope/plan/acceptance format
- **Edit-by-Diff Skeleton**: for proposing changes with clear impact summary
- **Test Plan**: stack-neutral validation approach
- **Commit Message Pattern**: type(scope) with context/change/impact/docs sections

## Commit Message Format
```
<type>(<scope>): <concise summary>

Context: <why>
Change: <what changed>
Impact: <user-visible effects / breaking changes>
Docs/Tests: <updated/added>
```

## Documentation Structure (Diátaxis Model)
Organize by user need:
- **Tutorials** - end-to-end learning journeys
- **How-to guides** - specific tasks (short and prescriptive)  
- **Reference** - factual API/configuration details
- **Explanation** - architecture, decisions, trade-offs

## Testing Approach
When testing framework is chosen:
- Prefer fast, deterministic tests close to the code
- Clearly separate test levels (unit/service/integration/e2e)
- Avoid global mutable state and time-dependent flakiness
- Propose lightweight testing framework with brief trade-off note when needed

## Git Workflow
- Default branch: **main**
- Use feature branches for work in progress
- Keep PRs small and focused
- Include Task Charter, Edit-by-Diff, and Test Plan in PR descriptions
- Link related issues

## Key Constraints
- **Language-agnostic**: Don't assume any specific stack
- **Minimal by default**: Only add what's explicitly needed
- **Template-driven**: Use the structured approaches from README.md
- **Safety-first**: Small, reversible changes with clear intent