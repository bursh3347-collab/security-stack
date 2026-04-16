# SonarQube

> Continuous code quality and security analysis platform — the industry standard for SAST at scale.

| Metric | Data |
|--------|------|
| GitHub | [SonarSource/sonarqube](https://github.com/SonarSource/sonarqube) |
| Stars | ~9,400 |
| License | LGPL-3.0 |
| Language | Java |
| Last Updated | Active (daily commits) |
| Contributors | 250+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 88 | 30+ language support, 5,000+ rules, sophisticated taint analysis. Best-in-class SAST engine. Clean Quality Gate concept. |
| E Ecosystem | 82 | 400K+ organizations use SonarQube. Massive plugin ecosystem. IDE integration (SonarLint). Deep CI/CD integration. Industry standard. |
| M Market | 75 | Mature market leader — timing advantage gone. Free Community Edition still powerful. Enterprise $15K+/yr. Solo dev uses free SonarCloud. |
| C Combo | 70 | Java-heavy = poor fit for solo TypeScript dev. SonarCloud free tier is the play. Rules architecture inspires custom scanner design. |
| **Composite** | **78** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Highlights

```
Source Code → Scanner (language plugins) → Issue Detection
     ↓                                         ↓
Quality Profile (rules)              Compute Engine
     ↓                                         ↓
Quality Gate (pass/fail)  ←←←  Database + Web UI
```

**Key Design Decisions:**
- **Quality Gate**: Binary pass/fail threshold — "Is this code shippable?" Genius UX for CI/CD integration.
- **Quality Profile**: Grouped rule configurations per language. Profiles are inheritable and overridable.
- **Incremental Analysis**: Only scans changed code on PRs (SonarCloud). Full scan on main branch.
- **Language Plugin Architecture**: Each language is a separate plugin with its own parser, rules, and AST model.
- **OWASP/CWE Mapping**: Every security rule maps to OWASP Top 10 + CWE IDs — compliance-ready.

## Core Modules

| Module | Size | Coupling | Purpose |
|--------|------|----------|---------|
| Compute Engine | Large | High | Analysis processing + issue computation |
| Web Server | Large | High | UI + REST API + auth |
| Database | Medium | High | PostgreSQL for persistent state |
| Scanner | Medium | Low | Client-side code analysis agent |
| Language Plugins | Medium each | Low | Per-language parsing + rules |
| Quality Gate Engine | Small | Medium | Threshold evaluation |

## Extractable Patterns

1. **Quality Gate Concept** → `code-base/security/quality-gate/` — Binary pass/fail with configurable thresholds. Applicable to Shadow AI Scanner: "Does this codebase pass AI security audit?"
2. **Rule Taxonomy** → `code-base/security/rule-taxonomy/` — Bug / Vulnerability / Code Smell / Security Hotspot classification. Maps to OWASP + CWE.
3. **Incremental Analysis** → PR-only scanning pattern, relevant for CI/CD integration of any scanner.

## Competitive Comparison

| | SonarQube | Semgrep | CodeQL |
|---|-----------|---------|--------|
| Languages | 30+ | 30+ | 15+ |
| Rules | 5,000+ | 3,000+ (registry) | 2,000+ |
| Self-hosted | ✅ | ✅ | ❌ (GitHub only) |
| Free tier | Community Edition | OSS rules free | Free on public repos |
| Quality Gate | ✅ native | ❌ | ❌ |
| IDE plugin | SonarLint | ✅ | ❌ |
| Taint analysis | ✅ (Enterprise) | ✅ (Pro) | ✅ |
| AI security rules | Limited | Growing | Good |
| Solo dev cost | Free (CE) / $0 (Cloud) | Free | Free |

## Solo Dev Verdict

**Use SonarCloud (free for open source), not self-hosted SonarQube.** Self-hosting SonarQube requires Java + PostgreSQL — overkill for solo dev. SonarCloud gives you the same engine as a free SaaS for public repos.

For a solo TypeScript SaaS, **Semgrep is better** — lighter, faster, more AI-security rules, no Java dependency. But SonarQube's Quality Gate concept is worth stealing: build a binary "AI Security Score: PASS/FAIL" into any scanner product.

**⭐ Best Extract**: Quality Gate architecture (threshold-based pass/fail) + OWASP/CWE rule mapping methodology.
