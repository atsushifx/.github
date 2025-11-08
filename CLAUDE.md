# CLAUDE.md

## プロジェクト

共有開発インフラ - 自動化による OSS 品質保証:

This repository provides shared development infrastructure for OSS projects.
It enforces consistency through automation rather than documentation.
Serves as GitHub's community health files repository for user-level default templates.

## 技術スタック

<!-- textlint-disable ja-technical-writing/max-comma -->

lefthook, dprint, gitleaks, secretlint, commitlint, markdownlint-cli2, textlint, cspell

<!-- textlint-enable -->

## コア原則

1. **Configuration as Truth** - All rules live in config files, not documentation
2. **Automate Everything** - Linters, formatters, and hooks prevent issues before commit
3. **AI-Powered Workflow** - Commit messages and documentation are AI-generated
4. **Zero Manual Checks** - CI/CD catches what local hooks miss

## リポジトリ構造

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
└── CLAUDE.md                  # AI assistant instructions (this file)
```

## 禁止事項

- Never bypass pre-commit hooks (--no-verify)
- Never commit secrets (gitleaks will block)
- Never manually format code (dprint handles it)
- Always follow Conventional Commits format

## 重要コマンド

```bash
lefthook install        # Install git hooks
dprint fmt              # Format all code
git commit              # Commit with AI-generated message
```

## Commit Types

### Standard

- `feat`: New features
- `fix`: Bug fixes
- `chore`: Maintenance tasks
- `docs`: Documentation
- `test`: Tests
- `refactor`: Code restructuring
- `perf`: Performance improvements
- `ci`: CI/CD changes

### Custom

- `config`: Configuration changes
- `release`: Release commits
- `merge`: Merge commits
- `build`: Build system changes
- `style`: Code style changes
- `deps`: Dependency updates

## 設定ファイル

| Category       | Tool               | Config File                                 |
| -------------- | ------------------ | ------------------------------------------- |
| **Formatting** | dprint             | `dprint.jsonc`                              |
|                | EditorConfig       | `.editorconfig`                             |
| **Linting**    | markdownlint       | `configs/.markdownlint.yaml`                |
|                | textlint           | `configs/textlintrc.yaml`                   |
|                | cspell             | `.vscode/cspell.json`                       |
| **Git Hooks**  | lefthook           | `lefthook.yml`                              |
| **Commit**     | commitlint         | `configs/commitlint.config.js`              |
|                | prepare-commit-msg | `scripts/prepare-commit-msg.sh`             |
| **Security**   | gitleaks           | `configs/gitleaks.toml`                     |
|                | secretlint         | `configs/secretlint.config.yaml`            |
| **CI/CD**      | Secret scan        | `.github/workflows/ci-secrets-scan.yml`     |
|                | CodeQL             | `.github/workflows/codeql-actions-only.yml` |

## リポジトリ情報

- Owner: atsushifx
- License: MIT License
- Copyright: (c) 2025 atsushifx

## Community Health Files

このリポジトリは GitHub の community health files 機能を活用:

- `.github/` ディレクトリ配下のファイルが全リポジトリから自動参照される
- 各リポジトリに同名ファイルがある場合、そちらが優先される
- Issue/PR テンプレート、行動規範、セキュリティポリシーなどを一元管理

**配置済み:**

- Issue Templates (`ISSUE_TEMPLATE/*.yml`)
- Pull Request Template (`PULL_REQUEST_TEMPLATE.md`)
- Code of Conduct (`CODE_of_CONDUCT.md`, `CODE_of_CONDUCT.ja.md`)
- Security Policy (`SECURITY.md`)
- Funding (`FUNDING.yml`)

## コミュニティガイドライン

- [行動規範 (Code of Conduct)](.github/CODE_of_CONDUCT.md) - Community code of conduct
- [セキュリティポリシー (Security Policy)](.github/SECURITY.md) - Vulnerability reporting procedures

## 詳細ドキュメント (Serena Memories)

プロジェクトの詳細情報は `.serena/memories/` に格納されています。

- `project_overview.md` - プロジェクト詳細・目的・構成
- `tech_stack.md` - 技術スタック詳細・ツール統合フロー
- `code_style_and_conventions.md` - コーディング規約・命名規則
- `suggested_commands.md` - コマンドリファレンス・日常操作
- `task_completion_checklist.md` - タスク完了チェックリスト
- `windows_system_utilities.md` - Windows 固有のユーティリティ・コマンド
