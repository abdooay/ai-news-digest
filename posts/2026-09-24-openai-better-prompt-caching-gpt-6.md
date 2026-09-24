---
title: OpenAI improves prompt caching for GPT-6, aimed at long-running agents
date: 2026-09-24
description: GPT-6's prompt caching now keeps cached prompts usable for 30 minutes, lets developers mark exactly what to cache, and can pre-load context before a request arrives.
---

## What changed

OpenAI updated prompt caching for its GPT-6 models. Prompt caching is a way to avoid re-processing (and re-paying for) the parts of a prompt that stay the same across multiple requests — useful when an AI agent keeps sending similar context turn after turn. The update includes:

- A longer cache window: a shared prompt prefix (the identical starting portion of a prompt) that gets reused within 30 minutes now stays eligible for the cache, up from OpenAI's previous shorter window.
- Explicit "cache breakpoints," which let a developer mark exactly which parts of a prompt should be cached, instead of relying only on automatic matching.
- A `configuration_update` parameter that lets a developer change a model's reasoning effort partway through a conversation without breaking its cache.
- `allowed_tools` and `tool_choice` parameters that let a developer restrict which tools are available for a turn without removing tool definitions from the request — removing them previously could invalidate the cache.
- "Cache prewarming," which lets an application load expected context into the cache in advance, before the first real request needing it arrives.

OpenAI says cached input tokens can cost up to 90% less than uncached ones.

## Why it matters

Long-running AI agents — for example, ones that work through a large codebase refactor or write a long research document over many steps — send a lot of repeated context with each request. Without effective caching, that repeated context gets reprocessed (and rebilled) every single time, which is slow and expensive. A longer cache window, explicit control over what gets cached, and the ability to prewarm the cache all make it more practical to run this kind of long, multi-step agent without the cost and latency spiraling as the conversation grows.

## How to use it

- Use explicit cache breakpoints in your GPT-6 API requests to control what gets cached, instead of relying only on automatic prefix matching.
- Use `configuration_update` to change reasoning effort mid-conversation without losing your cache.
- Use `allowed_tools` and `tool_choice` instead of removing tool definitions when you want to limit which tools are available for a turn.
- Check OpenAI's Prompt Caching Dashboard to see your cache hit rate, and use the diagnostics tool it provides to find where cache misses (requests that couldn't use the cache) are happening.
- Consider prewarming the cache with expected context at application startup for latency-sensitive use cases.

## Source

- [Better prompt caching for GPT-6](https://openai.com/index/better-prompt-caching-for-gpt-6/)
