# 🗺️ Security Tools Technology Roadmap

> Last updated: 2026-04-15

## 🟢 当前主流

| 技术 | 地位 | 一人公司适用度 |
|------|------|----------------|
| **GitHub Dependabot** | 依赖安全自动化标准 | ⭐⭐⭐⭐⭐ 零成本必用 |
| **Semgrep** | 开源 SAST 领导者 | ⭐⭐⭐⭐ CI 集成 |
| **Trivy** | 多目标漏洞扫描标准 | ⭐⭐⭐ 容器场景用 |
| **OWASP Top 10** | 安全检查清单标准 | ⭐⭐⭐⭐⭐ 必读 |

## 🚀 崛起方向

### 1. AI/Agent 安全（🔥 天子核心赛道）
- **Shadow AI 检测**：15+ 竞品爆发（Reco $25M、Witness AI $58M、Kai $125M...）
- **Agent Security Scanner**：OWASP LLM Top 10 + MCP Security + Agent 行为监控
- **AI 代码审计**：Semgrep + AI = 自动生成安全规则
- **趋势**：AI 安全是 2026 年网络安全最大赛道（$250M 单周融资）

### 2. 供应链安全
- **SBOM 强制化**：EU Cyber Resilience Act 要求软件物料清单
- **Sigstore/cosign**：软件签名标准化
- **SLSA Framework**：供应链完整性等级
- **趋势**：从 "扫描漏洞" 到 "验证整条供应链"

### 3. Shift-Left + Developer-First
- **IDE 内安全检测**（VS Code 扩展）
- **PR 级安全审查**（自动评论安全问题）
- **Security Champions**：开发团队内嵌安全角色
- **趋势**：安全左移到开发阶段，不再是上线前才检查

### 4. 合规自动化
- **EU AI Act**（2026年8月执法）：AI 系统透明度要求
- **Colorado AI Act**（2026年6月生效）：AI 治理要求
- **NIST AI Agent Standards**：Agent 安全标准化
- **趋势**：合规需求驱动安全工具采购（天子产品的最大推力）

## ↓ 衰退方向

| 技术 | 衰退原因 |
|------|----------|
| **Jenkins 安全插件** | Jenkins 本身在衰退 |
| **手动渗透测试** | AI 辅助扫描越来越强 |
| **传统 WAF** | Agent 时代的攻击绕过传统 WAF |
| **单点安全工具** | 被平台化解决方案整合 |

## 🔮 6-12 月预测

1. **Shadow AI 检测将成为独立产品品类**（置信度 90%）— 已有 15+ 玩家
2. **至少 3 家 AI 安全公司获得 $50M+ 融资**（置信度 85%）
3. **OWASP 将发布 AI Agent Security Top 10**（置信度 70%）
4. **EU AI Act 执法将催生一波合规 SaaS**（置信度 80%）
5. **Semgrep 将推出 AI 辅助规则生成**（置信度 65%）

## 💡 对一人公司的影响

**核心建议**：
- **Shadow AI Scanner 是天子最高优先级产品方向**（门下省评分 9.0/10）
- **学习 Nuclei 的 YAML 模板架构**——这是天子产品的核心设计参考
- **关注 EU AI Act + Colorado AI Act 时间窗口**——合规需求是最强采购驱动力
- **最小安全栈**：Dependabot + Semgrep in CI + pnpm audit = 30 分钟零成本

> 天子判断：安全不是一人公司的负担，而是天子的产品机会。Shadow AI Scanner 赛道已被 $250M+ 资本验证。
