---
title: OpenAI DevDay 2026 — GPT-6.1 Sol, computer use for the Agents API, and an Ultrafast speed tier
date: 2026-09-30
description: At its September 29 developer conference, OpenAI released GPT-6.1 Sol, added computer-use support to its Agents API, and detailed a paid "Ultrafast" speed tier.
---

## What changed

OpenAI held its DevDay developer conference on September 29, 2026, in San Francisco. Three concrete, developer-facing releases came out of it:

**GPT-6.1 Sol.** A new model released with multi-agent support in beta. OpenAI describes it as priced at roughly one-fifth of GPT-6 Astra's standard per-token price, while aiming for intelligence close to Astra's.

**Computer use added to the Agents API.** The Agents API (announced in September and covered here previously) is OpenAI's managed way to run agents — OpenAI hosts the session, handles context compaction, and manages multi-agent orchestration so you don't build that infrastructure yourself. As of DevDay, it can also drive an OpenAI-hosted browser to operate software the way a person would ("computer use" — the model looks at a screen and decides what to click or type), alongside its existing support for MCP server connections and running multiple subagents in parallel with durable session state.

**Ultrafast, a paid speed tier.** Ultrafast is OpenAI's fastest service tier, aimed at cases where speed is worth paying extra for. It's broadly available today for GPT-6 Astra, with OpenAI describing performance up to 8x faster in Codex (OpenAI's coding tool) and up to 6x faster through the API. It's billed with separate rates for input, cached input, cache writes, and output tokens.

## Why it matters

Computer-use support in a managed Agents API is notable because it removes work that developers previously had to do themselves: standing up a browser environment, handling screenshots, and looping the model's clicks and keystrokes. Now OpenAI hosts that browser and the loop around it.

GPT-6.1 Sol's pricing — about a fifth of Astra's — makes it a cheaper option for workloads that don't need Astra's full capability, especially now that it supports multi-agent setups.

Ultrafast matters mainly for latency-sensitive or interactive uses, like an agent that needs to make many tool calls back-to-back without the user waiting. It costs more, so it's a tradeoff, not a free upgrade.

## How to use it

- To turn on Ultrafast for GPT-6 Astra, set two parameters on your API request: `model` to `"gpt-6-astra"` and `service_tier` to `"ultrafast"`.
- Ultrafast is rate-limited by usage tier (500K to 5M tokens per minute); higher limits require contacting your OpenAI account team. It currently supports US data residency and global processing only — it excludes EU endpoints.
- For agentic workloads with many rapid tool calls, OpenAI recommends using WebSockets rather than plain HTTP requests to cut down on network overhead.
- GPT-6.1 Sol and Agents API computer use are both in beta — check the Agents API guide for current setup steps before building on them.

## Source

- [OpenAI API changelog — September 29, 2026](https://developers.openai.com/api/docs/changelog)
- [OpenAI Developer Community: DevDay 2026 announcements and developer resources](https://community.openai.com/t/devday-2026-announcements-and-developer-resources/1402006)
- [OpenAI Agents API guide](https://developers.openai.com/api/docs/guides/agents)
- [OpenAI Ultrafast mode guide](https://developers.openai.com/api/docs/guides/ultrafast-mode)
