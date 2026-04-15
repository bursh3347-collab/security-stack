# OWASP ZAP

> The world's most widely used web application security testing tool.

| Metric | Data |
|--------|------|
| GitHub | [zaproxy/zaproxy](https://github.com/zaproxy/zaproxy) |
| Stars | ~37,000 |
| Forks | ~8,000 |
| License | Apache-2.0 |
| Language | Java |
| Last Updated | 2026-04 (active) |
| Contributors | 300+ |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 82 | Comprehensive DAST, active/passive scanning, fuzzing, API testing |
| E Ecosystem | 85 | 37k stars, OWASP flagship, massive adoption, 150+ add-ons |
| M Market | 75 | Standard DAST tool, but DAST market shifting to API-first testing |
| C Combo | 55 | Java desktop app, useful for testing SaaS products but not directly composable |
| **Overall** | **73** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
OWASP ZAP is a free, open-source DAST (Dynamic Application Security Testing) tool. Point it at your web app, it automatically finds SQL injection, XSS, CSRF, and 100+ other vulnerability types.

## Architecture Highlights
- **Proxy-based**: Intercepts HTTP/HTTPS traffic
- **Active Scanner**: Automatically attacks target to find vulns
- **Passive Scanner**: Analyzes traffic without attacking
- **Spider**: Automatic site crawling
- **Fuzzer**: Input mutation testing
- **API**: REST API for CI integration

## Key Patterns
1. **Baseline Scan**: Quick passive scan in CI (5-10 min)
2. **Full Scan**: Active + passive scan (30-60 min)
3. **API Scan**: OpenAPI/GraphQL spec-based testing
4. **Auth Scan**: Test behind authentication

## Extractable Components
- ZAP Docker CI integration → code-base/security/dast/
- Security testing workflow → code-base/deploy/security-scanning/

## Why It Might NOT Be Worth It
- Java desktop app (heavy)
- Active scanning can be slow
- False positive management required
- Modern APIs need additional configuration
- Not TypeScript-native

## 天子点评
产品上线后的安全测试利器。DAST 领域无可替代。产品 MVP 完成后用 ZAP 做一次全扫描，成本为零。
