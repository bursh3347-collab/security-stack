# Semgrep

> Lightweight static analysis for 30+ languages — find bugs with patterns that look like source code.

| Metric | Data |
|--------|------|
| GitHub | [semgrep/semgrep](https://github.com/semgrep/semgrep) |
| Stars | 14,801 |
| Forks | 912 |
| License | LGPL-2.1 |
| Language | OCaml |
| Last Updated | 2026-04-15 |
| Contributors | 300+ |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 90 | Pattern-based SAST, 30+ languages, custom rules, fast scanning, Semgrep Pro |
| E Ecosystem | 82 | 15k stars, 2,000+ community rules, CI integration, Semgrep App platform |
| M Market | 85 | Leading open-source SAST, used by Dropbox/Slack/Figma, strong adoption |
| C Combo | 80 | TypeScript/Python supported, integrates with GitHub Actions, relevant to Shadow AI scanning |
| **Overall** | **84** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Semgrep lets you write security rules that look like the code they match. Pattern: `eval($X)` finds every eval call. No complex AST/regex required. Fast enough for CI.

## Architecture Highlights
- **Pattern-based matching**: Rules look like source code
- **30+ languages**: TypeScript, Python, Go, Java, Ruby, etc.
- **Semgrep Registry**: 2,000+ community rules
- **Semgrep Pro**: Cross-file analysis, secrets detection
- **CI Integration**: GitHub Actions, GitLab CI, pre-commit

## Key Modules
1. **Semgrep Core** (Large) — Pattern matching engine (OCaml)
2. **Rule Registry** (Large) — 2,000+ security rules
3. **Semgrep App** (Medium) — Cloud dashboard + policy management
4. **CI Integrations** (Small) — GitHub/GitLab/pre-commit hooks

## Extractable Components
- Custom Semgrep rules for AI/LLM security → code-base/security/semgrep-rules/
- CI integration patterns → code-base/deploy/security-scanning/

⭐ Universal Code Candidate: Semgrep CI integration pattern, custom rule templates

## Why It Might NOT Be Worth It
- LGPL-2.1 license (not as permissive as MIT/Apache)
- Core engine in OCaml (hard to extend)
- Pro features require paid plan
- False positive rate can be high without tuning
- Cross-file analysis only in paid Pro version

## 天子点评
Shadow AI Scanner 的规则引擎灵感来源。"代码即规则" 的思路非常适合天子产品。CI 集成模式可直接复用。
