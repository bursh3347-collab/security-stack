# Prowler

> World's most widely used open-source cloud security platform

| Metric | Data |
|--------|------|
| GitHub | [prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) |
| Stars | 13,602 |
| License | Apache-2.0 |
| Language | Python |
| Last Updated | 2026-04-16 |
| Contributors | 300+ |
| Forks | 2,095 |
| Open Issues | 203 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Python, 500+ checks across AWS/Azure/GCP/K8s. CIS benchmarks, PCI-DSS, HIPAA, SOC2 compliance |
| E (Ecosystem) | 78 | 14k stars, used by AWS in Security Hub integration. Commercial Prowler SaaS available |
| M (Market) | 80 | Cloud compliance is mandatory for any SaaS handling customer data. EU AI Act adds urgency |
| C (Combo) | 65 | Relevant when running on AWS/GCP, but overkill for Vercel+Supabase. Becomes critical at enterprise |
| **Overall** | **72** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Prowler automates cloud security audits and compliance checks across multi-cloud environments:
- **500+ security checks** across AWS, Azure, GCP, Kubernetes
- **Compliance frameworks** — CIS, PCI-DSS, HIPAA, SOC2, GDPR, ISO 27001
- **Automated scanning** — run in CI/CD or scheduled
- **Dashboard** — Prowler SaaS for visual reporting
- **Remediation guidance** — each finding includes fix instructions

## Architecture Highlights

- **Core**: Python 3.12+, modular check architecture
- **Providers**: AWS (boto3), Azure (SDK), GCP (API), K8s (kubectl)
- **Check system**: Each check is a Python class with metadata + audit logic + remediation
- **Output**: JSON, CSV, HTML, OCSF (Open Cybersecurity Schema Framework)
- **Integration**: AWS Security Hub, Slack, Jira, S3

## Solo Dev Verdict

**🟡 USE WHEN ON AWS** — If you're on Vercel+Supabase, Prowler isn't needed yet. But once you have AWS resources (S3 buckets, Lambda functions, RDS databases), run Prowler quarterly to catch misconfigurations.

**Key use case**: SOC2 compliance preparation. Prowler generates the evidence reports auditors need.

## Risks & Counter-Arguments

- **AWS-heavy**: Best coverage is AWS; Azure and GCP support is growing but less mature
- **Noisy**: 500+ checks generate many low-severity findings. Tuning required
- **vs AWS Config/Security Hub**: AWS native tools are tightly integrated but vendor-locked
- **Python dependency**: Large Python dependency tree, Docker recommended for clean runs
