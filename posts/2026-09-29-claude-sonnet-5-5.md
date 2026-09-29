---
title: Anthropic launches Claude Sonnet 5.5
date: 2026-09-29
description: Claude Sonnet 5.5 is a big capability jump over Sonnet 5 at the same price, and it's now the default Sonnet model everywhere.
---

## What changed

Anthropic released Claude Sonnet 5.5 on September 28, 2026. It replaces Claude Sonnet 5 as the default Sonnet model. The model ID is `claude-sonnet-5-5`.

Anthropic reports large jumps on its own benchmarks:
- **Terminal-Bench 4.0** (a test of using a command-line terminal to complete tasks): 70.6%, up from Sonnet 5's 10.3%.
- **GDPval-AA v2.1** (a test of real-world knowledge work quality): 1844, up from Sonnet 5's 1449 — close to Opus 5.5's 1846.
- **OSWorld 2.1** (a test of operating a computer through its screen): 80.1%.
- **Humanity's Last Exam**, using tools: 64.5%.

Output generation is over 30% faster than Sonnet 5. Anthropic says the speed and quality gains together mean a typical task costs up to 30% less to run, even though the per-token price hasn't changed.

The model also ships with the same class of safety measures introduced with Opus 5.5: cybersecurity safeguards that limit high-risk uses (routine bug-fixing and development still work normally), biology-related safeguards that mostly don't affect normal research or clinical use, and — new for a Sonnet model — classifiers meant to stop someone from using Sonnet 5.5's outputs to train ("distill") a rival model by extracting its reasoning.

## Why it matters

Sonnet models are the ones most people and companies use day to day, because they're cheaper and faster than Opus. Getting Sonnet 5.5 this close to Opus 5.5 on real-work benchmarks, without raising the price, means many teams can now do more with the cheaper model instead of paying for the top-tier one.

Companies already testing it report concrete gains. Zendesk said support tickets were processed 20% faster. Atlassian said its Rovo Agents run up to 30% faster. Slack said Sonnet 5.5 beat Sonnet 5 on almost all of its internal chatbot tests without changing any prompts — meaning existing setups can benefit without rework.

## How to use it

- Set your model to `claude-sonnet-5-5` in the Claude API (Anthropic calls it the Claude Platform) to start using it — it's already the default for new sessions that don't pin a specific model.
- Pricing is unchanged from Sonnet 5: $2 per million input tokens, $10 per million output tokens, $0.20 per million tokens for cache reads, $2.50 per million for cache writes.
- It's available today on the Claude Platform, Amazon Web Services (Bedrock), Google Cloud (Vertex AI), and Microsoft Azure (Foundry), as well as in the Claude apps and Claude Code.
- Claude Code v2.1.284 (released the same day) made Sonnet 5.5 its default model, with 1M-token context support.

## Source

- [Claude Sonnet 5.5](https://www.anthropic.com/claude-sonnet-5-5)
- [Claude API release notes — September 28, 2026](https://platform.claude.com/docs/en/release-notes/api#september-28-2026)
