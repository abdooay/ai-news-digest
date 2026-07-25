---
title: "Introducing Claude Opus 5"
date: 2026-07-24
description: Anthropic launched Claude Opus 5, its most capable model yet, at the same price as Opus 4.8, with a 1M-token context window and thinking turned on by default.
---

## What changed

On July 24, 2026, Anthropic released Claude Opus 5, an upgrade to the Opus tier (Anthropic's most capable line of Claude models, previously topped by Opus 4.8). Anthropic describes it as a "thoughtful and proactive" model, calling out particular strength in coding, agent tasks that run for a long time without supervision, scientific research (including organic chemistry and protein analysis), and generating technical diagrams.

Key specs and behavior:
- **Context window:** 1 million tokens (roughly 750,000 words), both as the default and the maximum, up from a smaller default on earlier Opus models. A token is a small chunk of text — a word or part of a word — that a model reads or writes at a time.
- **Max output:** 128,000 tokens per response.
- **Thinking:** "Thinking" (a mode where the model reasons step by step before answering) is on by default.
- **Pricing:** $5 per million input tokens and $25 per million output tokens — the same as Opus 4.8, so this is a capability upgrade at no extra cost. Fast mode (a faster response speed) costs double that, running about 2.5 times faster than the standard speed.
- **Effort control:** Opus 5 supports five "effort" levels — `low`, `medium`, `high`, `xhigh`, and `max` — which control how much reasoning the model applies to a task. `max` is meant for the hardest, most capability-critical work.
- **Behavior change:** you can only fully turn thinking off at effort `high` or below. Trying to disable thinking at `xhigh` or `max` now returns an error, a change from how Opus 4.8 behaved.

Anthropic also reported benchmark results: Opus 5 doubles Opus 4.8's score on Anthropic's internal Frontier-Bench test at a lower cost, and scored three times higher than competing models on ARC-AGI 3, a benchmark for novel problem-solving.

Alongside the launch, Anthropic shipped related API changes on the same day: mid-conversation tool changes (adding or removing tools mid-conversation while keeping the prompt cache) moved into beta on Opus 5 and a few other models, a new `fallbacks` parameter can automatically retry a refused request on Anthropic's recommended backup model, and fast mode was removed entirely for the older Opus 4.7 model — that model no longer offers a fast-mode option at all.

## Why it matters

This is a straight upgrade for anyone already paying for Opus-tier access: same price, bigger context window, and better benchmark results, so there's little reason to stay on Opus 4.8 once you've checked your workflow still works with it. The 1M-token context window by default (not something you have to opt into) matters for tasks that need the model to hold a lot of information at once, like reviewing a large codebase or a long document.

The effort-level restriction on disabling thinking is a real behavior change: if your code explicitly disables thinking while also requesting `xhigh` or `max` effort, that call will now fail with an error on Opus 5, and you'll need to update it.

## How to use it

- **API:** use the model ID `claude-opus-5`. It's available now on the Claude API, and also through Claude in Amazon Bedrock, Claude on Google Cloud, and Claude in Microsoft Foundry.
- **Claude.ai, Claude Pro, and Claude Code:** Opus 5 is available immediately in these products as well.
- **Set an effort level:** pass `effort` (`low`, `medium`, `high`, `xhigh`, or `max`) to control reasoning depth; use `max` for your hardest tasks.
- **If you disable thinking in code:** make sure you're not also requesting `xhigh` or `max` effort, or the request will return a 400 error.
- **Fast mode:** available at 2x the base price for about 2.5x the speed.

## Source

- [Introducing Claude Opus 5](https://www.anthropic.com/news/claude-opus-5)
- [Claude Platform release notes — July 24, 2026](https://platform.claude.com/docs/en/release-notes/api#july-24-2026)
