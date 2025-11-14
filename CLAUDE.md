# CLAUDE.md

## プロジェクト

共有開発インフラ - 自動化によるOSS品質保証

このリポジトリは、設定ファイルとCI/CDによって品質を強制するOSSプロジェクトの共有インフラです。
GitHubのcommunity health files機能により、全リポジトリから自動参照されます。

## コア原則

1. **Configuration as Truth** - ルールは設定ファイルに、ドキュメントではない
2. **Automate Everything** - 手動チェックゼロ、ツールが全て実施
3. **AI-Powered Workflow** - コミットメッセージ/PRは自動生成
4. **Zero Manual Checks** - ローカルフックで防ぎ、CIで検証

## 技術スタック

<!-- textlint-disable ja-technical-writing/max-comma -->

lefthook, dprint, gitleaks, secretlint, commitlint, markdownlint-cli2, textlint, cspell

<!-- textlint-enable -->

### ツール役割分担

- **フォーマット**: dprint が全ファイル処理
- **リント**: 各種専用ツールが言語別に検証
- **セキュリティ**: gitleaks + secretlint が二重防御
- **Git フック**: lefthook が全フック管理

### 設定ファイル一覧

| カテゴリ     | ツール       | 設定ファイル                     |
| ------------ | ------------ | -------------------------------- |
| フォーマット | dprint       | `dprint.jsonc`                   |
|              | EditorConfig | `.editorconfig`                  |
| リント       | markdownlint | `configs/.markdownlint.yaml`     |
|              | textlint     | `configs/textlintrc.yaml`        |
|              | cspell       | `.vscode/cspell.json`            |
| Git フック   | lefthook     | `lefthook.yml`                   |
| コミット     | commitlint   | `configs/commitlint.config.js`   |
| セキュリティ | gitleaks     | `configs/gitleaks.toml`          |
|              | secretlint   | `configs/secretlint.config.yaml` |

## 禁止事項

- ❌ フック回避 (`--no-verify`)
- ❌ シークレットコミット (gitleaksでブロック)
- ❌ 手動フォーマット (dprint に任せる)
- ❌ mainへの直接push
- ❌ configs/ディレクトリの不用意な変更

## 重要コマンド

### 初期セットアップ

```bash
lefthook install        # Git フックをインストール (初回必須)
```

### 日常的な開発

```bash
# フォーマット
dprint fmt              # 全ファイルフォーマット
dprint check            # フォーマットチェックのみ

# コミット
git add .               # 変更をステージング
git commit              # AI生成メッセージでコミット
git commit -m "type: description"  # 手動コミット (Conventional Commits形式)
```

### セキュリティスキャン

```bash
# ローカルスキャン
gitleaks protect --config ./configs/gitleaks.toml --staged
secretlint --secretlintrc ./configs/secretlint.config.yaml .
```

### 設定テスト

```bash
# commitlint設定テスト
echo "feat: test message" | commitlint --config ./configs/commitlint.config.js

# dprint設定テスト
dprint check --config ./dprint.jsonc

# 特定フックの手動実行
lefthook run pre-commit
```

## プロジェクト構造

```bash
.
├── .github/              # GitHub community health files
│    ├── workflows/       # CI/CD workflows
│    ├── ISSUE_TEMPLATE/  # Issue templates (YML format)
│    ├── PULL_REQUEST_TEMPLATE.md
│    ├── CODE_of_CONDUCT.md
│    └── SECURITY.md
├── configs/              # All linter/formatter configurations
├── scripts/              # Automation scripts
├── .vscode/              # VS Code settings
├── dprint.jsonc          # Code formatting config
├── lefthook.yml          # Git hooks management
└── .editorconfig         # Editor settings
```

## コーディング規約

### フォーマット基準 (dprint)

- **行幅**: 120文字
- **インデント**: 2スペース (タブ禁止)
- **改行**: LF (`\n`)
- **引用符**: シングルクォート推奨 (TypeScript/JavaScript)

詳細は、`dprint.jsonc`を参照

### Commit Types (Conventional Commits)

#### 標準タイプ

- `feat`: 新機能
- `fix`: バグ修正
- `chore`: メンテナンスタスク
- `docs`: ドキュメント
- `test`: テスト
- `refactor`: コード再構築
- `perf`: パフォーマンス改善
- `ci`: CI/CD変更

#### カスタムタイプ

- `config`: 設定変更
- `release`: リリースコミット
- `merge`: マージコミット
- `build`: ビルドシステム変更
- `style`: コードスタイル変更
- `deps`: 依存関係更新

## タスク完了チェックリスト

### コミット前

- [ ] `dprint fmt` でフォーマット実行
- [ ] `dprint check` でフォーマット検証
- [ ] markdownlint / textlint / cspell 実行 (該当ファイルがある場合)
- [ ] シークレットが含まれていないことを確認
- [ ] Conventional Commits形式でコミット

### 設定変更時

- [ ] 設定をテスト実行 (dry-runがあれば利用)
- [ ] ドキュメント更新 (必要に応じて)
- [ ] `lefthook run pre-commit` でフック動作確認

## AI協働ルール

1. **設定変更時**: configs/の変更は慎重に。必ずテスト実行
2. **コミット**: prepare-commit-msg.sh が自動生成。手動編集OK
3. **PR作成**: AI生成テンプレート使用。Summary/Test planは必須

## Community Health Files

このリポジトリはGitHubのcommunity health files機能を活用:

- `.github/`配下のファイルが全リポジトリから自動参照される
- 各リポジトリに同名ファイルがある場合、そちらが優先される
- Issue/PRテンプレート、行動規範、セキュリティポリシーなどを一元管理

**配置済み:**

- Issue Templates (`ISSUE_TEMPLATE/*.yml`)
- Pull Request Template (`PULL_REQUEST_TEMPLATE.md`)
- Code of Conduct (`CODE_of_CONDUCT.md`, `CODE_of_CONDUCT.ja.md`)
- Security Policy (`SECURITY.md`)
- Funding (`FUNDING.yml`)

## コミュニティガイドライン

- [行動規範](.github/CODE_of_CONDUCT.md) - Community code of conduct
- [セキュリティポリシー](.github/SECURITY.md) - Vulnerability reporting procedures

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
Copyright (c) 2025 atsushifx
