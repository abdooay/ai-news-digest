---
title: Anthropic launches Claude Fable 5.1 and Claude Mythos 5.1
date: 2026-09-01
description: Two new Claude models bring a 1M-token context window by default, much cheaper prompt caching, and eased safety limits for vetted science and security researchers.
---

## What changed

On September 1, 2026, Anthropic released two new AI models: **Claude Fable 5.1**, the general-release update to Fable 5, and **Claude Mythos 5.1**, the same underlying model but with fewer safety restrictions for vetted professionals.

Key facts about Fable 5.1:
- A 1 million token context window by default (a "context window" is how much text the model can hold in memory during a conversation), with up to 128,000 tokens of output.
- "Thinking" — the model's internal reasoning before it answers — now runs continuously by default, which Anthropic calls "adaptive thinking."
- Standard pricing is unchanged from Fable 5: $10 per million input tokens, $50 per million output tokens. But the price of reading from the prompt cache (reusing earlier parts of a conversation instead of reprocessing it) drops from $1 to $0.25 per million tokens, a 75% cut. Anthropic says this brings typical task cost down by about 25%, and up to 45% for longer, multi-step ("agentic") tasks.
- Text the model generates carries a hidden watermark; images and video it produces via the code execution tool carry Content Credentials tags (C2PA), a standard way of marking AI-made content.
- Available immediately on the Claude API, Amazon Bedrock, Google Cloud, and Microsoft Foundry. The API model name is `claude-fable-5-1`.

Mythos 5.1 is the same model with safety limits relaxed for vetted users, available only through two new programs: the Cyber Verification Program (for defensive security work) and the Life Sciences Verification Program (for biology/medical research). It's currently limited to US organizations. Anthropic says its safety filters now trigger far less often on legitimate questions: roughly 85% fewer false stops on basic biology and medical questions, and roughly 60% fewer on cybersecurity questions, while still blocking genuine threats.

On benchmarks Anthropic reported, Fable 5.1 scored 55.8% on Terminal-Bench 4.0 (a test of completing real tasks in a command-line terminal) and Mythos 5.1 scored 60.9%.

A few things break with this release: the API's `tool_choice` types `any` and `tool` are no longer supported for these models — using them now returns an error. Use `tool_choice: "auto"` or `"none"` instead, or switch to the newer "strict tool use" or "structured outputs" features for schema-following tool calls. Also, thinking blocks saved from an earlier turn are now only reusable with the same model or a newer one.

## Why it matters

The 1M-token context and always-on thinking mean the model can hold much more of a codebase or document set in memory and reason through longer problems without you managing context by hand. The 75% cut in cache-read price is a real, automatic savings for any application that reuses the same system prompt or reference documents across many requests. If your code sets `tool_choice` to `"any"` or a specific `"tool"`, switching to Fable 5.1 will break that call until you update the parameter.

## How to use it

- Call the model with `claude-fable-5-1` via the Claude API, Amazon Bedrock, Google Cloud, or Microsoft Foundry.
- If your code sets `tool_choice` to `"any"` or `"tool"`, change it to `"auto"` or `"none"`, or adopt strict tool use / structured outputs instead.
- Mythos 5.1 access requires applying to the Cyber Verification Program or Life Sciences Verification Program (currently US organizations only).
- No action is needed to get the cheaper cache pricing — it applies automatically to cached reads on the new models.

## Source

- [Introducing Claude Fable 5.1 and Claude Mythos 5.1](https://www.anthropic.com/claude-fable-and-mythos-5-1)
- [Claude Platform release notes, September 1, 2026](https://platform.claude.com/docs/en/release-notes/api#september-1-2026)
