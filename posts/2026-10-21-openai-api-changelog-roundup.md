---
title: "OpenAI API roundup: 12-hour prompt caching, Agents API sandbox upgrades and ultrafast mode"
date: 2026-10-21
description: OpenAI's developer changelog adds a longer prompt-cache option, document-editing skills in hosted agent sandboxes, and a faster response tier for the Agents API.
---

## What changed

Three updates from OpenAI's API changelog this week:

- **12-hour prompt caching (Oct 20).** In the Responses API, you can now choose to cache shared instructions, tools, and context for 12 hours instead of the shorter default. Prompt caching means OpenAI stores and reuses the processed version of content you send repeatedly, which is cheaper and faster than reprocessing it every time. The longer cache window helps even when requests to the same prompt are hours apart. Writing to a 12-hour cache costs 2.5 times the normal input token price.
- **Hosted agent sandboxes get document-editing skills (Oct 16).** OpenAI-hosted sandboxes in the Agents API — isolated environments where an agent can safely run code — now include the Artifact SDK and built-in skills for creating and editing spreadsheets, presentations, and Word documents.
- **Ultrafast mode added to the Agents API (Oct 16).** You can now set `agent.service_tier` to `"ultrafast"` on a supported model in the Agents API to reduce the time between generated tokens, making responses stream back faster. (OpenAI had already added this ultrafast tier to the separate Responses API for a specific model earlier in October; this extends the same idea to the Agents API.)

## Why it matters

The 12-hour cache option is useful for apps with long-lived context — like a coding assistant or long-running agent — where the same large system prompt or tool set gets reused across requests that are spread out, not just back-to-back. It costs more per cache write, so it's a trade-off: pay more up front to save more later if requests keep coming back to the same content. The sandbox skills update means agents built on the Agents API can now generate and edit real office documents directly inside their sandbox, instead of you building that capability yourself. Ultrafast mode in the Agents API helps if your agent-based product is latency-sensitive, matching the option already available for simpler Responses API calls.

## How to use it

- To use the longer cache, choose the 12-hour prompt caching option in the Responses API (see OpenAI's prompt-caching guide for the exact parameter).
- Document-editing skills in hosted sandboxes require no setup beyond using OpenAI-hosted sandboxes in the Agents API — the Artifact SDK and skills are included automatically.
- To turn on ultrafast mode for an agent, set `agent.service_tier` to `"ultrafast"` when using a model that supports it in the Agents API.

## Source

- [OpenAI API changelog](https://developers.openai.com/api/docs/changelog)
