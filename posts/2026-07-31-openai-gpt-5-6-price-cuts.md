---
title: OpenAI cuts GPT-5.6 Luna and Terra prices, adds Fast mode for Sol
date: 2026-07-31
description: Luna gets an 80% price cut, Terra gets 20% off, and Sol gains a paid Fast mode that runs up to 2.5x faster.
---

## What changed

On July 30, 2026, OpenAI cut API prices for two of its GPT-5.6 models and added a faster (but pricier) mode for the third, about three weeks after the GPT-5.6 family launched. GPT-5.6 comes in three sizes: Sol (the flagship, most capable), Terra (a balanced middle model), and Luna (the cheapest, most efficient one).

New prices per 1 million tokens:

| Model | Input (old → new) | Output (old → new) | Cached input (old → new) |
|-------|-------|--------|---------|
| Luna | $1.00 → $0.20 (80% cut) | $6.00 → $1.20 (80% cut) | $0.10 → $0.02 |
| Terra | $2.50 → $2.00 (20% cut) | $15.00 → $12.00 (20% cut) | $0.25 → $0.20 |
| Sol | $5.00 (unchanged) | $30.00 (unchanged) | $0.50 (unchanged) |

Sol's list price didn't change, but OpenAI added a new **Fast mode**: for double the standard price, it runs up to 2.5x faster. You turn it on by setting `"service_tier": "priority"` in the API request.

OpenAI says the cuts come from efficiency work done since GPT-5.6 launched: GPU kernel optimizations cut compute cost by about 20%, and improvements to speculative decoding (a technique where a smaller draft model predicts likely next tokens for the bigger model to confirm, speeding up generation) added roughly 15% more efficiency.

These prices apply across the API, the Codex CLI (OpenAI's coding tool), and ChatGPT. Model names in the API are `gpt-5.6-luna`, `gpt-5.6-terra`, and `gpt-5.6-sol`. Vision (image) input tokens are billed at 120% of the standard text token rate. OpenAI also says its own internal "auto-review" tooling has switched to using Luna, cutting its cost by roughly tenfold.

## Why it matters

If you're already building on GPT-5.6 Luna or Terra, your API bill for those models drops immediately with no code changes needed — you're charged the new, lower rate automatically. OpenAI says Luna now costs less than the older GPT-5.4 mini model did, making it the go-to option when you need a cheap model for high-volume, less-demanding tasks (like classifying text or a first-pass filter before a bigger model looks at it).

The new Fast mode on Sol is opt-in and costs more, so it's only worth it if your product genuinely needs lower latency (like a live chat interface) and can absorb double the cost for that one model.

## How to use it

- No action needed to get the lower Luna/Terra prices — they apply automatically to existing usage of `gpt-5.6-luna` and `gpt-5.6-terra`.
- To use Fast mode on Sol, add `"service_tier": "priority"` to your API request when calling `gpt-5.6-sol`. This costs 2x the standard Sol price.
- Check your current spend and rates on your OpenAI usage dashboard to see the new pricing reflected.

## Source

- [OpenAI Developer Community: "Announcing a major Price drop for 5.6 Terra and Luna and Fast mode for 5.6-Sol"](https://community.openai.com/t/announcing-a-major-price-drop-for-5-6-terra-and-luna-and-fast-mode-for-5-6-sol/1388484)
