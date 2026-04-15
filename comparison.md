# Security Tools Comparison

> Horizontal comparison of all security tools analyzed in this repository.
> Last updated: 2026-04-15

## Security Tool Category Matrix

| Tool | Category | Scan Type | Target |
|------|----------|-----------|--------|
| Semgrep | SAST | Static code analysis | Source code |
| Trivy | SCA + Scanner | Vulnerability scanning | Containers, FS, Git |
| OWASP ZAP | DAST | Dynamic testing | Running web apps |
| Nuclei | Vulnerability Scanner | Template-based scanning | URLs, hosts |
| Snyk | Developer Security | SCA + SAST + Container | Code, deps, containers |
| Vault | Secrets Management | N/A | Secrets, encryption |
| Falco | Runtime Security | Syscall monitoring | Containers, K8s |

## Feature Comparison

| Feature | Semgrep | Trivy | OWASP ZAP | Nuclei | Snyk |
|---------|---------|-------|-----------|--------|------|
| **Stars** | 14.8k | ~25k | ~37k | ~23k | N/A |
| **License** | LGPL-2.1 | Apache-2.0 | Apache-2.0 | MIT | Proprietary |
| **Language** | OCaml | Go | Java | Go | N/A |
| **SAST** | ✅ | ❌ | ❌ | ❌ | ✅ |
| **SCA (deps)** | ⚠️ Limited | ✅ | ❌ | ❌ | ✅ |
| **DAST** | ❌ | ❌ | ✅ | ✅ | ❌ |
| **Container Scan** | ❌ | ✅ | ❌ | ❌ | ✅ |
| **Secrets Detection** | ⚠️ Rules | ✅ | ❌ | ✅ | ❌ |
| **Custom Rules** | ✅ (patterns) | ⚠️ Policies | ⚠️ Scripts | ✅ (YAML) | ❌ |
| **CI Integration** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Free Tier** | ✅ Generous | ✅ Full | ✅ Full | ✅ Full | ⚠️ Limited |

## Recommended Security Stack for Micro SaaS

### Minimum Viable Security (Free, 30 min setup)
1. **GitHub Dependabot** — Auto dependency updates (built-in)
2. **Semgrep** — SAST in CI (GitHub Action, 2 min)
3. **Trivy** — Dependency CVE scan in CI (if using Docker)

### Enhanced Security (Free, 1-2 hours)
4. **OWASP ZAP Baseline** — Quick DAST scan in CI
5. **Nuclei** — Template-based vulnerability scanning
6. **GitHub Secret Scanning** — Built-in credential detection

### Enterprise-Grade (Paid)
7. **Snyk** — Full developer security platform
8. **Vault** — Centralized secrets management
9. **Falco** — Runtime security (if using K8s)

## TEMC Score Ranking

| Rank | Project | Overall | T | E | M | C |
|------|---------|---------|---|---|---|---|
| 1 | **Semgrep** | **84** | 90 | 82 | 85 | 80 |
| 2 | **Trivy** | **81** | 90 | 85 | 82 | 70 |
| 3 | **Nuclei** | **79** | 88 | 82 | 78 | 72 |
| 4 | **Snyk** | **79** | 85 | 88 | 82 | 65 |
| 5 | **OWASP ZAP** | **73** | 82 | 85 | 75 | 55 |
| 6 | **Vault** | **71** | 92 | 85 | 72 | 40 |
| 7 | **Falco** | **60** | 88 | 75 | 65 | 25 |

## Connection to Shadow AI Scanner

Several tools in this stack are directly relevant to天子's Shadow AI Security Scanner product:
- **Semgrep**: Pattern-based scanning approach applicable to AI security rules
- **Nuclei**: YAML template system similar to Medusa's 9,600 YAML rules
- **Trivy**: Multi-target scanning architecture as reference
- **OWASP ZAP**: DAST methodology applicable to AI API testing
