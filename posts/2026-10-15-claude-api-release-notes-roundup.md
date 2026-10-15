---
title: "Claude API roundup: OpenTelemetry tracing, dynamic workflows, Compliance API updates"
date: 2026-10-15
description: Claude Platform release notes from October 8–14, 2026 — OpenTelemetry tracing leaves beta, Managed Agents can now write their own multi-agent workflows, and the Compliance API covers more ground.
---

## What changed

Highlights from the Claude Platform release notes, published between October 8 and October 14, 2026:

- **OpenTelemetry export (Oct 14, beta).** You can now trace Messages API requests and Claude Managed Agents sessions using OpenTelemetry, a standard format for application monitoring data. The Claude SDK can emit this tracing data in Python, TypeScript, C#, Go, Java, PHP, and Ruby. To get it from the API directly, you add an OpenTelemetry destination in the Claude Console.
- **Managed Agents scheduled deployments on AWS (Oct 14).** Claude Managed Agents' "scheduled deployments" feature — running an agent automatically on a schedule — is now available on Claude Platform on AWS, not just the main Claude Platform.
- **Managed Agents dynamic workflows (Oct 9, beta, `managed-agents-2026-04-01` beta header).** A Managed Agents agent can now write its own "workflow" — a program that runs many smaller agents in phases and combines their results — for jobs with a lot of repetitive pieces, like reviewing hundreds of documents. The workflow runs in the background as a "workflow run," and you follow its progress through `workflow_run.*` events on the session's event stream. You turn this on by setting the agent's `multiagent` field to `{"type": "multiagent_20261001", "workflows": {"type": "enabled"}}`, and you tell the agent in its system prompt when to start one.
- **Compliance API updates (Oct 8, beta).** The Compliance API — which lets organizations audit how Claude is used — got two additions for Claude Enterprise organizations: its chat endpoints now also return chats from the unified Claude experience (using your existing Compliance Access Key), and it can now download Claude Docs documents as Word files.

## Why it matters

The OpenTelemetry export matters if your organization already monitors application performance with tools like Datadog, Grafana, or Honeycomb — you can now pull Claude API and Managed Agents activity into that same pipeline instead of building custom logging. Dynamic workflows is a meaningful capability upgrade for Managed Agents: instead of you designing a fixed multi-agent pipeline in advance, the agent can decide on the spot to fan a large task out across many sub-agents and merge the results, which is a better fit for unpredictable, large-scale work. The Compliance API changes are narrower — they matter mainly to Claude Enterprise admins doing usage audits or e-discovery.

## How to use it

- To get OpenTelemetry traces, add a destination in the Claude Console, or use the Claude SDK (available in seven languages) to emit spans directly.
- To turn on dynamic workflows for a Managed Agents agent, set `multiagent` to `{"type": "multiagent_20261001", "workflows": {"type": "enabled"}}` and send the `managed-agents-2026-04-01` beta header; tell the agent when to start a workflow run in its system prompt, and track progress via `workflow_run.*` events.
- Compliance API changes require no setup beyond an existing Compliance Access Key for Claude Enterprise organizations.

## Source

- [Claude Platform release notes — October 14, 2026](https://platform.claude.com/docs/en/release-notes/api#october-14-2026)
- [Claude Platform release notes — October 9, 2026](https://platform.claude.com/docs/en/release-notes/api#october-9-2026)
- [Claude Platform release notes — October 8, 2026](https://platform.claude.com/docs/en/release-notes/api#october-8-2026)
