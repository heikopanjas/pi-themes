# Recent Updates & Decisions

This file is the append-only log of project decisions and notable changes, maintained by coding agents following the `recent-updates` skill. Everything below the marker line is user-owned history: slopctl never overwrites it during init or merge.

<!-- {changelog} -->

### 2026-11-18 (v0.1.0, 15:05 CET, github repository preparation)

- renamed the public documentation to `README.md` and the upstream license file to `LICENSE`, preserving the license contents and updating its reference
- added `.gitignore` rules for os metadata, local editor files, logs, and environment secrets while allowing environment examples
- configured origin as `git@github.com:heikopanjas/pi-themes.git` and documented the repository purpose, layout, and tooling in `AGENTS.md`
- rationale: use github's standard entry points and keep local artifacts and secrets out of future commits without changing the themes
- version bump: none (documentation and repository configuration only; no theme code changed and no version manifest exists)

### 2026-11-18 (v0.1.0, commit message constraints)

- limited commit messages to 500 characters total and plain text without quoting or special characters beyond required conventional commits punctuation
- rationale: preserve the user's explicit commit requirements alongside the existing subject and body line limits
- version bump: none (instruction-only update; no code changed)

### 2025-10-05 (v0.1.0, initial setup)

- initial AGENTS.md setup
- established core coding standards and conventions
- defined repository structure and governance principles
