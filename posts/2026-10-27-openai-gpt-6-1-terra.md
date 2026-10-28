---
title: "OpenAI releases GPT-6.1 Terra, 50% cheaper and 3x faster than its predecessor"
date: 2026-10-27
description: OpenAI released GPT-6.1 Terra, a fast, efficient model for visual reasoning and computer use, with 50% lower API prices than GPT-5.6 Terra.
---

## What changed

OpenAI released a new model called **GPT-6.1 Terra** on October 26, 2026. OpenAI describes it as understanding what's on screen, taking action across apps, writing naturally, and being a more capable model for everyday work while staying efficient.

Key details from OpenAI's announcement:

- **Pricing**: standard API prices are 50% lower than GPT-5.6 Terra, its predecessor.
- **Speed and capability**: OpenAI says GPT-6.1 Terra substantially outperforms GPT-5.6 Terra on "Agents' Last Exam," a test of how well agents use software at work. OpenAI also claims it matches GPT-6 Astra (a larger, more expensive model) on that test at one-tenth the price per token, while finishing tasks over 3x faster on average than both GPT-6 Astra and GPT-6.1 Sol.
- **Availability**: it's rolling out now to all ChatGPT Plus, Pro, Enterprise, and Edu users in ChatGPT Work and Codex, where it stretches a usage allowance further than GPT-5.6 Terra, GPT-6.1 Sol, or GPT-6 Astra do. Developers can also call it through the OpenAI API as `gpt-6.1-terra`, via the `v1/responses` and `v1/chat/completions` endpoints.
- OpenAI positions GPT-6.1 Sol and GPT-6 Astra as the better choices for in-depth research or complex coding, with Terra meant for lighter, faster, cheaper everyday tasks.

OpenAI published a model guide with prompting and migration advice for developers moving from an earlier model to GPT-6.1 Terra.

## Why it matters

"Visual reasoning" and "precise computer use" both point to a model meant for agents that look at a screen and act on it — reading an image or screenshot and deciding what to click or type, for example. The 50% price cut and claimed 3x speed advantage over larger models make Terra a cheaper default option for agent and computer-use tasks that don't need a top-tier model's full reasoning power. If you're already using GPT-5.6 Terra, this is a direct, cheaper upgrade; if you're using a bigger model like GPT-6 Astra for tasks that don't strictly need it, OpenAI's benchmark claims suggest Terra may be worth testing as a faster, cheaper substitute.

## How to use it

- Call it by model name (`gpt-6.1-terra`) through the `v1/responses` or `v1/chat/completions` API endpoints.
- ChatGPT Plus, Pro, Enterprise, and Edu users can access it directly in ChatGPT Work and Codex — no setup needed.
- Read OpenAI's [GPT-6 guide, GPT-6.1 Terra section](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-6-astra#gpt-61-terra) for prompting tips and migration guidance if you're switching from another model.
- Check the [model page](https://developers.openai.com/api/docs/models/gpt-6.1-terra) for exact pricing, rate limits, and context window size.

## Source

- [OpenAI API changelog — October 26, 2026](https://developers.openai.com/api/docs/changelog#october-26-2026)
- [OpenAI Community: GPT-6.1 Terra — delivering fast and capable computer use at a lower price](https://community.openai.com/t/gpt-6-1-terra-delivering-fast-and-capable-computer-use-at-a-lower-price/1409900)
