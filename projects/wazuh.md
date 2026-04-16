# Wazuh

> Open-source unified SIEM/XDR platform — endpoint detection, log analysis, compliance, and incident response.

| Metric | Data |
|--------|------|
| GitHub | [wazuh/wazuh](https://github.com/wazuh/wazuh) |
| Stars | ~11,500 |
| License | GPL-2.0 |
| Language | C, Python |
| Last Updated | Active (daily commits) |
| Contributors | 200+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 82 | Full SIEM/XDR stack: agent + manager + indexer + dashboard. Ruleset-driven detection. FIM, rootkit detection, vulnerability scanning. Production-grade at enterprise scale. |
| E Ecosystem | 78 | 11k+ Stars, 200+ contributors. Official integrations: AWS/Azure/GCP, Docker, K8s, Elastic/OpenSearch. Active community + commercial support. |
| M Market | 76 | Open-source SIEM is growing as Splunk prices rise. Wazuh is THE free alternative. But SIEM market is mature and enterprise-heavy. Solo dev rarely needs full SIEM. |
| C Combo | 72 | C/Python core = not directly reusable for TypeScript stack. Value is in detection rule architecture and alert correlation patterns. API-first design enables integration. |
| **Composite** | **77** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Highlights

```
Endpoints (Wazuh Agents)
     ↓ (encrypted)
Wazuh Manager (analysis engine)
     ↓
Wazuh Indexer (OpenSearch fork)
     ↓
Wazuh Dashboard (Kibana fork)
```

**Key Design Decisions:**
- **Agent-Manager Architecture**: Lightweight agents on endpoints report to centralized manager. Manager does heavy analysis.
- **Ruleset Engine**: XML-based rules with decoder → rule → alert pipeline. 4,000+ default rules. Supports rule chaining and frequency-based detection.
- **Multi-Source Correlation**: Correlate events from endpoints, cloud APIs, network devices, and applications in a single timeline.
- **CDB Lists**: Constant Database lists for IP reputation, user watchlists, known-bad hashes. Fast lookup during rule evaluation.
- **Active Response**: Automated remediation (block IP, kill process, quarantine file) triggered by rules.

## Core Modules

| Module | Size | Coupling | Purpose |
|--------|------|----------|---------|
| Agent | Large | Low | Endpoint data collection (FIM, log collection, SCA) |
| Manager (analysisd) | Large | High | Event analysis + rule evaluation + alert generation |
| Indexer | Large | Medium | OpenSearch-based event storage + search |
| Dashboard | Large | Medium | Visualization + case management |
| API | Medium | Low | RESTful management API |
| Ruleset | Medium | Low | 4,000+ XML detection rules |

## Extractable Patterns

1. **Decoder → Rule → Alert Pipeline** → `code-base/security/detection-pipeline/` — Three-stage event processing: parse (decode), evaluate (rule match), notify (alert). Universal pattern for any detection system.
2. **CDB Lists for Fast Lookup** → `code-base/security/reputation-lists/` — Constant database pattern for O(1) lookup of known-bad indicators during real-time analysis.
3. **Active Response Architecture** → `code-base/security/active-response/` — Automated remediation triggered by detection rules. Applicable to Shadow AI Scanner: auto-revoke API keys when shadow AI detected.
4. **Rule Chaining** → Composite rules that trigger only when multiple conditions match in sequence — reduces false positives.

## Competitive Comparison

| | Wazuh | Splunk | ELK/Elastic SIEM | QRadar |
|---|-------|--------|-------------------|--------|
| License | GPL-2.0 | Proprietary | Elastic License | Proprietary |
| Cost | Free | $150+/GB/day | Free (basic) | Enterprise only |
| Agents | ✅ native | Universal Forwarder | Elastic Agent | ✅ |
| Cloud | ✅ (Wazuh Cloud) | ✅ | ✅ | ✅ |
| Default rules | 4,000+ | 1,000+ | 700+ | 500+ |
| Vulnerability scan | ✅ built-in | Via add-ons | Via add-ons | Via add-ons |
| Compliance | ✅ PCI/HIPAA/GDPR/NIST | ✅ | ✅ | ✅ |
| AI/ML detection | Basic | ✅ (MLTK) | ✅ (ML jobs) | ✅ (Watson) |

## Solo Dev Verdict

**Overkill for solo SaaS — but the architecture is a masterclass in detection engineering.** You don't need a full SIEM for a Vercel-deployed Micro SaaS. Use Vercel's built-in logging + Sentry for errors.

However, Wazuh's **detection pipeline architecture** (decode → rule → alert → active response) is the gold standard for building any security monitoring product. Shadow AI Scanner should implement this exact pattern:
1. **Decode**: Parse AI tool usage events (API calls, browser extensions, agent actions)
2. **Rule**: Evaluate against policy (unauthorized tool? sensitive data exposed?)
3. **Alert**: Notify admin with severity + context
4. **Respond**: Auto-revoke token / quarantine agent / notify compliance team

**⭐ Best Extract**: Decoder → Rule → Alert → Active Response four-stage pipeline architecture.
