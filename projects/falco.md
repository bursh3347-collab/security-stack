# Falco

> Cloud-native runtime security — detect threats in real-time using system call monitoring.

| Metric | Data |
|--------|------|
| GitHub | [falcosecurity/falco](https://github.com/falcosecurity/falco) |
| Stars | ~7,800 |
| Forks | ~1,000 |
| License | Apache-2.0 |
| Language | C++ |
| CNCF | Graduated |
| Contributors | 200+ |

## TEMC Score

| Dimension | Score | Reasoning |
|-----------|-------|-----------|
| T Tech | 88 | eBPF-based syscall monitoring, real-time detection, Falco Rules engine |
| E Ecosystem | 75 | CNCF graduated, 7.8k stars, but niche (runtime security for K8s/containers) |
| M Market | 65 | K8s runtime security niche, growing but requires container infrastructure |
| C Combo | 25 | Requires K8s/container infrastructure,天子 uses serverless (Vercel) |
| **Overall** | **60** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Falco monitors system calls in real-time to detect suspicious behavior: shell spawned in container, sensitive file read, unexpected network connection. It's the runtime IDS for cloud-native.

## Architecture Highlights
- **eBPF/kernel module**: System call capture at kernel level
- **Rules Engine**: Falco Rules (YAML-based detection)
- **Plugins**: Extend data sources (CloudTrail, Okta, GitHub)
- **Alert Channels**: Slack, PagerDuty, SIEM integration

## Why It Might NOT Be Worth It
- Requires container/K8s infrastructure (not serverless)
- C++ codebase, very specialized
- eBPF requires Linux kernel ≥ 5.8
- Overkill for Vercel-deployed Micro SaaS
- Only makes sense at container orchestration scale
