# Checkov

> Policy-as-code scanner for infrastructure-as-code (IaC) — catch misconfigurations before deploy.

| Metric | Data |
|--------|------|
| GitHub | [bridgecrewio/checkov](https://github.com/bridgecrewio/checkov) |
| Stars | ~7,400 |
| License | Apache-2.0 |
| Language | Python |
| Last Updated | Active (daily commits) |
| Contributors | 400+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 80 | 3,000+ built-in policies. Graph-based analysis (code→resource→connection graph). Python = easy to extend. Supports 30+ IaC frameworks. |
| E Ecosystem | 75 | Acquired by Palo Alto (Prisma Cloud). 400+ contributors. VS Code extension. Deep CI integration. Enterprise backing = stability. |
| M Market | 82 | IaC security is booming with cloud-native shift. Every Terraform/K8s user needs this. "Shift left" wave accelerating. Direct fit for DevSecOps pipeline. |
| C Combo | 78 | Python policies = learnable pattern for custom rule writing. Graph-based approach inspires AI agent permission scanning. Policy-as-code concept maps to Shadow AI policy engine. |
| **Composite** | **79** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Highlights

```
IaC Files (Terraform/K8s/Docker/CloudFormation/...)
        ↓
    Parser Layer (per-framework)
        ↓
    Resource Graph Builder
        ↓
    Policy Runner (3,000+ checks)
        ↓
    Results: PASSED / FAILED / SKIPPED
    (with CIS/NIST/SOC2/HIPAA mapping)
```

**Key Design Decisions:**
- **Graph-Based Analysis**: Builds a resource dependency graph, enabling cross-resource checks ("Is this S3 bucket connected to a public-facing ALB?").
- **Policy-as-Code**: Each check is a Python class OR YAML definition. Custom policies in minutes.
- **Framework Agnostic**: Single tool scans Terraform + Kubernetes + Dockerfile + CloudFormation + ARM + Serverless + Helm + ... 
- **Compliance Mapping**: Every check maps to CIS Benchmarks, NIST 800-53, SOC 2, HIPAA, PCI-DSS.
- **Supply Chain Scanning**: SCA + license compliance + VEX support.

## Core Modules

| Module | Size | Coupling | Purpose |
|--------|------|----------|---------|
| Parsers | Large | Low | Per-framework IaC parsing |
| Graph Builder | Medium | Medium | Resource dependency graph construction |
| Policy Runner | Medium | Low | Check execution engine |
| Built-in Checks | Large | Low | 3,000+ individual policy checks |
| Compliance Mapper | Small | Low | Maps checks to compliance frameworks |
| CLI | Medium | Medium | User interface + CI integration |

## Extractable Patterns

1. **Policy-as-Code Architecture** → `code-base/security/policy-as-code/` — Define security policies as versioned, testable code. Core concept for Shadow AI policy engine.
2. **Graph-Based Analysis** → `code-base/security/resource-graph/` — Build dependency graphs to find cross-resource vulnerabilities. Applicable to AI agent permission mapping.
3. **Compliance Mapping Framework** → `code-base/security/compliance-mapping/` — Every check → CIS/NIST/SOC2 mapping. Essential for enterprise security products.
4. **Multi-Framework Scanner** → Pattern for supporting multiple input formats with a unified analysis engine.

## Competitive Comparison

| | Checkov | tfsec | Terrascan | KICS |
|---|---------|-------|-----------|------|
| Frameworks | 30+ | Terraform only | 10+ | 15+ |
| Checks | 3,000+ | 200+ | 500+ | 1,800+ |
| Graph analysis | ✅ | ❌ | ❌ | ❌ |
| Compliance maps | ✅ CIS/NIST/SOC2 | ✅ CIS | ✅ CIS | ✅ CIS |
| Custom policies | Python + YAML | Rego | Rego | Rego |
| Enterprise | Prisma Cloud | Aqua | Accurics (acquired) | Checkmarx |
| Language | Python | Go | Go | Go |
| License | Apache-2.0 | MIT | Apache-2.0 | Apache-2.0 |

## Solo Dev Verdict

**Essential if you use Terraform or Kubernetes.** Add `checkov -d .` to your CI pipeline — catches S3 public access, open security groups, missing encryption, weak IAM policies before they hit production. Zero cost, 2-minute setup.

For a Vercel-only SaaS (no Terraform), Checkov isn't directly needed. But its **policy-as-code pattern is the single most important architecture to steal** for any security product: define rules as code, version them, test them, map them to compliance frameworks. This is exactly how Shadow AI Scanner's rule engine should work.

**⭐ Best Extract**: Policy-as-code architecture + compliance framework mapping + graph-based cross-resource analysis.
