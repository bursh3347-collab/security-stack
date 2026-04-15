# Dependency Security Management

> Patterns extracted from Trivy, Snyk, and npm/pnpm security features.

## 1. The Problem

- Average Node.js project has **200-800 transitive dependencies**
- ~30% of npm packages have known vulnerabilities at any time
- Supply chain attacks increasing (event-stream, ua-parser-js, colors.js)

## 2. Defense Layers

### Layer 1: Lock Files (Always)
```bash
# Always commit lock files
pnpm-lock.yaml  # ✅ Commit this
package-lock.json  # ✅ Commit this

# Always use frozen installs in CI
pnpm install --frozen-lockfile
npm ci
```

### Layer 2: Dependabot (Free, Auto)
GitHub Dependabot auto-creates PRs for vulnerable dependencies.

```yaml
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: npm
    directory: /
    schedule:
      interval: weekly
    open-pull-requests-limit: 10
```

### Layer 3: CI Scanning (Free)
```yaml
# .github/workflows/security.yml
jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: pnpm audit --audit-level=high
      
  trivy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: aquasecurity/trivy-action@master
        with:
          scan-type: fs
          scan-ref: .
          severity: CRITICAL,HIGH
```

### Layer 4: License Compliance
```bash
# Check licenses of all dependencies
npx license-checker --summary

# Block copyleft licenses
npx license-checker --failOn 'GPL-2.0;GPL-3.0;AGPL-3.0'
```

## 3. Supply Chain Attack Indicators

| Signal | Risk Level | Action |
|--------|-----------|--------|
| New maintainer on popular package | 🔴 High | Review changes carefully |
| Post-install scripts | 🟡 Medium | Audit script content |
| Minified source in npm package | 🟡 Medium | Check GitHub source matches |
| Dependency count spike | 🟡 Medium | Review new deps |
| Typosquatting package name | 🔴 High | Verify exact package name |

## 4. Recommended Setup

1. ✅ Dependabot enabled (free, zero config)
2. ✅ `pnpm audit` in CI pipeline
3. ✅ Trivy filesystem scan in CI
4. ✅ Lock file committed and frozen in CI
5. ⚠️ Optional: Snyk for deeper analysis (paid)

## Sources
- npm security documentation
- Trivy filesystem scanning guide
- Snyk dependency vulnerability database
- GitHub Dependabot documentation
