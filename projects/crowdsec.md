# CrowdSec

> Collaborative, open-source security engine — crowd-powered IP reputation & behavior detection.

| Metric | Data |
|--------|------|
| GitHub | [crowdsecurity/crowdsec](https://github.com/crowdsecurity/crowdsec) |
| Stars | ~9,400 |
| License | MIT |
| Language | Go |
| Last Updated | Active (daily commits) |
| Contributors | 100+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 72 | Clean Go codebase, modular parser/scenario/decision engine. LAPI + bouncer architecture. Solid but not groundbreaking engineering. |
| E Ecosystem | 70 | 9k+ Stars, active Discord, 50+ community bouncers (Nginx, Traefik, Cloudflare, pfSense). Growing but smaller than Fail2ban ecosystem. |
| M Market | 78 | Crowd-sourced threat intel is a hot category. Free tier + paid Console/CTI API. Strong timing with API-first security wave. Solo dev can deploy free tier instantly. |
| C Combo | 75 | Go binary = easy deploy on any VPS/Docker. REST API for integration. Bouncer model fits SaaS reverse proxy. Direct combo with Nginx/Traefik/Cloudflare stack. |
| **Composite** | **74** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Highlights

```
Log Sources → Parsers → Scenarios → Decisions → LAPI → Bouncers
                                                  ↓
                                          CrowdSec CTI
                                     (crowd-sourced blocklists)
```

**Key Design Decisions:**
- **Bouncer Architecture**: Decoupled detection (agent) from remediation (bouncers). Bouncers are language-agnostic plugins.
- **LAPI (Local API)**: Central decision hub. All agents report to LAPI, all bouncers query LAPI.
- **Crowd Intelligence**: Opt-in sharing of attack signals → community blocklist → 150M+ IPs curated.
- **Scenario DSL**: YAML-based behavior detection — similar to Nuclei's template approach but for runtime behavior.

## Core Modules

| Module | Size | Coupling | Purpose |
|--------|------|----------|---------|
| Agent (crowdsec binary) | Large | Medium | Log parsing + scenario evaluation |
| LAPI | Medium | Low | REST API for decisions |
| Bouncers | Small each | Low | Enforcement plugins (Nginx, iptables, Cloudflare) |
| Hub | Medium | Low | Centralized parsers/scenarios/collections repository |
| CTI API | N/A (SaaS) | Low | Crowd threat intel enrichment |

## Extractable Patterns

1. **Bouncer Plugin Architecture** → `code-base/security/bouncer-pattern/` — Decouple detection from enforcement. Any language can implement a bouncer via REST API.
2. **Scenario DSL** → `code-base/security/behavior-detection/` — YAML behavior rules with leaky-bucket rate limiting.
3. **Crowd Intelligence Model** → Relevant to Shadow AI Scanner — anonymous signal sharing for threat intel.

## Competitive Comparison

| | CrowdSec | Fail2ban | Cloudflare WAF |
|---|----------|----------|----------------|
| Language | Go | Python | N/A (SaaS) |
| Architecture | Agent + LAPI + Bouncer | Monolith | Cloud edge |
| Crowd Intel | ✅ 150M+ IPs | ❌ | ✅ (proprietary) |
| API | ✅ REST | ❌ | ✅ REST |
| Price | Free + paid CTI | Free | $20+/mo |
| Multi-server | ✅ native | ❌ manual | ✅ |
| Container | ✅ first-class Docker | ⚠️ workarounds | N/A |

## Solo Dev Verdict

**CrowdSec replaces Fail2ban for the modern stack.** If you run any public-facing server (VPS, Docker, K8s), CrowdSec gives you crowd-sourced IP blocking for free in 5 minutes. The bouncer architecture means zero application code changes. Skip the paid Console unless you have 10+ servers. The CTI API ($) is interesting for security products — could enrich Shadow AI Scanner with IP reputation data.

**⭐ Best Extract**: Bouncer plugin pattern (detection ≠ enforcement) is a reusable architecture for any security product.
