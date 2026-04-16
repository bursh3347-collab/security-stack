# ModSecurity

> The world's most deployed open-source WAF (Web Application Firewall) engine.

| Metric | Data |
|--------|------|
| GitHub | [owasp-modsecurity/ModSecurity](https://github.com/owasp-modsecurity/ModSecurity) |
| Stars | ~8,200 |
| License | Apache-2.0 |
| Language | C++ |
| Last Updated | Active (monthly releases) |
| Contributors | 100+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 75 | libModSecurity v3 is a clean C++ library. SecRules DSL is powerful but complex. Performance-optimized for high-throughput. |
| E Ecosystem | 65 | OWASP CRS (Core Rule Set) is the crown jewel — 150+ rules maintained by OWASP. Nginx/Apache connectors. But community aging. |
| M Market | 68 | WAF market is mature and consolidated. Cloud WAFs (Cloudflare, AWS WAF) dominate. ModSecurity is the "free self-hosted" choice. Timing is neutral. |
| C Combo | 62 | C++ = no direct code extraction for TypeScript stack. Value is in rule patterns and WAF architecture concepts. CRS rules inspire AI security rule design. |
| **Composite** | **68** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Highlights

```
HTTP Request → Connector (Nginx/Apache) → libModSecurity
                                              ↓
                                    SecRules Engine
                                    (5 phases × N rules)
                                              ↓
                                    Action: ALLOW / DENY / LOG
```

**Key Design Decisions:**
- **libModSecurity (v3)**: Rewritten as standalone C++ library, decoupled from Apache. Any server can embed it via connectors.
- **5-Phase Processing**: REQUEST_HEADERS → REQUEST_BODY → RESPONSE_HEADERS → RESPONSE_BODY → LOGGING. Each phase runs applicable rules.
- **SecRules DSL**: `SecRule ARGS "@rx <script>" "id:1,deny,status:403"` — operator-based pattern matching with chaining.
- **Anomaly Scoring**: Instead of blocking on first match, accumulate score across rules. Block only when threshold exceeded. Reduces false positives.
- **OWASP CRS**: Community-maintained ruleset covering SQL injection, XSS, RFI, LFI, etc.

## Core Modules

| Module | Size | Coupling | Purpose |
|--------|------|----------|---------|
| libModSecurity | Large | Low (library) | Core WAF engine |
| SecRules Parser | Medium | Medium | Rule DSL parsing + evaluation |
| Nginx Connector | Small | Low | Nginx integration module |
| Apache Connector | Small | Low | Apache module |
| Audit Logger | Small | Low | Request/response logging |

## Extractable Patterns

1. **Anomaly Scoring Model** → `code-base/security/anomaly-scoring/` — Accumulate risk score across multiple signals before blocking. Directly applicable to Shadow AI Scanner: score AI tool usage risk across multiple dimensions.
2. **Multi-Phase Processing** → `code-base/security/pipeline-phases/` — Process requests in ordered phases, each phase has different data available.
3. **Rule DSL Design** → `code-base/security/rule-dsl/` — SecRules syntax inspires YAML rule design for any scanner.

## Competitive Comparison

| | ModSecurity | Cloudflare WAF | AWS WAF | Coraza |
|---|-------------|----------------|---------|--------|
| Type | Self-hosted | Cloud | Cloud | Self-hosted |
| Language | C++ | N/A | N/A | Go |
| Rules | OWASP CRS | Managed + custom | Managed + custom | OWASP CRS |
| Cost | Free | $20+/mo | $5/ACL + request | Free |
| Performance | Excellent | Excellent | Good | Good |
| Maintenance | Manual | Zero | Low | Manual |
| AI/LLM rules | ❌ | Growing | Growing | ❌ |

> **Note**: [Coraza](https://github.com/corazawaf/coraza) (7k+ ⭐) is the Go rewrite of ModSecurity — compatible with CRS rules, better for modern Go stacks.

## Solo Dev Verdict

**Skip ModSecurity. Use Cloudflare (free tier) or Vercel's built-in DDoS protection.** ModSecurity requires server-level configuration and C++ — completely wrong layer for a Vercel-deployed SaaS.

However, ModSecurity's **anomaly scoring model is gold** for any security product. Instead of binary block/allow, accumulate risk scores across signals. This pattern directly applies to Shadow AI Scanner: score each AI tool usage across multiple risk dimensions, alert when cumulative score exceeds threshold.

**⭐ Best Extract**: Anomaly scoring architecture + multi-phase processing pipeline concept.
