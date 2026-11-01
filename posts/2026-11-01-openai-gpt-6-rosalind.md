---
title: OpenAI releases GPT-6 Rosalind for life sciences research
date: 2026-11-01
description: OpenAI's new GPT-6 Rosalind model adds specialized biological reasoning, but it's only available to approved research organizations.
---

## What changed

On October 30, 2026, OpenAI released GPT-6 Rosalind, a model built for biology research. OpenAI says it adds "specialized biological reasoning" and scientific tool use, aimed at complex life sciences research.

Access is restricted. OpenAI only gives it to organizations approved for "Rosalind Research" through what it calls the trusted-access program, and only for internal research by people it has authorized. This isn't a model the average developer can just sign up and use.

OpenAI's pricing page also lists two smaller models in the same family, `gpt-rosalind-research` and `gpt-rosalind-discovery`, priced lower than the main model. The changelog entry itself only announces GPT-6 Rosalind as the new release.

## Why it matters

Most AI model releases are open to any developer with an API key. GPT-6 Rosalind is different: it's a gated, specialist tool for vetted research organizations working on biology problems, not a general-purpose model. If your work isn't in that approved research category, this release doesn't change anything for you.

For the research organizations that do get access, it's a sign OpenAI is building separate, narrower models for scientific domains rather than relying only on its general-purpose GPT-6 line.

## How to use it

You can't just start calling this model. OpenAI's process, per its documentation:

1. Your organization needs to be approved for "Rosalind Research" through OpenAI's trusted-access program.
2. Access is for internal research by users your organization has authorized — it's not opened up broadly.
3. Pricing (per 1 million tokens, standard tier): `gpt-6-rosalind` costs $15.00 for input and $75.00 for output, with cached input at $1.50. For prompts longer than 272,000 tokens, input rises to $30.00 and output to $112.50 per million tokens.

## Source

- [OpenAI API changelog, October 30, 2026 entry](https://developers.openai.com/api/docs/changelog)
- [OpenAI API pricing: life sciences models](https://developers.openai.com/api/docs/pricing#life-sciences-models)
