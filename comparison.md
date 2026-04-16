# Security Tools Comparison

> Horizontal comparison of all security tools analyzed in this repository.
> Last updated: 2026-04-16

## Security Tool Category Matrix

| Tool | Category | Scan Type | Target | License |
|------|----------|-----------|--------|--------|
| Semgrep | SAST | Static code analysis | Source code | LGPL-2.1 |
| Trivy | SCA + Scanner | Vulnerability scanning | Containers, FS, Git | Apache-2.0 |
| OWASP ZAP | DAST | Dynamic testing | Running web apps | Apache-2.0 |
| Nuclei | Vuln Scanner | Template-based scanning | URLs, hosts | MIT |
| Snyk CLI | Multi-Scanner | SCA+SAST+Container+IaC | Everything | Apache-2.0 |
| Gitleaks | Secret Scanner | Pattern + entropy | Git repos, files | MIT |
| Vault | Secrets Mgmt | N/A | Secrets, encryption | BUSL-1.1 ⚠️ |
| Falco | Runtime | Syscall monitoring | Containers, K8s | Apache-2.0 |
| Prowler | Cloud Audit | Compliance checks | AWS/Azure/GCP/K8s | Apache-2.0 |
| Grype | SCA | Vulnerability matching | Containers, FS, SBOMs | Apache-2.0 |
| Cosign | Supply Chain | Signing/verification | Container images | Apache-2.0 |

## Feature Comparison (Expanded)

| Feature | Semgrep | Trivy | Gitleaks | Snyk CLI | Grype | Prowler |
|---------|---------|-------|----------|----------|-------|--------|
| **Stars** | 14.8k | ~25k | 26k | 5.5k | 12k | 14k |
| **Language** | OCaml | Go | Go | TypeScript | Go | Python |
| **SAST** | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ |
| **SCA (deps)** | ⚠️ | ✅ | ❌ | ✅ | ✅ | ❌ |
| **Container Scan** | ❌ | ✅ | ❌ | ✅ | ✅ | ❌ |
| **Secret Detection** | ⚠️ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Cloud Audit** | ❌ | ❌ | ❌ | ⚠️ IaC | ❌ | ✅ |
| **SBOM** | ❌ | ✅ | ❌ | ❌ | ✅ | ❌ |
| **Custom Rules** | ✅ | ⚠️ | ✅ TOML | ❌ | ❌ | ✅ |
| **CI Integration** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Free Tier** | ✅ | ✅ Full | ✅ Full | ⚠️ Limited | ✅ Full | ✅ Full |

## Supply Chain Security Comparison

| Feature | Cosign | Trivy | Grype | Snyk |
|---------|--------|-------|-------|------|
| **Image Signing** | ✅ | ❌ | ❌ | ❌ |
| **SBOM Generation** | ❌ (Syft) | ✅ | ❌ (Syft) | ❌ |
| **SBOM Scanning** | ❌ | ✅ | ✅ | ✅ |
| **SLSA Provenance** | ✅ | ❌ | ❌ | ❌ |
| **VEX Support** | ❌ | ✅ | ✅ | ❌ |
| **Keyless Signing** | ✅ | N/A | N/A | N/A |

## Recommended Security Stack for Micro SaaS

### Minimum Viable Security (Free, 30 min setup)
1. **Gitleaks** — Secret scanning in CI (GitHub Action, 2 min) 🟢
2. **Semgrep** — SAST in CI (GitHub Action, 2 min) 🟢
3. **Snyk CLI** — Dependency CVE scan (`snyk test`, 5 min) 🟢
4. **GitHub Dependabot** — Auto dependency updates (built-in) 🟢

### Enhanced Security (Free, 1-2 hours)
5. **Trivy** — Container + filesystem scanning 🟡
6. **Grype** — Defense-in-depth container scanning 🟡
7. **Nuclei** — Template-based vulnerability scanning 🟡
8. **OWASP ZAP Baseline** — Quick DAST scan in CI 🟡

### Enterprise-Grade (When scaling)
9. **Prowler** — Cloud compliance audits (SOC2/HIPAA) 🟡
10. **Cosign** — Container image signing (supply chain) 🟡
11. **Vault** — Centralized secrets management 🔴
12. **Falco** — Runtime security (if using K8s) 🔴

## TEMC Score Ranking (All 12 Projects)

| Rank | Project | Overall | T | E | M | C | Solo Dev |
|------|---------|---------|---|---|---|---|----------|
| 1 | **Semgrep** | **84** | 90 | 82 | 85 | 80 | 🟢 Must |
| 2 | **Gitleaks** | **82** | 85 | 82 | 88 | 88 | 🟢 Must |
| 3 | **Trivy** | **81** | 90 | 85 | 82 | 70 | 🟢 Use |
| 4 | **Nuclei** | **79** | 88 | 82 | 78 | 72 | 🟡 Use |
| 5 | **Snyk CLI** | **77** | 80 | 85 | 85 | 75 | 🟢 Use |
| 6 | **Grype** | **76** | 88 | 75 | 82 | 72 | 🟡 Use |
| 7 | **OWASP ZAP** | **73** | 82 | 85 | 75 | 55 | 🟡 Use |
| 8 | **Prowler** | **72** | 82 | 78 | 80 | 65 | 🟡 Later |
| 9 | **Vault** | **71** | 92 | 85 | 72 | 40 | 🔴 Later |
| 10 | **Cosign** | **70** | 85 | 72 | 78 | 60 | 🟡 Later |
| 11 | **Snyk (Platform)** | **79** | 85 | 88 | 82 | 65 | 🟡 Use |
| 12 | **Falco** | **60** | 88 | 75 | 65 | 25 | 🔴 Skip |

## Connection to Shadow AI Scanner

Several tools in this stack are directly relevant to天子's Shadow AI Security Scanner product:
- **Semgrep**: Pattern-based scanning approach applicable to AI security rules
- **Nuclei**: YAML template system similar to Medusa's 9,600 YAML rules
- **Trivy/Grype**: Multi-target scanning architecture as reference
- **Gitleaks**: Secret detection patterns applicable to AI API key leakage
- **Snyk CLI**: Developer-first UX model — exactly the experience天子should build
- **Cosign**: Supply chain signing pattern applicable to AI model provenance
- **Prowler**: Compliance check architecture applicable to AI governance audits
