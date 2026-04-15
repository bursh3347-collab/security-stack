# Trivy

> Comprehensive vulnerability scanner for containers, filesystems, Git repos, and Kubernetes.

| Metric | Data |
|--------|------|
| GitHub | [aquasecurity/trivy](https://github.com/aquasecurity/trivy) |
| Stars | ~25,000 |
| Forks | ~2,500 |
| License | Apache-2.0 |
| Language | Go |
| Last Updated | 2026-04 (very active) |
| Contributors | 500+ |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 90 | Multi-target (container/fs/git/k8s), CVE + misconfig + secrets + license scanning |
| E Ecosystem | 85 | 25k stars, CNCF, GitHub Actions integration, Docker Hub integration |
| M Market | 82 | Default scanner for many CI pipelines, replaces multiple tools |
| C Combo | 70 | Container scanning useful for Docker builds, but天子 uses Vercel (less container focus) |
| **Overall** | **81** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Trivy is the Swiss Army knife of vulnerability scanning. One tool scans containers, filesystems, Git repos, Kubernetes clusters for CVEs, misconfigurations, secrets, and license issues.

## Architecture Highlights
- **Multi-scanner**: CVE + misconfiguration + secrets + license
- **Multi-target**: Container images, filesystems, Git repos, K8s
- **Offline DB**: Vulnerability database cached locally
- **SBOM**: Generate and scan Software Bill of Materials
- **CI-native**: GitHub Actions, GitLab CI, Jenkins integration

## Key Modules
1. **Scanner Engine** (Large) — Core vulnerability detection
2. **Vulnerability DB** (Large) — CVE database (NVD, RedHat, etc.)
3. **Misconfig Scanner** (Medium) — IaC/K8s misconfiguration detection
4. **Secret Scanner** (Medium) — Credential/API key detection
5. **SBOM Generator** (Small) — CycloneDX/SPDX output

## Extractable Components
- CI scanning workflow → code-base/deploy/security-scanning/
- Dockerfile scanning patterns → code-base/deploy/docker/

⭐ Universal Code Candidate: CI vulnerability scanning workflow

## Why It Might NOT Be Worth It
- Container focus is less relevant for Vercel deployments
- Go codebase, not extensible for TypeScript developers
- Vulnerability DB can produce false positives
- Overhead for small projects

## 天子点评
多目标扫描架构是 Shadow AI Scanner 的参考模板。"一个工具扫所有" 的产品理念值得学习。Apache-2.0 协议友好。
