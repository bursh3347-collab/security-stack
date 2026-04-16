# Sources

> All projects analyzed in this repository.
> Last updated: 2026-04-16

| # | Project | GitHub | Stars | License | Category | TEMC |
|---|---------|--------|-------|---------|----------|------|
| 1 | Semgrep | [semgrep/semgrep](https://github.com/semgrep/semgrep) | 14,801 | LGPL-2.1 | SAST | 84 |
| 2 | Gitleaks | [gitleaks/gitleaks](https://github.com/gitleaks/gitleaks) | 25,976 | MIT | Secret Scanner | 82 |
| 3 | Trivy | [aquasecurity/trivy](https://github.com/aquasecurity/trivy) | ~25,000 | Apache-2.0 | Vulnerability Scanner | 81 |
| 4 | Checkov | [bridgecrewio/checkov](https://github.com/bridgecrewio/checkov) | ~7,400 | Apache-2.0 | IaC Security | 79 |
| 5 | Nuclei | [projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) | ~23,000 | MIT | Template Scanner | 79 |
| 6 | Snyk (Platform) | [snyk.io](https://snyk.io) | N/A | Proprietary | Dev Security | 79 |
| 7 | SonarQube | [SonarSource/sonarqube](https://github.com/SonarSource/sonarqube) | ~9,400 | LGPL-3.0 | SAST Platform | 78 |
| 8 | Snyk CLI | [snyk/cli](https://github.com/snyk/cli) | 5,500 | Apache-2.0 | Multi-Scanner | 77 |
| 9 | Wazuh | [wazuh/wazuh](https://github.com/wazuh/wazuh) | ~11,500 | GPL-2.0 | SIEM / XDR | 77 |
| 10 | Grype | [anchore/grype](https://github.com/anchore/grype) | 12,032 | Apache-2.0 | Container Scanner | 76 |
| 11 | CrowdSec | [crowdsecurity/crowdsec](https://github.com/crowdsecurity/crowdsec) | ~9,400 | MIT | Crowd Security | 74 |
| 12 | OWASP ZAP | [zaproxy/zaproxy](https://github.com/zaproxy/zaproxy) | ~37,000 | Apache-2.0 | DAST | 73 |
| 13 | Prowler | [prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | 13,602 | Apache-2.0 | Cloud Audit | 72 |
| 14 | Vault | [hashicorp/vault](https://github.com/hashicorp/vault) | ~32,000 | BUSL-1.1 ⚠️ | Secrets Management | 71 |
| 15 | Cosign | [sigstore/cosign](https://github.com/sigstore/cosign) | 5,824 | Apache-2.0 | Supply Chain | 70 |
| 16 | ModSecurity | [owasp-modsecurity/ModSecurity](https://github.com/owasp-modsecurity/ModSecurity) | ~8,200 | Apache-2.0 | WAF Engine | 68 |
| 17 | Falco | [falcosecurity/falco](https://github.com/falcosecurity/falco) | ~7,800 | Apache-2.0 | Runtime Security | 60 |

## License Notes
- ⚠️ Vault changed to BUSL-1.1. Consider **OpenBao** (Linux Foundation fork) for new projects.
- ⚠️ Semgrep uses LGPL-2.1 — OK for CI tool usage, but linking restrictions apply.
- ⚠️ Wazuh uses GPL-2.0 — copyleft, OK for self-hosted usage but derivative works must be GPL.
- ⚠️ SonarQube uses LGPL-3.0 — similar restrictions to Semgrep.
- Snyk platform is proprietary with free tier; Snyk CLI is Apache-2.0.
- All other projects use permissive licenses (MIT or Apache-2.0) ✅

## Category Coverage

| Category | Projects | Coverage |
|----------|----------|----------|
| SAST (Static Analysis) | Semgrep, SonarQube | ✅ Strong |
| Vulnerability Scanning | Trivy, Grype, Snyk | ✅ Strong |
| Secret Detection | Gitleaks | ✅ |
| DAST (Dynamic Analysis) | OWASP ZAP, Nuclei | ✅ Strong |
| IaC Security | Checkov, Prowler | ✅ Strong |
| WAF / Runtime | ModSecurity, Falco, CrowdSec | ✅ Strong |
| SIEM / XDR | Wazuh | ✅ |
| Secrets Management | Vault | ✅ |
| Supply Chain | Cosign | ✅ |
| Multi-Scanner | Snyk CLI | ✅ |
