---
header:
  - src: README.md
  - @(#): .github Shared Development Infrastructure
title: .github - Shared Development Infrastructure
description: Common development infrastructure ensuring OSS quality through automation - Configuration as Truth
version: 1.0.0
created: 2025-11-08
authors:
  - atsushifx
changes:
  - 2025-11-08: Initial version
copyright:
  - Copyright (c) 2025 atsushifx <https://github.com/atsushifx>
  - This software is released under the MIT License.
  - https://opensource.org/licenses/MIT
---

English | [日本語](README.ja.md)

## 🛠 `.github` Shared Development Infrastructure

## OSS Quality Assurance Through Automation - Enforce Quality via Configuration, Not Documentation

<!-- textlint-disable ja-technical-writing/max-comma -->

This repository provides shared development infrastructure actively used in OSS projects.
Leveraging GitHub's community health files feature, it functions as user-level default templates
automatically referenced across all repositories.
It ensures quality through automation rather than manual checks.
Key features include Issue/PR templates, auto-formatting, linting, security scanning, and Git Hooks.

<!-- textlint-enable -->

## 📖 Purpose of This Repository

### Problems Solved

- Inconsistent code style
- Varying quality of commit messages
- Security risks (accidental commits of secrets)
- Increased review burden
- Documentation maintenance overhead

### Approach

1. **Configuration as Truth** - Rules live in config files, no documentation needed
2. **Automate Everything** - Formatters, linters, and hooks prevent issues before they occur
3. **AI-Powered Workflow** - Commit messages and documentation are AI-generated
4. **Zero Manual Checks** - Two-layer defense with local hooks and CI/CD

## 🏗 Repository Structure

### Directory Structure

```bash
.
├── .github/                    # GitHub community health files
│   ├── workflows/              # CI/CD workflows
│   │   ├── ci-secrets-scan.yml
│   │   └── codeql-actions-only.yml
│   ├── ISSUE_TEMPLATE/         # Issue templates (YML format)
│   │   ├── bug_report.yml
│   │   ├── feature_request.yml
│   │   ├── open_topic.yml
│   │   └── config.yml
│   ├── PULL_REQUEST_TEMPLATE.md
│   ├── CODE_of_CONDUCT.md
│   ├── CODE_of_CONDUCT.ja.md
│   ├── SECURITY.md
│   └── FUNDING.yml
├── configs/                    # All linter/formatter configurations
│   ├── commitlint.config.js
│   ├── gitleaks.toml
│   ├── secretlint.config.yaml
│   ├── .markdownlint.yaml
│   ├── textlintrc.yaml
│   └── .textlint/
├── scripts/                    # Automation scripts
│   └── prepare-commit-msg.sh
├── .vscode/                    # VS Code settings
│   └── cspell.json
├── .serena/memories/           # AI assistant knowledge base
├── dprint.jsonc               # Code formatting config
├── lefthook.yml               # Git hooks management
├── .editorconfig              # Editor settings
├── LICENSE / LICENSE.ja       # Repository licenses
├── README.md / README.ja.md   # Repository documentation
└── CLAUDE.md                  # AI assistant instructions
```

### Core Features

| Category       | Feature                      | What's Provided                             |
| -------------- | ---------------------------- | ------------------------------------------- |
| **Templates**  | Issue/PR                     | Bug reports, feature requests, PR checklist |
| **Formatting** | dprint                       | Auto-formatting for Markdown/JSON/YAML/TOML |
| **Lint**       | markdownlint/textlint/cspell | Document quality checks, spell checking     |
| **Security**   | gitleaks/secretlint          | Secret detection, commit blocking           |
| **Git Hooks**  | lefthook                     | Pre-commit automated checks                 |
| **Commit**     | commitlint                   | Conventional Commits enforcement            |
| **CI/CD**      | GitHub Actions               | Secret scanning, CodeQL                     |

### Configuration Files

| Category       | Tool               | Config File                                 |
| -------------- | ------------------ | ------------------------------------------- |
| **Formatting** | dprint             | `dprint.jsonc`                              |
|                | EditorConfig       | `.editorconfig`                             |
| **Lint**       | markdownlint       | `configs/.markdownlint.yaml`                |
|                | textlint           | `configs/textlintrc.yaml`                   |
|                | cspell             | `.vscode/cspell.json`                       |
| **Git Hooks**  | lefthook           | `lefthook.yml`                              |
| **Commit**     | commitlint         | `configs/commitlint.config.js`              |
|                | prepare-commit-msg | `scripts/prepare-commit-msg.sh`             |
| **Security**   | gitleaks           | `configs/gitleaks.toml`                     |
|                | secretlint         | `configs/secretlint.config.yaml`            |
| **CI/CD**      | Secret scan        | `.github/workflows/ci-secrets-scan.yml`     |
|                | CodeQL             | `.github/workflows/codeql-actions-only.yml` |

## 🚀 How to Use

### 1. Setup

```bash
# Place this repository in your project's .github/ directory
git clone https://github.com/atsushifx/.github.git

# Install Git Hooks
lefthook install

# Verify formatting configuration
dprint fmt
```

### 2. Daily Usage

```bash
# Write code → dprint auto-formats
# (.editorconfig applied on save)

# Commit → Hooks auto-check
git commit
# - gitleaks detects secrets
# - markdownlint/textlint check documents
# - commitlint validates messages
# - AI-generated messages prepared

# Push → CI performs final checks
git push
```

### 3. Using Templates

- Issue Creation: Template selection automatically available in repository's Issues tab
  - Bug Report (`bug_report.md`)
  - Feature Request (`feature_request.md`)
  - General Topic (`topic.md`)

- PR Creation: Checklist template automatically applied when opening a PR

## 📋 Important Usage Rules

### Prohibited Actions

- Don't bypass hooks with `--no-verify`
- Don't commit secrets (gitleaks will block)
- Don't manually format code (leave it to dprint)
- Follow Conventional Commits format

### Commit Types

**Standard Types:**

- `feat`: New features
- `fix`: Bug fixes
- `docs`: Documentation
- `chore`: Maintenance tasks
- `test`: Tests
- `refactor`: Refactoring
- `perf`: Performance improvements
- `ci`: CI/CD changes

**Custom Types:**

- `config`: Configuration changes
- `release`: Releases
- `merge`: Merges
- `build`: Build system
- `style`: Style changes
- `deps`: Dependency updates

## 🌐 Community Health Files

This repository leverages GitHub's [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) feature:

- Files in the `.github/` directory are automatically referenced across all repositories
- Repository-specific files take precedence when they exist
- Centralized management of Issue/PR templates, code of conduct, and security policies

### Available Files

- Issue Templates (`ISSUE_TEMPLATE/*.yml`) - Bug reports, feature requests, topic discussions
- Pull Request Template (`PULL_REQUEST_TEMPLATE.md`) - PR checklist
- Code of Conduct (`CODE_of_CONDUCT.md`, `CODE_of_CONDUCT.ja.md`) - Community code of conduct
- Security Policy (`SECURITY.md`) - Vulnerability reporting procedures
- Funding (`FUNDING.yml`) - Sponsor link configuration

### Community Guidelines

- [Code of Conduct](.github/CODE_of_CONDUCT.md) - Community code of conduct
- [Security Policy](.github/SECURITY.md) - Vulnerability reporting procedures

## 📚 Detailed Information

For technical details and AI development guide, refer to [`CLAUDE.md`](./CLAUDE.md).

## 📄 License

- **License**: MIT License
- **Copyright**: Copyright (c) 2025 atsushifx
- **Owner**: atsushifx

MIT © Atsushi Furukawa (@atsushifx)

## 🙏 Thanks

This repository was created and maintained with the support of AI agent assistants:

- 🤖 Elpha
- 🤖 Kobeni
- 🤖 Tsumugi
