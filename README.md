[English](README.md) | [中文](README_CN.md)

# 🔒 security-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/security-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/security-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/security-stack?style=flat-square)

> ⭐ Maturity: **L1 Growing** — 7 projects analyzed, comparison complete, best practices started.

Extracted best practices, architecture patterns, and deep analysis from **7 high-star security tools** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📈 Trending Board (Updated: 2026-04-15)

| Rank | Project | Stars | Weekly Δ | Trend |
|------|---------|-------|----------|-------|
| 1 | OWASP ZAP | 37k | +100 | → |
| 2 | Vault | 32k | +80 | → |
| 3 | Trivy | 25k | +200 | ↑ |
| 4 | Nuclei | 23k | +300 | 🚀 |
| 5 | Semgrep | 14.8k | +150 | ↑ |
| 6 | Falco | 7.8k | +30 | → |
| 7 | Snyk | N/A | N/A | → |

> 🌟 Nuclei is surging (template ecosystem explosion). Trivy and Semgrep growing steadily. The Shadow AI security wave is spawning a new generation of tools.

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

This repository directly supports Shadow AI Security Scanner product development:
- **Semgrep**: Pattern-based rule writing approach
- **Nuclei**: YAML template architecture (similar to Medusa's 9,600 rules)
- **Trivy**: Multi-target scanning architecture reference
- **OWASP Top 10**: Security checklist methodology

## 🏗️ Repository Structure

```
security-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← Individual project analyses (TEMC scored)
├── best-practices/        ← Cross-project security patterns
├── code/                  ← Extractable code (coming soon)
├── comparison.md          ← Horizontal comparison tables
├── roadmap.md             ← Technology trends & predictions
├── CONTRIBUTING.md        ← How to contribute
└── SOURCES.md             ← All source links + licenses
```

## <a id="temc-scoring"></a>📊 TEMC Scoring

**TEMC** = Technology × 0.25 + Ecosystem × 0.20 + Market × 0.30 + Combo × 0.25

- **T (Technology)**: Code quality, architecture, tech stack fit, docs
- **E (Ecosystem)**: Stars/forks, community activity, integrations, maintainer reputation
- **M (Market)**: Timing, competitive scarcity, trend alignment, commercializability
- **C (Combo)**: Stack compatibility, modularity, business combo potential, learning cost

## ⚔️ Solo Dev Verdict

**Start with Semgrep + Dependabot.** That alone covers 80% of your attack surface at zero cost. Add Trivy for container scanning when you Dockerize. Skip Vault until you have real secrets management needs — environment variables + Vercel encrypted secrets are fine for solo SaaS.

Nuclei is your secret weapon if you build a security product — its YAML template architecture is the gold standard for extensible scanning.

## License

This repository contains analysis and extracted patterns. See [SOURCES.md](SOURCES.md).
