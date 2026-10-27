---
title: "OpenAI releases GPT-6.1 Terra"
date: 2026-10-27
description: OpenAI released GPT-6.1 Terra, a fast, efficient model aimed at visual reasoning, precise computer use, and natural writing.
---

## What changed

OpenAI released a new model called **GPT-6.1 Terra** on October 26, 2026. According to OpenAI's API changelog, it's described as "a fast, efficient model for visual reasoning, precise computer use, and clear, natural writing."

It's available through OpenAI's two main API endpoints: `v1/responses` and `v1/chat/completions`. OpenAI published a model guide with prompting and migration advice for developers moving from an earlier model to GPT-6.1 Terra.

OpenAI's changelog entry does not give pricing, context window size, or benchmark numbers for this release.

## Why it matters

"Visual reasoning" and "precise computer use" both point to a model meant for agents that look at a screen and act on it — reading an image or screenshot and deciding what to click or type, for example. If you're building an agent that needs to interact with a graphical interface, or process images as part of its reasoning, GPT-6.1 Terra is now an option. Being described as "fast, efficient" suggests OpenAI is positioning it as a cheaper or quicker alternative to a larger flagship model for these tasks, though OpenAI didn't publish pricing details in this changelog entry.

## How to use it

- Call it by model name (`gpt-6.1-terra`) through the `v1/responses` or `v1/chat/completions` API endpoints.
- Read OpenAI's [GPT-6 guide, GPT-6.1 Terra section](https://developers.openai.com/api/docs/guides/latest-model?model=gpt-6-astra#gpt-61-terra) for prompting tips and migration guidance if you're switching from another model.
- Check the [model page](https://developers.openai.com/api/docs/models/gpt-6.1-terra) for the latest specs, since pricing and context window details weren't included in the changelog entry itself.

## Source

- [OpenAI API changelog — October 26, 2026](https://developers.openai.com/api/docs/changelog#october-26-2026)
