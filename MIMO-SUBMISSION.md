# SwarmOS — Xiaomi MiMo 100T 申请材料

> Xiaomi MiMo Orbit 百万亿 Token 创造者激励计划 · 申请文档
> 表单地址：https://100t.xiaomimimo.com/

---

## 一、表单填写速查表

| 表单字段 | 填写值 |
|---|---|
| 项目名称 / Project Name | **SwarmOS** |
| 项目英文名 | SwarmOS — AI Agent Swarm Operating System |
| 项目类别 / Category | AI Agent · Multi-Agent Orchestration · Developer Tool |
| 阶段 / Stage | Alpha · Active Development（落地页 + 源码已上线） |
| 仓库 URL / Repo | `https://github.com/santuy69/swarmos-landing` |
| 项目网站 / Demo | `https://santuy69.github.io/swarmos-landing/` |
| License | MIT |
| 一句话 Tagline | One model. Infinite agents.（一个模型，无限代理。） |
| 团队规模 | 1 人独立开发者 |
| 联系方式 / Contact | X: @0x_Missy22 |
| 申请用邮箱 | （请填写已注册 platform.xiaomimimo.com 的邮箱） |

> 重要提示：申请用邮箱必须与 Xiaomi MiMo 开放平台账号一致，否则权益无法到账。

---

## 二、使用的 AI 工具与底层模型

### 底层模型（Underlying Models）

| 工作负载 | 模型 | 说明 |
|---|---|---|
| 主推理 / Swarm 调度 | **MiMo V2.5（计划接入）** | 意图分类、技能路由、多步推理链 |
| 代码生成 / 架构设计 | Anthropic Claude Sonnet/Opus 4.7 | 落地页生成、文档编写 |
| 视觉评审 | Gemini 2.0 Flash | 截图质量检查 |
| 嵌入 / 检索 | OpenAI text-embedding-3-small | 跨会话记忆搜索 |

### AI 编程工具（AI Coding Tools）

| 工具 | 用途 | MiMo 集成计划 |
|---|---|---|
| **Hermes Agent v0.14.0** | 主控 Agent 框架（自托管） | ✓ 主推理后端切换到 MiMo V2.5 |
| Claude Code CLI | PR 工作流、代码审查 | ✓ 可配置 MiMo API 端点 |
| OpenClaw | 项目上下文管理（AGENTS.md） | ✓ FAQ 明确提及 |
| Cursor | 本地代码编辑 | ✓ 支持自定义 base_url |

### 接入 MiMo V2.5 的具体计划

1. `~/.hermes/config.yaml` 添加 provider: `xiaomi`，base_url: `https://platform.xiaomimimo.com/v1`
2. 主推理负载（Swarm 调度、意图分类、技能路由）切换到 MiMo V2.5
3. 高频低延迟工作负载（Agent 间通信、实时任务路由）由 MiMo 处理
4. 周维度对比 MiMo V2.5 vs Claude 4.7 在 Agent 调度 + 工具调用场景的延迟/质量
5. 结果回写到仓库 `/benchmarks` 目录公开

---

## 三、项目描述

### A. 一句话（≤ 60 字）

> SwarmOS — 基于 MiMo V2.5 的 AI Agent 群智操作系统，一个模型驱动无限代理协同。

### B. 短描述（≤ 140 字）

> SwarmOS 是一个 AI Agent 群智编排框架。每个 Agent 专注一类任务（侦察、执行、交付、监控），通过语义路由共享单一推理核心。MiMo V2.5 作为推理骨干，实现亚秒级意图分类和多步工具链调用，使 7×24 小时自主运行在经济上可行。

### C. 中等描述（≤ 500 字）

> **SwarmOS** 是一个面向开发者的 AI Agent 群智操作系统框架，核心理念是「一个模型，无限代理」。
>
> 传统单体 Agent 将所有能力塞进一个推理循环——侦察、分析、执行、交付混在一起，上下文窗口膨胀，token 消耗失控。SwarmOS 的做法不同：将 Agent 职责拆分为 7 个专职角色（Recon / Execute / Ship / Monitor / Research / Memory / Route），每个角色通过 `skill_view` 按需加载 100+ 个过程式技能，零冷启动开销。
>
> 三种推理范式支撑不同工作流：
> 1. **同步扇出**（`delegate_task` 并行批次）— 独立任务同时执行
> 2. **异步链**（`cron context_from` 跨任务上下文注入）— 数据采集 → 分析 → 推送管道
> 3. **递归单轮**（单次 LLM 调用内 10+ 工具链）— WL 筛查、表单提交等复杂内联任务
>
> **MiMo V2.5 在此架构中的关键作用**：Swarm 调度需要亚秒级意图分类（用户消息 → 技能匹配 → Agent 分发），MiMo 的推理速度使得实时路由无需排队。同时，Token Plan 的定价模型使 7×24 小时自主运行在经济上可行——这是 Claude 等按量付费模型难以支撑的。
>
> 当前运行环境：Hermes Agent v0.14.0（自托管），100+ 技能库，EVM 多链钱包（0xc086…A064c），跨平台消息投递（Telegram / Discord）。计划在 Token Plan 到账后，将主推理后端从 Claude 切换到 MiMo V2.5，并发布基准对比报告。

