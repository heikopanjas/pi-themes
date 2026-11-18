# Project Instructions for AI Coding Agents

**Last updated:** 2026-11-18 15:05 CET

<!-- {preamble} -->

# ⚠️ Before You Start

Run `/init-session` at the beginning of each new session, OR read this entire file before proceeding.

**DO NOT** make code changes or commits until you have done one of the above.

<!-- {mission} -->

## Mission Statement

Maintain light and dark GitHub Colorblind theme adaptations for Pi, preserving
upstream attribution and documenting palette mappings and accessibility limits.

- **Repository:** git@github.com:heikopanjas/pi-themes.git
- **Public documentation:** `README.md`
- **License and upstream notices:** `LICENSE`

## Technology Stack

- **Format:** JSON theme definitions and Markdown documentation
- **Runtime:** Pi
- **Version Control:** Git, hosted on GitHub
- **Build / Package Manager:** None currently configured
- **License:** MIT; preserve the upstream notices in `LICENSE`

## Session Protocol

When starting a new session, read this entire file and confirm you have
understood the project instructions before proceeding. Summarize the project
purpose and key conventions briefly. Do not make changes until you have
confirmed your understanding.

<!-- {principles} -->

## Primary Instructions

- Avoid making assumptions. If you need additional context to accurately answer the user, ask the user for the missing information. Be specific about which context you need.
- Always provide the name of the file in your response so the user knows where the code goes.
- Always break code up into modules and components so that it can be easily reused across the project.
- All code you write MUST be fully optimized. ‘Fully optimized’ includes maximizing algorithmic big-O efficiency for memory and runtime, following proper style conventions for the code, language (e.g. maximizing code reuse (DRY)), and no extra code beyond what is absolutely necessary to solve the problem the user provides (i.e. no technical debt). If the code is not fully optimized, you will be fined $100.

### Working Together

This file (`AGENTS.md`) is the primary instructions file for AI coding assistants working on this project. Agent-specific instruction files (such as `CLAUDE.md`, `.github/copilot-instructions.md`, `.cursorrules`) reference this document, maintaining a single source of truth.

When initializing a session or analyzing the workspace, refer to instruction files in this order:

1. `AGENTS.md` (this file - primary instructions and single source of truth)
2. Agent-specific reference file (if present - points back to AGENTS.md)

### Update Protocol (CRITICAL)

**PROACTIVELY update this file (`AGENTS.md`) as we work together.** Whenever you make a decision, choose a technology, establish a convention, or define a standard, you MUST update AGENTS.md immediately in the same response.

**Update ONLY this file (`AGENTS.md`)** when coding standards, conventions, or project decisions evolve. Do not modify agent-specific reference files unless the reference mechanism itself needs changes.

**When to update** (do this automatically, without being asked):

- Technology choices (build tools, languages, frameworks)
- Directory structure decisions
- Coding conventions and style guidelines
- Architecture decisions
- Naming conventions
- Build/test/deployment procedures

**How to update AGENTS.md:**

- Maintain the "Last updated" timestamp at the top
- Add content to the relevant section (Project Overview, Coding Standards, etc.)
- Log every change in the "Recent Updates & Decisions" log in `UPDATES.md` with:
  - Date (with time if multiple updates per day)
  - Brief description
  - Reasoning for the change
- New log entries go directly below the changelog marker in `UPDATES.md`, newest first; load the `recent-updates` skill for the full rules
- Preserve the AGENTS.md structure: title header → timestamp → main instructions

## Best Practices

### When Updating This Repository

1. **Maintain Consistency**: Keep code style consistent across the codebase
2. **Test First**: Write tests before implementing features when applicable
3. **Document Changes**: Update documentation when changing functionality
4. **Code Review**: [Describe your code review process]
5. **Date Changes**: Update the "Last updated" timestamp in this file when making changes
6. **Log Updates**: Add entries to the "Recent Updates & Decisions" log in `UPDATES.md`

### Development Guidelines

- Keep theme JSON files at the repository root, alongside `README.md` and `LICENSE`.
- Keep license links and attribution synchronized with the root `LICENSE` file.
- Use `.gitignore` for OS metadata, local editor files, logs, and environment secrets;
  allow environment example files. Keep shared agent instructions and configuration tracked.

### Security & Safety

- Never include API keys, tokens, or credentials in code
- Always require explicit human confirmation before commits
- Maintain conventional commit message standards
- Keep change history transparent through commit messages
- [Add project-specific security guidelines]

### Testing

[Describe your testing approach]

- Unit tests: [location and conventions]
- Integration tests: [location and conventions]
- Test coverage requirements: [if any]
- Testing framework: [e.g., Jest, pytest, JUnit]

### Documentation

[Describe your documentation requirements]

- Code comments: [when and how]
- API documentation: [format and location]
- README updates: [when required]
- Changelog: maintained in `UPDATES.md` (see the `recent-updates` skill)

<!-- {languages} -->



<!-- {integration} -->

## Commit Protocol

- **NEVER commit automatically** — always wait for explicit user confirmation
- Stage changes, write a conventional commits message (max 50-char subject, 72-char body lines, 500 characters total), then commit
- Commit messages must use plain text without quoting or special characters beyond the punctuation required by conventional commits
- Load the `git-workflow` skill for the full message format, character limits, and examples before committing
- Never add co-authorship trailers or any attribution naming an AI coding agent to commit messages

## Recent Updates & Decisions

Project decisions and notable changes are logged in `UPDATES.md`, below its changelog marker. The log is append-only: add new entries at the top, never edit or delete existing ones, and keep the "Last updated" timestamp in `AGENTS.md` in sync. Load the `recent-updates` skill for the entry format and full rules.

## Semantic Versioning

Automatically bump the project version after every code change and include it in the same commit. Load the `semantic-versioning` skill for the full PATCH/MINOR/MAJOR decision rules.
