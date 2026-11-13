---
title: Anthropic launches self-hosted Claude Managed Agents
date: 2026-11-13
description: Organizations can now run the entire Claude Managed Agents service — not just the sandboxes — on their own infrastructure, with model calls going to a provider of their choice.
---

## What changed

Anthropic's Claude Managed Agents is a hosted service for running Claude as an autonomous agent: you define an agent, start a session, and exchange events with it while it works on a task. Until now, Anthropic ran the whole service for you. As of November 12, 2026, Anthropic has added **self-hosted Claude Managed Agents**, in which an organization runs the entire service itself — not only the "sandboxes" (the isolated containers where an agent's tools run commands and edit files), but also the API, the agent loop, and the database that stores agents, sessions, and session history.

A self-hosted deployment has these pieces, all run by the customer:
- **Server (`cma-server`)**: serves the API, runs the agent loop, and stores session data. It calls out to an inference provider whenever the agent needs the model — that can be Anthropic, Amazon Bedrock, Claude Models on Google Cloud, Microsoft Foundry, or the customer's own model gateway.
- **Database**: PostgreSQL 16 or later. Without one, the server keeps data only in memory, and a restart erases it.
- **Workers**: programs that pull work from the server and actually run an agent's shell and file tools inside the customer's own sandboxes.
- **Admin CLI and a console**: for creating environments and letting people sign in through the organization's own identity provider to create agents and run sessions.

The server exposes the same API as Anthropic's hosted service, so the existing SDK and `ant` command-line tool work against it unchanged. Anthropic's docs note some features exist only on the hosted service, and list the differences separately. Access requires contacting your Anthropic account team.

## Why it matters

This is aimed at organizations with requirements the hosted service can't meet: needing to keep agent session data entirely on their own infrastructure, or needing model calls to go to a specific inference provider — such as Amazon Bedrock, Google Cloud, Microsoft Foundry, or an internal model gateway — rather than directly to Anthropic. Running your own server also means your organization is responsible for securing it, running its database, and watching for unusual usage, work that Anthropic otherwise does for you.

One important limitation to note: the agent's shell tool is a real, unrestricted shell running with the worker process's own permissions and network access — the worker itself does not sandbox it. Isolation has to come from how you run the worker (for example, in a disposable container or VM), so this is squarely aimed at organizations with the operational capacity to run and secure that infrastructure themselves, not a casual option.

## How to use it

1. Contact your Anthropic account team to request access to the self-hosted Managed Agents download.
2. Set up a server, a PostgreSQL 16+ database, and workers that run in your own sandboxes (a Docker Compose stack and a `cma-sandboxes` Helm chart are provided for this).
3. Configure which inference provider the server should call for model requests (Anthropic by default, or Bedrock, Google Cloud, Microsoft Foundry, or your own gateway).
4. Point your existing SDK or `ant` CLI code at your own server instead of Anthropic's hosted endpoint — the API is the same.
5. Each release ships with an `operator-guide.md` file; Anthropic suggests having Claude read it to help you configure and run the server.

## Source

- [Claude Platform release notes — November 12, 2026](https://platform.claude.com/docs/en/release-notes/overview#november-12-2026)
- [Self-hosted Claude Managed Agents docs](https://platform.claude.com/docs/en/managed-agents/self-hosted)
