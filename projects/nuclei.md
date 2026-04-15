# Nuclei

> Fast, template-based vulnerability scanner by ProjectDiscovery.

| Metric | Data |
|--------|------|
| GitHub | [projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) |
| Stars | ~23,000 |
| Forks | ~3,000 |
| License | MIT |
| Language | Go |
| Last Updated | 2026-04 (very active) |
| Templates | 9,000+ community templates |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 88 | Template-based, fast (Go), protocol support (HTTP/DNS/TCP/SSL), headless browser |
| E Ecosystem | 82 | 23k stars, 9k+ templates, active community, ProjectDiscovery platform |
| M Market | 78 | Popular in bug bounty/pentest community, growing enterprise adoption |
| C Combo | 72 | Template approach relevant to Shadow AI scanning (YAML rules like Medusa) |
| **Overall** | **79** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Nuclei uses YAML templates to define vulnerability checks. 9,000+ community templates cover CVEs, misconfigurations, exposed panels, and more. Extremely fast scanning.

## Architecture Highlights
- **YAML Templates**: Declarative vulnerability definitions
- **Multi-protocol**: HTTP, DNS, TCP, SSL, WebSocket, Code
- **Template Library**: 9,000+ community-maintained templates
- **Headless Browser**: JavaScript-rendered page testing
- **Workflows**: Chain multiple templates for complex checks

## Key Modules
1. **Scanning Engine** (Large) — Core Go scanning engine
2. **Template System** (Large) — YAML template parser + executor
3. **Protocol Handlers** (Medium) — HTTP/DNS/TCP/SSL handlers
4. **Reporting** (Small) — JSON/Markdown/SARIF output

## Extractable Components
- YAML security template pattern → code-base/security/nuclei-templates/
- Template-based scanning architecture → reference for Shadow AI scanner

⭐ Universal Code Candidate: Template-based vulnerability scanning pattern (relevant to天子 Shadow AI scanner)

## Why It Might NOT Be Worth It
- Go codebase, not TypeScript
- Bug bounty-focused, less enterprise polish
- Template quality varies widely
- Can trigger IDS/WAF alerts

## 天子点评
YAML 模板架构是天子 Shadow AI Scanner 的核心参考。9000+ 社区模板证明模板驱动扫描器有强大的生态飞轮。MIT 协议完美。
