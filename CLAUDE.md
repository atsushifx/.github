# CLAUDE.md

## Project Philosophy

This repository provides shared development infrastructure for OSS projects.
It enforces consistency through automation rather than documentation.

**Core Principles:**

1. Configuration as Truth - All rules live in config files, not documentation
2. Automate Everything - Linters, formatters, and hooks prevent issues before commit
3. AI-Powered Workflow - Commit messages and documentation are AI-generated
4. Zero Manual Checks - CI/CD catches what local hooks miss

**Working with AI:**

- Trust automated tools over manual inspection
- Rely on pre-commit hooks to enforce standards
- Use AI-generated commit messages (scripts/prepare-commit-msg.sh)
- Let linters define code style, not personal preference

**Non-Negotiable Rules:**

- Never bypass pre-commit hooks (--no-verify)
- Never commit secrets (gitleaks will block)
- Never manually format code (dprint handles it)
- Always follow Conventional Commits format

---

## Technical Context

### Tech Stack

- Git Hooks: lefthook
- Secret Scanning: gitleaks, secretlint
- Commit Validation: commitlint
- Code Formatting: dprint
- Markdown Linting: markdownlint-cli2
- Japanese Text: textlint
- Spell Checking: cspell

### Project Structure

```bash
configs/              # All linter/formatter configurations
scripts/              # Automation scripts (commit message generation)
.github/workflows/    # CI/CD workflows
.github/ISSUE_TEMPLATE/  # Issue templates
.github/PULL_REQUEST_TEMPLATE/  # PR templates
```

### Essential Commands

```bash
# Setup
lefthook install                    # Install git hooks

# Development
dprint fmt                          # Format all code
lefthook run pre-commit            # Run hooks manually

# Commit
git add . && git commit            # Auto-generates message via AI
```

### Commit Types

Standard:

- `feat` - New features
- `fix` - Bug fixes
- `chore` - Maintenance tasks
- `docs` - Documentation
- `test` - Tests
- `refactor` - Code restructuring
- `perf` - Performance improvements
- `ci` - CI/CD changes

Custom:

- `config` - Configuration changes
- `release` - Release commits
- `merge` - Merge commits
- `build` - Build system changes
- `style` - Code style changes
- `deps` - Dependency updates

## Configuration Reference

### Linting & Formatting

Code formatting:

- dprint: `dprint.jsonc`,
- \<Editor>: `.editorconfig`

Markdown linting:

- markdownlint-cli2: `configs/.markdownlint.yaml`

Japanese text linting:

- textlint: `configs/textlintrc.yaml`

Spell checking:

- cspell: `.vscode/cspell.json`

### Git Workflow

Hooks management:

- lefthook: `lefthook.yml`

Commit validation:

- commitlint: `configs/commitlint.config.js`

Secret scanning:

- gitleaks: `configs/gitleaks.toml`
- secretlint: `configs/secretlint.config.yaml`

### CI/CD

Secret scanning:

- gitleaks: `.github/workflows/ci-secrets-scan.yml`, `configs/gitleaks.toml`

### External Dependencies

Spell checking:

- cspell: `${XDG_CONFIG_HOME}/vscode/cspell.config.json`

Commit message generation:

- prepare-commit-msg.sh:
- commit-message-generator: `~/.claude/plugins/`
