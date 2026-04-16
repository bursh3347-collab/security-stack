# Grype

> A vulnerability scanner for container images and filesystems

| Metric | Data |
|--------|------|
| GitHub | [anchore/grype](https://github.com/anchore/grype) |
| Stars | 12,032 |
| License | Apache-2.0 |
| Language | Go |
| Last Updated | 2026-04-16 |
| Contributors | 100+ |
| Forks | 781 |
| Open Issues | 390 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 88 | Go, uses Syft for SBOM generation. Scans containers, directories, SBOMs. CycloneDX/SPDX support |
| E (Ecosystem) | 75 | 12k stars, backed by Anchore (enterprise container security). Growing adoption in CI pipelines |
| M (Market) | 82 | Supply chain security is top priority post-SolarWinds/Log4Shell. Container scanning mandatory for regulated industries |
| C (Combo) | 72 | Useful if shipping Docker containers. Pairs with Trivy for defense-in-depth. Direct CI integration |
| **Overall** | **76** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Grype finds known vulnerabilities in container images and filesystems by matching packages against vulnerability databases:
- **Multi-source scanning** — container images, directories, SBOMs, archives
- **Multiple DB sources** — NVD, GitHub Advisories, Alpine/Debian/RHEL/Ubuntu advisories
- **SBOM-native** — scan CycloneDX or SPDX SBOMs directly
- **VEX support** — OpenVEX for vulnerability exception management
- **Fast** — Go binary, parallel scanning

## Usage

```bash
# Scan a container image
grype alpine:latest

# Scan a directory
grype dir:./my-project

# Scan with severity filter
grype alpine:latest --only-fixed --fail-on high

# Output as JSON for CI
grype alpine:latest -o json

# Generate SBOM first, then scan
syft alpine:latest -o cyclonedx-json | grype
```

## Architecture Highlights

- **Syft integration**: Uses Syft (also by Anchore) for SBOM generation
- **Vulnerability DB**: Auto-updated local database from multiple advisory sources
- **Matcher system**: Package-type-specific matchers (apk, dpkg, rpm, npm, pip, go, java, etc.)
- **SBOM formats**: CycloneDX, SPDX, Syft native
- **Output**: Table, JSON, CycloneDX, SARIF

## Solo Dev Verdict

**🟡 USE IF SHIPPING CONTAINERS** — If you deploy via Docker (Coolify, Kamal, self-hosted), add Grype to CI. If you're on Vercel (serverless), the platform handles container security.

```yaml
# GitHub Actions
- uses: anchore/scan-action@v4
  with:
    image: myapp:latest
    fail-build: true
    severity-cutoff: high
```

**vs Trivy**: Grype focuses purely on vulnerability matching; Trivy is broader (secrets, IaC, licenses). Use both for defense-in-depth, or Trivy alone for simplicity.

## Risks & Counter-Arguments

- **vs Trivy**: Trivy is more popular (25k vs 12k stars) and broader in scope
- **Database lag**: Vulnerability DB updates may lag behind NVD by hours
- **False positives**: Package detection in compiled binaries can be imprecise
- **Anchore lock-in**: Enterprise features push toward Anchore commercial platform
