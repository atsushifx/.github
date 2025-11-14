---
title: .github - 共有開発インフラ
description: OSS品質を自動化で保証する共通開発基盤 - Configuration as Truth
---

<!--
Document Metadata:
- Version: 1.0.0
- Created: 2025-11-08
- Author: atsushifx
- Last Updated: 2025-11-14

Changelog:
- 2025-11-14: CLAUDE.mdに合わせて大幅簡素化、詳細はCLAUDE.mdへ誘導
- 2025-11-08: 初版作成

Copyright (c) 2025 atsushifx <https://github.com/atsushifx>
This software is released under the MIT License.
https://opensource.org/licenses/MIT
-->

[English](README.md) | 日本語

# 🛠 `.github` 共有開発インフラ

**atsushifx 配下全リポジトリの共通設定リポジトリ**

このリポジトリは、GitHub の [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) 機能を活用した **共通設定リポジトリ** です。
atsushifx 配下の全リポジトリから **自動的に参照** され、Issue/PR テンプレート、行動規範、セキュリティポリシーなどを一元提供します。

> **重要**: このリポジトリは「使う」ものではなく、他のリポジトリが「自動的に参照する」ものです。

## 📖 このリポジトリの役割

### 全リポジトリに自動提供されるもの

GitHub の community health files 機能により、以下のファイルが atsushifx 配下の全リポジトリから **自動的に利用可能** になります：

- 📋 **Issue Templates** - バグ報告、機能要望、トピック投稿用テンプレート
- 📄 **Pull Request Template** - PR作成時のチェックリスト
- 🤝 **Code of Conduct** - コミュニティ行動規範（日本語・英語）
- 🔒 **Security Policy** - 脆弱性報告手順
- 💖 **Funding** - スポンサーリンク設定

各リポジトリに同名ファイルがある場合は、そちらが優先されます。

### このリポジトリ専用のもの

以下は `.github` リポジトリ **自体の品質管理** のためのツール・設定です：

- ⚙️ **configs/** - このリポジトリ用の linter/formatter 設定
- 🔧 **dprint.jsonc, lefthook.yml** - このリポジトリのフォーマット・Git Hooks設定
- 📚 **CLAUDE.md** - このリポジトリ開発用AIアシスタント指示書

他のリポジトリでこれらの設定を使う場合は、各リポジトリに **個別にコピー・カスタマイズ** してください。

## 🌐 Community Health Files の仕組み

```
atsushifx/.github (このリポジトリ)
├── .github/
│   ├── ISSUE_TEMPLATE/        ← 全リポジトリで利用可能
│   ├── PULL_REQUEST_TEMPLATE.md  ← 全リポジトリで利用可能
│   ├── CODE_of_CONDUCT.md     ← 全リポジトリで利用可能
│   └── SECURITY.md            ← 全リポジトリで利用可能
└── configs/                   ← このリポジトリ専用

atsushifx/example-project
└── (ファイルなし)
    → .github リポジトリのテンプレートが自動適用される

atsushifx/another-project
└── .github/
    └── ISSUE_TEMPLATE/        ← こちらが優先される
```

### 自動参照の条件

1. atsushifx ユーザー配下のリポジトリであること
2. 該当ファイルが各リポジトリに存在しないこと
3. パブリック/プライベート問わず適用される

詳細は [GitHub公式ドキュメント](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) を参照してください。

## 🔧 このリポジトリの開発

このリポジトリ自体を編集・開発する場合は、**[CLAUDE.md](./CLAUDE.md)** を参照してください。

CLAUDE.mdには以下が記載されています：

- このリポジトリの技術スタック（dprint, lefthook, gitleaks等）
- configs/配下の設定ファイルの説明
- Git Hooksのセットアップ方法
- コミット規約とフォーマットルール

## 📚 関連ドキュメント

- **[CLAUDE.md](./CLAUDE.md)** - 開発者向け詳細ガイド
- **[CODE_OF_CONDUCT.ja.md](.github/CODE_of_CONDUCT.ja.md)** - コミュニティ行動規範
- **[SECURITY.md](.github/SECURITY.md)** - セキュリティポリシー

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
Copyright (c) 2025 atsushifx

## 🙏 Thanks

本リポジトリは、下記の AI エージェントのサポートのもと作成・整備されました：

- 🤖 Elpha（エルファ）
- 🤖 Kobeni（小紅）
- 🤖 Tsumugi（つむぎ）
