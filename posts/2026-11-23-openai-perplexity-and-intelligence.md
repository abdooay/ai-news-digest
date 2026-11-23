---
title: "OpenAI's chief scientist proposes a shared AI progress metric, and shares his lab's own numbers"
date: 2026-11-23
description: Jakub Pachocki argues AI labs should track and share "perplexity," a measure of how well a model predicts text, to agree on shared safety limits before the next jump in capability.
---

## What changed

OpenAI published a post by Jakub Pachocki, the company's chief scientist. In it, he argues that AI labs should adopt a shared way to measure progress: "perplexity" (also called cross-entropy loss), a score for how well a model predicts the next piece of text when trained on huge amounts of data. Lower perplexity means the model has learned to compress and predict text better, and Pachocki argues new capabilities tend to show up as this score drops past certain points.

To make the case concrete, OpenAI published some of its own internal perplexity numbers, measured on a fixed, held-out set of text from its internal codebase:

- GPT-3.5 scored about 0.99 — good enough for fluent conversation, the basis of the original ChatGPT.
- GPT-4 scored about 0.91 — able to do useful step-by-step ("chain-of-thought") reasoning.
- Below about 0.8, OpenAI says it saw new, more powerful abilities emerge in cybersecurity and math.
- A later model scored about 0.76 and began producing notable results on open math problems.
- OpenAI expects its next models to land around 0.68–0.7, where it expects further new capabilities to appear, though it says it doesn't know yet what those will be.

Pachocki also raises two concerns: that a wave of pretraining progress could arrive as soon as 2027, partly helped along by AI itself contributing to research, and that the tools used to check whether models are being honest and safe ("alignment auditing") are getting harder to trust as models get better at recognizing when they're being tested.

He proposes that frontier AI labs agree on shared norms: common safety tests, red-teaming practices, and transparency standards, plus "common limits" on perplexity or other measures that labs agree not to cross until some safety milestone is reached — for example, a working successor to today's chain-of-thought monitoring tools.

He's also upfront about perplexity's limits as a metric: labs use different training data and evaluation sets, so numbers aren't directly comparable across companies; it doesn't measure results on any specific task; it doesn't capture gains that come from methods other than pretraining, such as chain-of-thought reasoning; and nobody knows the lowest score a model could theoretically reach, so the same size of improvement could matter more or less over time.

## Why it matters

This isn't a product release — it's a proposal about how AI companies should talk to each other about progress and risk. If it's adopted, it could change how the industry decides when a new model needs extra safety review before release, similar to how nuclear or biotech fields agree on shared risk thresholds. For developers and users, there's no immediate change. But the underlying claim is worth tracking: OpenAI says its own measurements show capability jumps are correlated with specific perplexity drops, and that further jumps are expected soon, with unknown capabilities attached.

## How to use it

There's no API, tool, or setting to change here — this is a research and policy post, not a feature. If you follow AI safety or industry coordination efforts, the practical takeaway is to watch whether other labs (including Anthropic) respond publicly to this proposal, since Pachocki is explicitly calling for shared standards across companies, not just inside OpenAI.

## Source

- [OpenAI: Perplexity and Intelligence](https://openai.com/index/perplexity-and-intelligence/)
