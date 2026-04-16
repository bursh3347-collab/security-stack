# Gitleaks

> Find secrets with Gitleaks 🔑 — Git secret scanning and detection

| Metric | Data |
|--------|------|
| GitHub | [gitleaks/gitleaks](https://github.com/gitleaks/gitleaks) |
| Stars | 25,976 |
| License | MIT |
| Language | Go |
| Last Updated | 2026-04-16 |
| Contributors | 200+ |
| Forks | 1,991 |
| Open Issues | 358 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Go binary, regex + entropy-based detection, 150+ built-in rules. Fast scanning of entire git history |
| E (Ecosystem) | 82 | 26k stars, widely adopted in CI pipelines. GitHub Action available. Used by major companies |
| M (Market) | 88 | Secret leaks are #1 security incident cause. AI coding assistants increase leak risk (Shadow AI angle) |
| C (Combo) | 88 | Directly useful — add to GitHub Actions in 2 minutes. Prevents API keys from hitting production |
| **Overall** | **82** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Gitleaks scans git repositories for hardcoded secrets (API keys, passwords, tokens). It catches:
- **150+ secret patterns** — AWS keys, Stripe keys, JWT tokens, database URLs
- **Entire git history** — finds secrets in old commits, not just current code
- **Pre-commit hooks** — block secrets before they enter the repo
- **CI/CD integration** — fail pipelines on secret detection
- **AI-powered** — recent updates add LLM-based detection for non-pattern secrets

## Usage

```bash
# Scan current repo
gitleaks detect

# Scan with verbose output
gitleaks detect -v

# Pre-commit hook
gitleaks protect --staged

# GitHub Action
# .github/workflows/gitleaks.yml
# uses: gitleaks/gitleaks-action@v2
```

## Architecture Highlights

- **Detection engine**: Regex patterns + Shannon entropy analysis
- **Rule system**: TOML-based rules, easily extensible
- **Git integration**: Uses go-git for native git history traversal
- **Output formats**: JSON, SARIF, CSV for CI integration
- **Allowlisting**: Path-based, commit-based, regex-based ignore rules
- **New**: AI/LLM-powered detection for non-human-identifiable secrets

## Solo Dev Verdict

**🟢 MUST HAVE** — Add to your GitHub Actions right now. 2-minute setup prevents the #1 security incident for solo devs: accidentally pushing an API key to a public repo.

```yaml
# .github/workflows/gitleaks.yml
name: gitleaks
on: [push, pull_request]
jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: gitleaks/gitleaks-action@v2
```

**Shadow AI connection**: As AI coding assistants generate more code, they may embed API keys from training data. Gitleaks catches these automatically.

## Risks & Counter-Arguments

- **False positives**: High-entropy strings sometimes flagged incorrectly. Allowlist management needed
- **vs GitHub Secret Scanning**: GitHub's built-in scanning is free for public repos, but Gitleaks works everywhere and catches more patterns
- **Performance**: Full history scan on large repos can be slow (mitigate with `--since` flag)
- **Not a vault**: Catches leaks but doesn't manage secrets — pair with Vault/Doppler for management
