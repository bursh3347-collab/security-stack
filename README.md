# 🔒 security-stack

> ⭐ Maturity: **L1 Growing** — 7 projects analyzed, comparison complete, best practices started.

Extracted best practices, architecture patterns, and deep analysis from 7 high-star security tools on GitHub.

## 📈 本分类飙升榜（最近更新：2026-04-15）

| 排名 | 项目 | 总Stars | 周增 | 趋势 |
|------|------|---------|------|------|
| 1 | OWASP ZAP | 37k | +100 | → |
| 2 | Vault | 32k | +80 | → |
| 3 | Trivy | 25k | +200 | ↑ |
| 4 | Nuclei | 23k | +300 | 🚀 |
| 5 | Semgrep | 14.8k | +150 | ↑ |
| 6 | Falco | 7.8k | +30 | → |
| 7 | Snyk | N/A | N/A | → |

> 🌟 Nuclei 增速最快（模板生态爆发），Trivy 和 Semgrep 稳步增长。Shadow AI 安全领域正在催生新一波工具。

## 📋 What's Inside

### Projects Analyzed (7)
| Project | Stars | TEMC | Language | Category |
|---------|-------|------|----------|----------|
| [Semgrep](projects/semgrep.md) | 14.8k | **84** | OCaml | SAST |
| [Trivy](projects/trivy.md) | ~25k | **81** | Go | Vulnerability Scanner |
| [Nuclei](projects/nuclei.md) | ~23k | **79** | Go | Template Scanner |
| [Snyk](projects/snyk.md) | N/A | **79** | N/A | Dev Security Platform |
| [OWASP ZAP](projects/owasp-zap.md) | ~37k | **73** | Java | DAST |
| [Vault](projects/vault.md) | ~32k | **71** | Go | Secrets Management |
| [Falco](projects/falco.md) | ~7.8k | **60** | C++ | Runtime Security |

### Comparison & Best Practices
- [📊 Security Tools Comparison](comparison.md) — Category matrix + feature comparison
- [🔐 Secure Coding](best-practices/secure-coding.md) — TypeScript security patterns
- [📦 Dependency Security](best-practices/dependency-security.md) — Supply chain protection
- [🗺️ Technology Roadmap](roadmap.md) — Trends & predictions for security tools

## 🎯 Minimum Viable Security for Micro SaaS

Free, 30-minute setup:
1. **GitHub Dependabot** — Auto dependency updates (already built-in)
2. **Semgrep** — SAST scan in GitHub Actions CI
3. **`pnpm audit`** — Dependency vulnerability check in CI

## 🔗 Connection to Shadow AI Scanner

This repository directly supports天子's Shadow AI Security Scanner product development:
- **Semgrep**: Pattern-based rule writing approach
- **Nuclei**: YAML template architecture (similar to Medusa's 9,600 rules)
- **Trivy**: Multi-target scanning architecture reference
- **OWASP Top 10**: Security checklist methodology

## 🏗️ Repository Structure
```
security-stack/
├── README.md              ← You are here
├── projects/              ← Individual project analyses (TEMC scored)
├── best-practices/        ← Cross-project security patterns
├── code/                  ← Extractable code (coming soon)
├── comparison.md          ← Horizontal comparison tables
├── roadmap.md             ← Technology trends & predictions
├── CONTRIBUTING.md        ← How to contribute
└── SOURCES.md             ← All source links + licenses
```

## License
This repository contains analysis and extracted patterns. See [SOURCES.md](SOURCES.md).
