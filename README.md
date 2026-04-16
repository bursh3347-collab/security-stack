[English](README.md) | [中文](README_CN.md)

# 🔒 security-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/security-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/security-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/security-stack?style=flat-square)

> ⭐ Maturity: **L2 Growing** — 17 projects analyzed across 10 security categories, comparison complete, best practices expanding.

Extracted best practices, architecture patterns, and deep analysis from **17 high-star security tools** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📈 Trending Board (Updated: 2026-04-16)

| Rank | Project | Stars | Weekly Δ | Trend |
|------|---------|-------|----------|-------|
| 1 | OWASP ZAP | 37k | +100 | → |
| 2 | Vault | 32k | +80 | → |
| 3 | Trivy | 25k | +200 | ↑ |
| 4 | Nuclei | 23k | +300 | 🚀 |
| 5 | Semgrep | 14.8k | +150 | ↑ |
| 6 | Wazuh | 11.5k | +120 | ↑ |
| 7 | CrowdSec | 9.4k | +90 | ↑ |
| 8 | SonarQube | 9.4k | +60 | → |
| NEW | Checkov | 7.4k | +80 | 🌟 |
| NEW | ModSecurity | 8.2k | +40 | → |

> 🌟 Nuclei surging (template ecosystem explosion). Wazuh + CrowdSec gaining momentum in open-source SIEM/crowd-security space. Shadow AI security wave spawning new tools.

## 📋 What's Inside

### Projects Analyzed (17)

| Project | Stars | TEMC | Language | Category |
|---------|-------|------|----------|----------|
| [Semgrep](projects/semgrep.md) | 14.8k | **84** | OCaml | SAST |
| [Gitleaks](projects/gitleaks.md) | 26k | **82** | Go | Secret Scanner |
| [Trivy](projects/trivy.md) | ~25k | **81** | Go | Vulnerability Scanner |
| [Checkov](projects/checkov.md) | ~7.4k | **79** | Python | IaC Security |
| [Nuclei](projects/nuclei.md) | ~23k | **79** | Go | Template Scanner |
| [Snyk](projects/snyk.md) | N/A | **79** | N/A | Dev Security Platform |
| [SonarQube](projects/sonarqube.md) | ~9.4k | **78** | Java | SAST Platform |
| [Snyk CLI](projects/snyk-cli.md) | 5.5k | **77** | TypeScript | Multi-Scanner |
| [Wazuh](projects/wazuh.md) | ~11.5k | **77** | C/Python | SIEM / XDR |
| [Grype](projects/grype.md) | 12k | **76** | Go | Container Scanner |
| [CrowdSec](projects/crowdsec.md) | ~9.4k | **74** | Go | Crowd Security |
| [OWASP ZAP](projects/owasp-zap.md) | ~37k | **73** | Java | DAST |
| [Prowler](projects/prowler.md) | 13.6k | **72** | Python | Cloud Audit |
| [Vault](projects/vault.md) | ~32k | **71** | Go | Secrets Management |
| [Cosign](projects/cosign.md) | 5.8k | **70** | Go | Supply Chain |
| [ModSecurity](projects/modsecurity.md) | ~8.2k | **68** | C++ | WAF Engine |
| [Falco](projects/falco.md) | ~7.8k | **60** | C++ | Runtime Security |

### Category Coverage Map

| Category | Projects | Status |
|----------|----------|--------|
| 🔍 SAST | Semgrep, SonarQube | ✅ Strong |
| 🐛 Vulnerability Scanning | Trivy, Grype, Snyk | ✅ Strong |
| 🔑 Secret Detection | Gitleaks | ✅ |
| 🌐 DAST | OWASP ZAP, Nuclei | ✅ Strong |
| 🏗️ IaC Security | Checkov, Prowler | ✅ Strong |
| 🛡️ WAF / Runtime | ModSecurity, Falco, CrowdSec | ✅ Strong |
| 📊 SIEM / XDR | Wazuh | ✅ |
| 🔐 Secrets Management | Vault | ✅ |
| 📦 Supply Chain | Cosign | ✅ |
| 🔧 Multi-Scanner | Snyk CLI | ✅ |

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
4. **Checkov** — IaC policy scanning (if using Terraform/K8s)
5. **Gitleaks** — Pre-commit hook for secret detection

## 🔗 Connection to Shadow AI Scanner

This repository directly supports Shadow AI Security Scanner product development:
- **Semgrep**: Pattern-based rule writing approach
- **Nuclei**: YAML template architecture (similar to Medusa's 9,600 rules)
- **Trivy**: Multi-target scanning architecture reference
- **Checkov**: Policy-as-code + compliance mapping framework
- **SonarQube**: Quality Gate (pass/fail threshold) UX concept
- **ModSecurity**: Anomaly scoring model (accumulate risk across signals)
- **Wazuh**: Decode → Rule → Alert → Active Response pipeline
- **CrowdSec**: Crowd-sourced threat intel + bouncer enforcement model
- **OWASP Top 10**: Security checklist methodology

## 🏗️ Repository Structure

```
security-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← Individual project analyses (17 TEMC scored)
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

**Start with Semgrep + Dependabot + Gitleaks.** That covers 80% of your attack surface at zero cost. Add Trivy for container scanning when you Dockerize. Add Checkov when you use Terraform. Skip Vault until you have real secrets management needs — environment variables + Vercel encrypted secrets are fine for solo SaaS.

Nuclei is your secret weapon if you build a security product — its YAML template architecture is the gold standard for extensible scanning.

For **Shadow AI Scanner** product development, the key architectures to steal are:
1. **Checkov's policy-as-code** for rule management
2. **ModSecurity's anomaly scoring** for risk accumulation
3. **Wazuh's 4-stage pipeline** for detection flow
4. **CrowdSec's bouncer model** for enforcement decoupling

## License

This repository contains analysis and extracted patterns. See [SOURCES.md](SOURCES.md).
