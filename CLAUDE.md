# CLAUDE.md

This file provides complete, self-sufficient guidance for Claude Code (claude.ai/code) when working in this repository. Claude can execute routine workflows using this file and `README.md`, while observing approval gates for structural changes.

## Project Overview

This is "Boiler" - an agent-ready template repository designed as a clean, language-agnostic starting point for best practices in agentic coding. The repository serves as a scaffold that can evolve into any stack (language, framework, tooling) while maintaining consistent collaboration protocols.

**Key principle**: This is intentionally stack-neutral. No specific language, framework, or tooling is hard-wired. The project should be filled in with chosen technologies as it evolves.

## Independent Operation Capability

Claude can handle end‑to‑end tasks for existing stacks. For stack/CI/dependency/public‑API changes, propose first and proceed only after approval.
- **Architecture Analysis**: Understanding existing codebases without external dependencies
- **Stack Selection**: Making technology choices with clear rationale and implementation
- **Full Development Cycle**: From planning through code, tests, docs, and PR creation
- **Quality Assurance**: Testing, validation, and safety verification
- **Emergency Decision Making**: Resolving ambiguous situations without external input

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

## Technology Stack Proposals

Claude may propose and implement technology stacks after approval:

### Stack Decision Process
1. **Analyze Requirements**: Consider project needs, constraints, and context
2. **Propose Options**: Present 1-2 viable stacks with trade-offs
3. **Make Selection**: Choose based on project fit and team preferences (after approval)
4. **Implement Minimally**: Add basic build/test/run commands post‑approval
5. **Document Choice**: Update README.md and this file with rationale

### Common Stack Implementations
See `AGENT-HANDBOOK.md` for the Stack Decision Matrix, minimal commands, and CI templates.

### When Stack Is Unclear
- Prefer reversible, lightweight defaults; document assumptions
- Seek quick confirmation before committing to toolchains

## Independent Quality Assurance

Claude can verify work quality autonomously for routine tasks:

### Self-Validation Checklist
- [ ] Task Charter completed as specified
- [ ] All acceptance checks met
- [ ] Tests written and passing (describe test approach)
- [ ] Documentation updated following Diátaxis model
- [ ] No secrets or heavy dependencies introduced
 - [ ] Approval received for any stack/CI/dependency or public‑API change
- [ ] Scope strictly adhered to as declared
- [ ] Commit message follows structured format

### Testing Approach Decisions
When testing framework needs selection:
- **Node.js**: Jest (comprehensive) or Vitest (lightweight)
- **Python**: pytest (standard) or unittest (built-in)
- **Rust**: Built-in cargo test
- **Any Stack**: Document choice rationale in commit

## Key Constraints
- **Language-agnostic**: Don't assume any specific stack unless choosing one with approval
- **Minimal by default**: Only add what's explicitly needed
- **Template-driven**: Use the structured approaches from README.md
- **Safety-first**: Small, reversible changes with clear intent
- **Self-sufficient**: Complete tasks without requiring other agents
