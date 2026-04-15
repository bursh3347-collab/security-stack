[English](README.md) | [中文](README_CN.md)

# 🔒 security-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/security-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/security-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/security-stack?style=flat-square)

> ⭐ 成熟度: **L1 成长期** — 7个项目已分析，横向对比完成，最佳实践进行中。

从GitHub全域 **7个高星安全工具** 中拆解精华、提炼最佳实践、深度分析架构模式。每个项目使用 [TEMC评分体系](#temc评分) 量化评估。

## 📈 飙升榜（更新：2026-04-15）

| 排名 | 项目 | 总Stars | 周增 | 趋势 |
|------|------|---------|------|------|
| 1 | OWASP ZAP | 37k | +100 | → |
| 2 | Vault | 32k | +80 | → |
| 3 | Trivy | 25k | +200 | ↑ |
| 4 | Nuclei | 23k | +300 | 🚀 |
| 5 | Semgrep | 14.8k | +150 | ↑ |
| 6 | Falco | 7.8k | +30 | → |
| 7 | Snyk | N/A | N/A | → |

> 🌟 Nuclei 增速最快（模板生态爆发），Trivy 和 Semgrep 稳步增长。Shadow AI 安全领域正在催生新一波工具。

## 📋 仓库内容

### 已分析项目 (7)

| 项目 | Stars | TEMC | 语言 | 类别 |
|------|-------|------|------|------|
| [Semgrep](projects/semgrep.md) | 14.8k | **84** | OCaml | 静态分析(SAST) |
| [Trivy](projects/trivy.md) | ~25k | **81** | Go | 漏洞扫描 |
| [Nuclei](projects/nuclei.md) | ~23k | **79** | Go | 模板扫描 |
| [Snyk](projects/snyk.md) | N/A | **79** | N/A | 开发安全平台 |
| [OWASP ZAP](projects/owasp-zap.md) | ~37k | **73** | Java | 动态分析(DAST) |
| [Vault](projects/vault.md) | ~32k | **71** | Go | 密钥管理 |
| [Falco](projects/falco.md) | ~7.8k | **60** | C++ | 运行时安全 |

### 对比与最佳实践

- [📊 安全工具横向对比](comparison.md) — 类别矩阵 + 功能对比
- [🔐 安全编码](best-practices/secure-coding.md) — TypeScript安全模式
- [📦 依赖安全](best-practices/dependency-security.md) — 供应链防护
- [🗺️ 技术路线图](roadmap.md) — 安全工具趋势与预测

## 🎯 Micro SaaS 最小可行安全方案

免费、30分钟搞定：
1. **GitHub Dependabot** — 自动依赖更新（内置功能）
2. **Semgrep** — GitHub Actions CI中集成SAST扫描
3. **`pnpm audit`** — CI中检查依赖漏洞

## 🔗 与Shadow AI扫描器的关联

本仓库直接支撑Shadow AI安全扫描器产品开发：
- **Semgrep**: 基于模式的规则编写方法
- **Nuclei**: YAML模板架构（类似Medusa的9,600条规则）
- **Trivy**: 多目标扫描架构参考
- **OWASP Top 10**: 安全检查清单方法论

## 🏗️ 仓库结构

```
security-stack/
├── README.md              ← 英文版
├── README_CN.md           ← 你在这里
├── projects/              ← 单项目分析（TEMC评分）
├── best-practices/        ← 跨项目安全模式
├── code/                  ← 可提取代码（即将推出）
├── comparison.md          ← 横向对比表
├── roadmap.md             ← 技术趋势与预测
├── CONTRIBUTING.md        ← 贡献指南
└── SOURCES.md             ← 所有来源链接 + 许可证
```

## <a id="temc评分"></a>📊 TEMC评分体系

**综合评分** = T×0.25 + E×0.20 + M×0.30 + C×0.25

- **T（技术分）**: 代码质量、架构设计、技术栈匹配度、文档质量
- **E（生态分）**: Stars/Forks、社区活跃度、生态集成度、维护者信誉
- **M（时机分）**: 市场时机、竞品稀缺度、趋势匹配度、可商用性
- **C（组合分）**: 技术栈兼容性、模块可拆解性、商业组合价值、学习成本

## ⚔️ 天子点评

**先上Semgrep + Dependabot。** 零成本覆盖80%攻击面。Docker化时加Trivy做容器扫描。Vault暂时不需要——环境变量 + Vercel加密密钥对独立SaaS足够了。

Nuclei是做安全产品的秘密武器——其YAML模板架构是可扩展扫描的黄金标准。

## License

本仓库包含分析和提取的模式。详见 [SOURCES.md](SOURCES.md)。
