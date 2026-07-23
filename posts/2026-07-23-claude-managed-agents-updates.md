---
title: "Claude API: five Managed Agents updates (effort levels, more webhooks, session seeding)"
date: 2026-07-23
description: Five small API updates for Claude Managed Agents landed on July 22 — configurable effort levels, more webhook event types, session seeding, optional version checks, and thread-level event streaming.
---

## What changed

Claude Managed Agents is Anthropic's fully managed service for running Claude as an autonomous agent, with built-in sandboxing, tools, and event streaming, all accessed through the API. On July 22, 2026, five updates landed in the Claude Platform release notes:

- **Effort levels on agent model config.** You can now set an `effort` level (how much reasoning depth the model applies) directly on a Managed Agents agent's model configuration, by passing `effort` inside the `model` object when you create the agent.
- **More webhook event types.** Webhooks (automatic notifications sent to your server when something happens) now cover the environment and memory-store lifecycle: four new `environment.*` event types and three new `memory_store.*` event types. This lets you react to environment or memory-store changes without repeatedly polling the API to check.
- **Seed a session with initial events.** When creating a session, you can now pass `initial_events` on `POST /v1/sessions` — up to 50 `user.message` and `user.define_outcome` events. If this list isn't empty, the agent starts working immediately in that same call, so you don't need a separate follow-up request to kick things off.
- **Optional version field when updating an agent.** The `version` field is now optional when updating a Managed Agents agent. Supply it if you want optimistic concurrency control (the update fails with a 409 error if the version doesn't match what's on the server); omit it to apply the update unconditionally.
- **Event deltas on session thread streams.** Session thread event streams now support "event deltas" — `GET /v1/sessions/{session_id}/threads/{thread_id}/stream` accepts the same `event_deltas[]` query parameter as the session-level stream, letting you preview a subagent's text as the model generates it, rather than waiting for the complete message.

## Why it matters

These are all incremental developer-experience improvements rather than new capabilities. The most useful ones for most integrations are probably session seeding (fewer round-trips to start an agent working) and the expanded webhooks (less polling, more event-driven code). The optional `version` field simplifies update calls for callers who don't need to guard against concurrent edits.

## How to use it

- To set an effort level: include `effort` inside the `model` object when calling the agent-creation endpoint.
- To use the new webhooks: subscribe to the new `environment.*` and `memory_store.*` event types in your webhook configuration.
- To seed a session: pass an `initial_events` array (up to 50 `user.message`/`user.define_outcome` events) in your `POST /v1/sessions` call.
- To skip optimistic concurrency checks on agent updates: omit `version` from the update request body.
- To preview subagent text as it streams: add `event_deltas[]` as a query parameter on the thread stream endpoint.

## Source

- [Claude Platform release notes — July 22, 2026](https://platform.claude.com/docs/en/release-notes/api#july-22-2026)
