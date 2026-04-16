# Cosign

> Code signing and transparency for containers and binaries

| Metric | Data |
|--------|------|
| GitHub | [sigstore/cosign](https://github.com/sigstore/cosign) |
| Stars | 5,824 |
| License | Apache-2.0 |
| Language | Go |
| Last Updated | 2026-04-16 |
| Contributors | 200+ |
| Forks | 718 |
| Open Issues | 147 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Go, sigstore ecosystem, keyless signing via Fulcio/Rekor. SLSA provenance support |
| E (Ecosystem) | 72 | 5.8k stars, but part of larger sigstore project (Linux Foundation). Kubernetes policy integration |
| M (Market) | 78 | Software supply chain security post-SolarWinds. SLSA framework adoption growing. Executive orders mandate signing |
| C (Combo) | 60 | Advanced use case — relevant when publishing containers or packages. Not needed for basic SaaS deployment |
| **Overall** | **70** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Cosign signs, verifies, and stores container image signatures. Part of the sigstore ecosystem for software supply chain security:
- **Keyless signing** — sign with OIDC identity (GitHub, Google) instead of managing private keys
- **Transparency log** — all signatures recorded in Rekor (public ledger)
- **SLSA provenance** — attest build provenance for supply chain verification
- **Kubernetes integration** — policy controllers verify signatures before deployment
- **Blob signing** — sign any file, not just containers

## Usage

```bash
# Keyless sign a container image
cosign sign myregistry.io/myapp:latest

# Verify a signed image
cosign verify myregistry.io/myapp:latest

# Sign with GitHub Actions OIDC
# (automatic keyless signing in CI)

# Attach SBOM to image
cosign attach sbom --sbom sbom.json myregistry.io/myapp:latest

# Verify SLSA provenance
cosign verify-attestation myregistry.io/myapp:latest
```

## Architecture Highlights

- **Sigstore stack**: Cosign (signing) + Fulcio (certificate authority) + Rekor (transparency log)
- **Keyless flow**: OIDC token → Fulcio issues short-lived cert → sign with cert → record in Rekor
- **OCI native**: Signatures stored as OCI artifacts alongside container images
- **Policy engine**: Works with Kyverno, OPA/Gatekeeper for Kubernetes admission control

## Solo Dev Verdict

**🟡 FUTURE NEED** — Not critical today for a solo dev Micro SaaS. But as supply chain requirements tighten (SLSA, EU CRA), container signing will become mandatory. Learn the concept now, implement when publishing Docker images or open-source packages.

**When to implement**: When you publish Docker images to a public registry, or when customers ask about supply chain security.

## Risks & Counter-Arguments

- **Complexity**: Sigstore ecosystem has a learning curve (Fulcio, Rekor, OIDC)
- **Overkill**: For private images deployed to your own VPS, signing adds overhead without much benefit
- **Ecosystem maturity**: Keyless signing occasionally has reliability issues with Fulcio CA
- **vs Docker Content Trust**: Docker's built-in Notary is simpler but less featured
