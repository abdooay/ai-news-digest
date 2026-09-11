---
title: "Claude API: automatic tool-call evaluation for Managed Agents, and a terminal session connector"
date: 2026-09-11
description: The Claude API adds an "auto" permission policy that evaluates each Managed Agents tool call automatically, plus an `ant` CLI command to attach a terminal to a running agent session.
---

## What changed

On September 10, 2026, the Claude Platform release notes added two changes for **Claude Managed Agents** (Anthropic's hosted service for running long-lived Claude-powered agents in the cloud):

- **A new `auto` permission policy.** Until now, each tool call an agent wanted to make had to be explicitly allowed, denied, or paused for a human to approve, based on rules you set in advance. With `auto`, the server itself evaluates each agent or MCP (Model Context Protocol — a standard way for AI models to connect to external tools and data) tool call as it happens, and decides whether to run it, deny it, or pause for approval. The events that report tool activity (`agent.tool_use` and `agent.mcp_tool_use`) now include a new `evaluation` field, alongside the existing `evaluated_permission` field, describing how each call was judged.
- **A new `ant` CLI command: `ant beta:sessions connect`.** This attaches your terminal to a running Managed Agents session so you can watch it live, send it messages, and approve or deny tool calls that are waiting on you — all from the command line instead of the web console. Adding the `--web` flag instead serves the Claude Console's session viewer locally and opens it in a browser.

## Why it matters

Before `auto`, teams running Managed Agents had to choose permission rules in advance for every kind of tool call, which is hard to get right for agents that encounter a wide variety of situations. Server-side evaluation means the platform can make a case-by-case judgment instead, cutting down on both unnecessary approval prompts and overly broad blanket-allow rules. The `evaluation` field in the event stream makes that judgment auditable — you can see why a call was allowed, denied, or escalated.

`ant beta:sessions connect` is a smaller but practical addition for anyone debugging or supervising an agent: instead of switching to a browser to check on a running session or approve a paused tool call, you can do it without leaving the terminal.

## How to use it

- To use the `auto` permission policy, set it as the `permission_policy` for an agent or MCP tool when configuring your Managed Agents session (see the linked docs below for exact syntax).
- Check the `evaluation` and `evaluated_permission` fields on `agent.tool_use` and `agent.mcp_tool_use` events to see how each call was handled.
- Run `ant beta:sessions connect` (from `ant` CLI v1.30.0 or later) and pass your session ID to attach your terminal to a live Managed Agents session; add `--web` to open the Console session viewer locally instead.

## Source

- [Claude Platform release notes — September 10, 2026](https://platform.claude.com/docs/en/release-notes/api#september-10-2026)
- [Let the server evaluate each call with `auto`](https://platform.claude.com/docs/en/managed-agents/permission-policies#let-the-server-evaluate-each-call-with-auto)
- [Connect to a Managed Agents session from your terminal](https://platform.claude.com/docs/en/cli-sdks-libraries/cli/sessions-connect)
