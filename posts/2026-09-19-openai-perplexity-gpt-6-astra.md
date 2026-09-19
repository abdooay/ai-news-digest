---
title: "Perplexity says GPT-6 Astra needs less oversight for automated testing and production monitoring"
date: 2026-09-19
description: Perplexity's Johnny Ho says GPT-6 Astra can generate realistic mock responses for testing and monitor production systems reliably enough to check in on it less often than with earlier models.
---

## What changed

Perplexity, the AI-powered search company, described how it uses GPT-6 Astra (OpenAI's model, accessed through the API) internally. Johnny Ho, Perplexity's co-founder and Chief Strategy Officer, said the model is used to draft communications, make direct edits to live systems, and monitor production software — tasks earlier model generations weren't reliable enough for.

One specific use case: automated testing. Ho said GPT-6 Astra can generate realistic mock responses that simulate what external services would return, letting Perplexity's team test applications thoroughly without manually writing those mock responses by hand.

Ho said the model was reliable enough that the team could "trust it with full end-to-end systems and check in on it much less frequently than previous generations of models" — meaning less manual oversight was needed to catch mistakes.

## Why it matters

Using an AI model to monitor and act on production systems (the live software actually serving users) is a higher-trust use case than drafting text or answering questions — mistakes there can cause real outages or bad data. Perplexity reporting reduced need for human oversight is a signal of growing confidence in agentic reliability for backend engineering tasks, at least for one company. As with any single company's account, this reflects Perplexity's own experience and testing standards, not an independent benchmark.

## How to use it

This describes Perplexity's internal engineering use of the GPT-6 Astra model via OpenAI's API — there's no new tool or setting introduced here. Teams interested in similar use cases (automated test-mock generation, production monitoring) would build them on GPT-6 Astra through the standard OpenAI API.

## Source

- [Perplexity trusts GPT-6 Astra with end-to-end systems](https://openai.com/index/perplexity-improving-accuracy-with-astra)