### D. 详细描述（≤ 1200 字 · 中文）

> **SwarmOS：基于 MiMo V2.5 的 AI Agent 群智操作系统**
>
> **一、项目定位**
>
> SwarmOS 是一个开源的 AI Agent 群智编排框架，解决的核心问题是：如何用一个推理模型高效协调多个专职 Agent，实现 7×24 小时自主运行，同时将 token 成本控制在可持续范围内。
>
> 项目基于 Hermes Agent 运行时（自托管，v0.14.0），通过 SOUL.md 宪法文件定义 Agent 人格，AGENTS.md 路由器实现语义意图分发，100+ 个过程式技能（Skills）按需加载——每个技能是一个自包含的操作手册，包含触发条件、分步指令、常见陷阱和验证步骤。
>
> **二、架构设计：三种推理范式**
>
> SwarmOS 不使用单一的 Agent 循环，而是根据任务特性选择最优推理范式：
>
> 1. **同步扇出（Sync Fan-out）**：通过 `delegate_task` 并行启动多个子 Agent，各自在隔离上下文中执行，最终汇总结果。适用于独立任务（如同时进行链上数据侦察和社交媒体监控）。子 Agent 之间无共享状态，避免协调开销。
>
> 2. **异步链（Async Chain）**：通过 `cron` 定时任务 + `context_from` 上下文注入实现跨任务管道。Job A 采集数据，Job B 处理分析，Job C 推送通知——每个环节独立调度，通过上下文注入传递中间结果。
>
> 3. **递归单轮（Recursive Single-turn）**：在单次 LLM 调用中执行 10+ 个工具调用链。适用于需要紧密上下文的复杂任务（如 WL 筛查：RPC 查询 → 合约分析 → 社交验证 → 表单提交）。典型执行时间约 2 分 40 秒，消耗约 17k tokens。
>
> **三、Agent 角色体系**
>
> - **Recon Agent**：持续发现——链上数据、社交信号、市场动态。通过 web3-project-recon、polymarket、xurl 等技能实现多源数据采集。
> - **Execute Agent**：任务执行——表单提交、钱包操作、部署流水线。通过 non-custodial-wallet（8 链 EVM）、cloakbrowser（反检测浏览器）等技能完成。
> - **Ship Agent**：交付与持久化——cron 调度、webhook 触发、内存写入、跨会话上下文。
> - **Monitor Agent**：监控——RSS 轮询、API 监控、阈值告警。
> - **Research Agent**：深度研究——arxiv 论文、OSINT 调查、市场分析。
> - **Memory Agent**：持久化——会话搜索、长期记忆、技能管理。
> - **Route Agent**：智能路由——语义意图分类、技能分发。
>
> **四、MiMo V2.5 的关键作用**
>
> 选择 MiMo V2.5 作为 SwarmOS 的推理骨干，基于三个技术需求：
>
> 1. **低延迟路由**：Swarm 调度需要亚秒级意图分类。用户消息进入后，Router 需要在 < 1 秒内判断意图、匹配技能、分发到对应 Agent。MiMo 的推理速度使得这种实时路由成为可能。
>
> 2. **多步推理一致性**：工具调用链需要 10+ 步的上下文保持。MiMo 的推理深度确保长链调用不会丢失前序上下文。
>
> 3. **Token 经济性**：运行 7 个 Agent 7×24 小时，token 消耗巨大。MiMo Token Plan 的定价模型使持续自主运行在经济上可持续——这是 Claude 等按量计费模型无法比拟的优势。
>
> **五、当前状态与公开证据**
>
> - 源码仓库：https://github.com/santuy69/swarmos-landing （MIT）
> - 落地页演示：https://santuy69.github.io/swarmos-landing/
> - Agent 钱包：0xc086A8aacB0BD742c9E7C3499E07e651298A064c
> - 运行时证据：仓库 /proof 目录（技能注册表、运行时截图、架构证明）
> - 社交账号：X @0x_Missy22

---

## 四、证明材料清单

| # | 文件 | 说明 | GitHub 直链 |
|---|---|---|---|
| 1 | `landing-desktop.png` | 落地页桌面端截图（1440×1296） | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/landing-desktop.png) |
| 2 | `landing-hero.png` | OG 分享卡片（1200×630） | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/landing-hero.png) |
| 3 | `landing-fullpage.png` | 全页滚动截图 | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/landing-fullpage.png) |
| 4 | `proof-skills.png` | 100+ 技能注册表终端截图 | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/proof-skills.png) |
| 5 | `proof-runtime.png` | 运行时证据终端截图 | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/proof-runtime.png) |
| 6 | `proof-architecture.png` | Agent 架构终端截图 | [查看](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/proof-architecture.png) |

---

## 五、上传顺序建议（按影响力排序）

1. `landing-desktop.png` — 最强单张证明（完整的交互式落地页）
2. `proof-skills.png` — 100+ 技能注册表（基础设施证明）
3. `proof-runtime.png` — 运行时 + 钱包证据
4. `landing-fullpage.png` — 全页展示（架构图 + Why MiMo 部分）
5. `proof-architecture.png` — 三种推理范式详解
6. `landing-hero.png` — OG 卡片（可选）

---

*Generated: 2026-05-20 · SwarmOS v0.1.0 · MIT License*
