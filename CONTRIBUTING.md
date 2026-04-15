# 🤝 Contributing to security-stack

This repository is part of the [GitHub Open Source Knowledge Restructuring Project](https://github.com/bursh3347-collab).

## 📋 How to Contribute

### Add a New Project Analysis
1. Create `projects/[project-name].md` using the TEMC template below
2. Update `comparison.md` with the new project
3. Update `SOURCES.md` with the source link and license
4. Update the README.md project table and 飙升榜
5. Submit a Pull Request

### Improve Existing Analysis
- Fix outdated Stars/metrics data
- Add missing architecture details
- Improve extractable components section
- Add or update 天子点评

### Add Best Practices
- Extract cross-project patterns to `best-practices/`
- Add extractable code to `code/` with full documentation

## 📝 TEMC Template

Every project analysis must include:

```markdown
# Project Name

> One-line description

| Metric | Data |
|--------|------|
| GitHub | [owner/repo](link) |
| Stars | X,XXX |
| License | MIT/Apache-2.0/... |
| Language | ... |

## TEMC Score
| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | XX | Data-backed reasoning |
| E Ecosystem | XX | ... |
| M Market | XX | ... |
| C Combo | XX | ... |
| **Overall** | **XX** | |

## Core Value / Architecture / Key Modules / Extractable Components
## Why It Might NOT Be Worth It (required for scores ≥ 80)
## 天子点评
One-line judgment from天子's perspective.
```

## ✅ Quality Standards

- **TEMC scores must be backed by data** — no subjective scoring without evidence
- **Counter-argument required** for projects scoring ≥ 80
- **Stars > 500** minimum (exceptions must be justified)
- **Active within 90 days** (no abandoned projects)
- **Permissive license** (MIT / Apache-2.0 / BSD preferred)
- **天子点评** required for every project

## 🌐 Language

Project analyses are in English. 天子点评 and roadmap content may be in Chinese.

## 📬 Questions?

Open an issue or submit a PR. All contributions welcome!
