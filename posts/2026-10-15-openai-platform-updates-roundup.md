---
title: "OpenAI platform roundup: Ultrafast mode and GPT-4-series retirement date"
date: 2026-10-15
description: GPT-6.1 Sol gets a lower-latency "ultrafast" tier in the Responses API, and OpenAI set a January 14, 2027 shutdown date for GPT-4o, GPT-4o mini, GPT-4.1, and GPT-4.1 mini.
---

## What changed

Two smaller OpenAI platform updates from this week:

- **Ultrafast mode for GPT-6.1 Sol (Oct 8).** In the Responses API, setting `service_tier` to `"ultrafast"` on a `gpt-6.1-sol` request reduces the time between generated output tokens — meaning text streams back to you faster, token by token. It's open to all API users (subject to normal rate limits) and supports both US and EU data residency. Pricing for this tier is on OpenAI's pricing page.
- **GPT-4-series models set to retire (announced Oct 14).** OpenAI announced that `gpt-4o-2024-08-06`, `gpt-4o-2024-11-20`, `gpt-4o-mini-2024-07-18`, `gpt-4.1-2025-04-14`, and `gpt-4.1-mini-2025-04-14` will be shut down on **January 14, 2027**. Fine-tuned versions built on these models follow the same shutdown date as their base model. OpenAI's recommended replacement is `gpt-6-luna`.

## Why it matters

The ultrafast tier is useful if your product is latency-sensitive — chat interfaces, live coding assistants, anything where users notice text appearing slowly. It's an API setting, not a new model, so no other behavior should change.

The GPT-4-series retirement is the one that needs action if it affects you: January 14, 2027 sounds far off, but if you have production code hard-coded to any of these five specific model snapshots (or a fine-tune built on one of them), you'll need to migrate before then. OpenAI points to `gpt-6-luna` as the suggested replacement, but you should test your prompts against it rather than assuming a drop-in swap, since behavior differs between model generations.

## How to use it

- To try ultrafast mode, set `"service_tier": "ultrafast"` on a Responses API request using `gpt-6.1-sol`.
- If you use `gpt-4o-2024-08-06`, `gpt-4o-2024-11-20`, `gpt-4o-mini-2024-07-18`, `gpt-4.1-2025-04-14`, `gpt-4.1-mini-2025-04-14`, or a fine-tune of any of them, plan to migrate to `gpt-6-luna` (or another current model) before January 14, 2027.

## Source

- [OpenAI API changelog](https://developers.openai.com/api/docs/changelog)
- [OpenAI model deprecations](https://developers.openai.com/docs/deprecations)
