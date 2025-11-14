---
title: .github - Shared Development Infrastructure
description: Common development infrastructure ensuring OSS quality through automation - Configuration as Truth
---

<!--
Document Metadata:
- Version: 1.0.0
- Created: 2025-11-08
- Author: atsushifx
- Last Updated: 2025-11-14

Changelog:
- 2025-11-14: Major simplification aligned with CLAUDE.md, detailed info delegated to CLAUDE.md
- 2025-11-08: Initial version

Copyright (c) 2025 atsushifx <https://github.com/atsushifx>
This software is released under the MIT License.
https://opensource.org/licenses/MIT
-->

English | [日本語](README.ja.md)

# 🛠 `.github` Shared Development Infrastructure

**Common Configuration Repository for All atsushifx Repositories**

This repository is a **shared configuration repository** leveraging GitHub's [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) feature.
It is **automatically referenced** by all repositories under atsushifx, providing Issue/PR templates, code of conduct, security policies, and more in a centralized manner.

> **Important**: This repository is not meant to be "used" directly, but rather "automatically referenced" by other repositories.

## 📖 Role of This Repository

### Automatically Provided to All Repositories

Through GitHub's community health files feature, the following files become **automatically available** to all repositories under atsushifx:

- 📋 **Issue Templates** - Templates for bug reports, feature requests, and topic discussions
- 📄 **Pull Request Template** - Checklist for PR creation
- 🤝 **Code of Conduct** - Community code of conduct (Japanese and English)
- 🔒 **Security Policy** - Vulnerability reporting procedures
- 💖 **Funding** - Sponsor link configuration

If a repository has a file with the same name, that file takes precedence.

### Exclusive to This Repository

The following are tools and configurations for **quality management of the `.github` repository itself**:

- ⚙️ **configs/** - Linter/formatter configurations for this repository
- 🔧 **dprint.jsonc, lefthook.yml** - Formatting and Git Hooks settings for this repository
- 📚 **CLAUDE.md** - AI assistant instructions for developing this repository

If you want to use these configurations in other repositories, please **copy and customize them individually** for each repository.

## 🌐 How Community Health Files Work

```
atsushifx/.github (this repository)
├── .github/
│   ├── ISSUE_TEMPLATE/        ← Available to all repositories
│   ├── PULL_REQUEST_TEMPLATE.md  ← Available to all repositories
│   ├── CODE_of_CONDUCT.md     ← Available to all repositories
│   └── SECURITY.md            ← Available to all repositories
└── configs/                   ← Exclusive to this repository

atsushifx/example-project
└── (no files)
    → Templates from .github repository are automatically applied

atsushifx/another-project
└── .github/
    └── ISSUE_TEMPLATE/        ← This takes precedence
```

### Conditions for Automatic Reference

1. Repository must be under the atsushifx user
2. The file must not exist in the individual repository
3. Applies to both public and private repositories

For details, see the [GitHub official documentation](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file).

## 🔧 Developing This Repository

If you need to edit or develop this repository itself, please refer to **[CLAUDE.md](./CLAUDE.md)**.

CLAUDE.md includes:

- Technical stack for this repository (dprint, lefthook, gitleaks, etc.)
- Explanation of configuration files under configs/
- Git Hooks setup instructions
- Commit conventions and formatting rules

## 📚 Related Documentation

- **[CLAUDE.md](./CLAUDE.md)** - Detailed developer guide
- **[CODE_OF_CONDUCT.md](.github/CODE_of_CONDUCT.md)** - Community code of conduct
- **[SECURITY.md](.github/SECURITY.md)** - Security policy

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
Copyright (c) 2025 atsushifx

## 🙏 Thanks

This repository was created and maintained with the support of AI agent assistants:

- 🤖 Elpha
- 🤖 Kobeni
- 🤖 Tsumugi
