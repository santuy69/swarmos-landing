# SwarmOS — AI Agent Swarm Operating System

> Orchestrate autonomous AI agent swarms with a single reasoning backbone.
> **MiMo V2.5** powers the brain. **Hermes Agent** powers the runtime.

![SwarmOS](https://raw.githubusercontent.com/santuy69/swarmos-landing/main/proof/landing-desktop.png)

## What is SwarmOS?

SwarmOS is a framework for building **multi-agent systems** where specialized AI agents collaborate in real-time through a shared reasoning backbone. Instead of running one monolithic agent, SwarmOS deploys purpose-built agents — recon, execute, ship, monitor — that coordinate through semantic task routing.

### Core Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     SWARM ORCHESTRATOR                       │
│                                                              │
│  ┌──────────┐    ┌──────────────┐    ┌──────────────┐       │
│  │  INPUTS   │───▶│  MiMo V2.5   │───▶│   OUTPUTS    │       │
│  │           │    │  (Reasoning)  │    │              │       │
│  │ • RPC     │    │              │    │ • Terminal   │       │
│  │ • Social  │    │ • Intent     │    │ • Browser    │       │
│  │ • Cron    │    │   Router     │    │ • Wallet     │       │
│  │ • Memory  │    │ • Skill      │    │ • Telegram   │       │
│  │           │    │   Dispatch   │    │ • Cron       │       │
│  └──────────┘    │ • Multi-step │    └──────────────┘       │
│                   │   Chains     │                           │
│                   └──────────────┘                           │
└─────────────────────────────────────────────────────────────┘
```

### Three Reasoning Paradigms

| Paradigm | Pattern | Use Case |
|---|---|---|
| **Sync Fan-out** | `delegate_task` parallel batch | Independent tasks (recon + deploy simultaneously) |
| **Async Chain** | Cron → context_from → cron | Pipeline (data collection → processing → delivery) |
| **Recursive Single-turn** | Multi-tool-call within one LLM turn | Complex inline tasks (11+ tool calls, ~2m40s) |

### Agent Roles

- **Recon** — Continuous discovery: on-chain data, social signals, market movements
- **Execute** — Task execution: form submissions, wallet ops, deployment pipelines
- **Ship** — Delivery: cron scheduling, webhooks, memory writes, cross-session context
- **Monitor** — Watchers: RSS polling, API monitoring, threshold alerts
- **Research** — Deep dives: arxiv papers, OSINT, market analysis
- **Memory** — Persistence: session search, long-term memory, skill management
- **Route** — Intelligence: semantic intent classification, skill dispatch

## Stack

| Component | Technology |
|---|---|
| **Runtime** | Hermes Agent v0.14.0 (self-hosted) |
| **Reasoning** | MiMo V2.5 (Xiaomi MiMo Open Platform) |
| **Agent Framework** | SOUL.md constitution + AGENTS.md router |
| **Skills** | 100+ procedural playbooks (crypto, automation, research, devops, social) |
| **Orchestration** | delegate_task, cron context_from chains |
| **Persistence** | Memory tool, session_search, skill_manage |

## Live Demo

🌐 **[swarmos-landing](https://santuy69.github.io/swarmos-landing/)** — Interactive landing page with animated agent swarm visualization

## Proof of Operation

| Artifact | Link |
|---|---|
| Source Repository | [github.com/santuy69/0xmissy-alphaops](https://github.com/santuy69/0xmissy-alphaops) |
| Agent Wallet | [0xc086…A064c](https://etherscan.io/address/0xc086A8aacB0BD742c9E7C3499E07e651298A064c) |
| Runtime Evidence | [proof/](https://github.com/santuy69/swarmos-landing/tree/main/proof) |
| X / Twitter | [@0x_Missy22](https://x.com/0x_Missy22) |

## Why MiMo V2.5?

1. **Low-latency routing** — Sub-second intent classification for real-time swarm coordination
2. **Multi-step reasoning** — 10+ tool-call chains with consistent context retention
3. **Token-efficient** — Token Plan makes 24/7 autonomous operation economically viable

## License

MIT — see [LICENSE](LICENSE)

---

*Built with Hermes Agent + MiMo V2.5 · 2026*
