# HashiCorp Vault

> Secrets management, encryption as a service, and identity-based access for machines and humans.

| Metric | Data |
|--------|------|
| GitHub | [hashicorp/vault](https://github.com/hashicorp/vault) |
| Stars | ~32,000 |
| Forks | ~4,500 |
| License | BUSL-1.1 (⚠️ Changed from MPL-2.0) |
| Language | Go |
| Last Updated | 2026-04 (very active) |
| Contributors | 1,000+ |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 92 | Dynamic secrets, encryption as service, auto-rotation, PKI, transit engine |
| E Ecosystem | 85 | 32k stars, enterprise standard, massive integration ecosystem |
| M Market | 72 | Enterprise secrets tool, but cloud-native alternatives growing (AWS Secrets Manager) |
| C Combo | 40 | Overkill for solo developer, Vercel/Supabase handle secrets natively |
| **Overall** | **71** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Vault centralizes secret management for your entire infrastructure. Dynamic secrets (auto-generated, auto-rotated), encryption as a service, and identity-based access control.

## Architecture Highlights
- **Secret Engines**: KV, AWS, Database, PKI, Transit
- **Auth Methods**: OIDC, LDAP, AppRole, Kubernetes, GitHub
- **Dynamic Secrets**: Auto-generate + auto-revoke credentials
- **Encryption as a Service**: Transit engine for app-level encryption
- **Audit Logging**: Every access logged and auditable

⚠️ **License Warning**: Changed to BUSL-1.1. Consider OpenBao (Linux Foundation fork).

## Why It Might NOT Be Worth It
- BUSL-1.1 license concerns
- Massive complexity for solo developer
- Cloud providers have simpler alternatives (AWS Secrets Manager, Vercel env vars)
- Self-hosted Vault requires HA setup
- Overkill for .env file + Vercel secrets
