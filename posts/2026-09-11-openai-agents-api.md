---
title: "OpenAI launches the Agents API: Codex's agent engine, available to any developer"
date: 2026-09-11
description: OpenAI's new Agents API, in public beta, gives developers the same agent harness and cloud infrastructure that powers Codex, so they can build a working cloud agent with one API call.
---

## What changed

On September 10, 2026, OpenAI launched the **Agents API** in public beta. A "harness" is the surrounding software that manages an AI agent's context, decides how it uses tools, and coordinates any sub-agents it delegates work to — separate from the underlying language model itself. The Agents API exposes the same harness and cloud infrastructure that powers Codex (OpenAI's coding agent) to any developer through a single API call: you specify a task, a model, the tools it can use, and where it should run, and OpenAI hosts and manages the agent for you.

Key pieces of the release:
- **Choice of environment.** Agents can run in an OpenAI-managed sandbox, on your own infrastructure, or through partner providers including Blaxel, Cloudflare, Daytona, DigitalOcean, E2B, Modal, Oracle, Runloop, and Vercel — covering different needs like staying inside your own network (VPC), specific storage requirements, or particular CPU/GPU configurations.
- **Automatic context compaction.** For agents that need to work for hours at a time, the API automatically compacts (summarizes and shrinks) older context as a session nears its context-window limit, so you don't have to write your own logic to keep long sessions running.
- **Tool search and programmatic tool calling.** "Tool search" loads only the tool definitions relevant to the current step, instead of every tool the agent has access to, cutting token usage and preserving prompt caching. "Programmatic tool calling" lets an agent run tool calls in parallel, chain them together, and filter or combine large results in code before bringing only what's relevant back into its context.
- **Multi-agent support.** Agents can split a complex task into independent pieces and hand each one to a sub-agent that works in parallel with its own separate context, while a main agent coordinates and combines the results.
- **Open-source foundation.** The API is built on the open-source Codex harness, so developers can inspect the actual code that coordinates model calls, tools, and context, rather than working against a black box.

## Why it matters

Building a reliable long-running agent from scratch is hard: you need infrastructure to keep it running for hours or days, logic to manage a shrinking context budget, and a way to let it use many tools without wasting tokens on definitions it doesn't need yet. Previously, developers who wanted this had to build it themselves or rely on OpenAI's own products (Codex, ChatGPT for Work) rather than their own applications. The Agents API packages that infrastructure so any developer can use it directly, and because OpenAI maintains the harness centrally, improvements from new model releases should reach existing integrations without requiring a rewrite.

## How to use it

- The Agents API is available today, in public beta, to all developers — no waitlist.
- There are no extra fees for the API itself: you pay only for the tokens and tools your agents actually use, per OpenAI's standard pricing.
- To try it, follow the guide in OpenAI's developer docs, which covers specifying a task, model, tools, and environment in a single API call, and configuring an environment (OpenAI-hosted sandbox, your own infrastructure, or a partner provider).
- Since it's a public beta, expect the API to keep changing based on developer feedback before it reaches general availability.

## Source

- [Introducing the Agents API](https://openai.com/index/introducing-the-agents-api/)
- [Agents API developer guide](https://developers.openai.com/api/docs/guides/agents-api/overview)
