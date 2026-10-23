---
title: "OpenAI's Decisions API reaches general availability"
date: 2026-10-23
description: OpenAI's Decisions API, a tool for classifying or routing large batches of items, is now generally available on gpt-6-luna with caching, image inputs, and a higher per-request limit.
---

## What changed

OpenAI's Decisions API moved from public beta to general availability on October 22, 2026, running on the `gpt-6-luna` model. The Decisions API is built for answering a specific question about many items at once — for example, labeling or routing a large batch of pieces of content.

Changes that come with general availability:
- Shared input (context used across many requests) can now be cached, which gets a prompt-cache discount.
- Individual question instructions can include images, not just text.
- Structured data can be passed directly using a new `input_json` parameter, instead of needing to be converted to text first.
- Each request can now include up to 400 questions, up from 200 during the public beta.

OpenAI's documentation includes a "changes since public beta" section in the Decisions guide listing the full set of differences.

## Why it matters

If you were using the Decisions API during its public beta, general availability means it's now meant for production use, and the caching support should lower cost for workloads that reuse the same shared context across many questions. The jump from 200 to 400 questions per request and the ability to pass images or structured JSON directly reduce the amount of pre-processing needed to use the API for larger or more varied classification jobs.

## How to use it

- If you're already using the Decisions API in beta, check the "changes since public beta" section of the Decisions guide for anything that affects your integration.
- Use the new `input_json` parameter to pass structured data directly instead of converting it to text.
- Include images in individual question instructions where that's useful for your classification task.
- Batch up to 400 questions per request instead of 200.

## Source

- [OpenAI API changelog — October 22, 2026](https://developers.openai.com/api/docs/changelog)
