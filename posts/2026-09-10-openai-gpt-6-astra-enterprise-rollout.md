---
title: "GPT-6 Astra a week in: enterprise admin controls, new plugins, and benchmark numbers"
date: 2026-09-10
description: A week after launch, OpenAI adds enterprise admin controls and desktop plugins for GPT-6 Astra, and publishes workplace-safety and cost-efficiency benchmark numbers.
---

## What changed

OpenAI launched GPT-6 Astra on September 3, 2026, and covered its safety testing in follow-up documents shortly after (both covered in earlier posts). On September 9, 2026, OpenAI published an update on how Astra is being used in ChatGPT Work and Codex, about a week into rollout:

- **New enterprise admin controls**: organizations can now restrict which websites and desktop apps Astra can access, and manage its file uploads/downloads and browsing history.
- **New enterprise plugins** for ChatGPT Desktop, connecting to Oracle Analytics, Microsoft's Power BI, Navan, and Avalara. OpenAI says these use the model's browser-use ability to work with apps that don't have a direct API.
- **A workplace safety benchmark result**: on an internal test of risky business scenarios (such as leaking confidential data, oversharing a dashboard, or deleting files), OpenAI says Astra produced unwanted outcomes 89% less often than GPT-5.6 Sol, and 74.7% less often than Anthropic's Claude Fable 5.1.
- **A coding benchmark result**: on Terminal-Bench 4.0 (a benchmark for terminal-based coding and admin tasks), OpenAI reports Astra scores 57.9%, versus 37.3% for GPT-5.6 Sol and 55.8% for Claude Fable 5.1 — at a lower estimated API cost per task than either.
- OpenAI also shared an internal example: its own engineering team used Astra to find and fix a memory-allocation bug that was slowing down Codex sessions, cutting turn latency 25x by switching allocators (at the cost of about 30% more peak memory use).

## Why it matters

The admin controls matter most for IT and security teams: before this update, organizations deploying Astra in ChatGPT Work had less ability to restrict exactly which sites, apps, and data flows the model could touch. Being able to limit access up front, then expand it gradually, is a more cautious way to roll out a model OpenAI itself has classified as having "Critical" cybersecurity capability (see our earlier post on that).

The benchmark numbers are self-reported by OpenAI and should be read as marketing claims, not independent verification — but they're still useful data points if you're comparing Astra against GPT-5.6 Sol or Claude Fable 5.1 for coding or business-automation work, since OpenAI is explicitly claiming both a safety and a cost advantage over both.

## How to use it

- The new admin controls (restricting sites, apps, uploads/downloads, browsing history) are configured through your organization's ChatGPT Work / Enterprise admin settings.
- The new plugins (Oracle Analytics, Power BI, Navan, Avalara) are added the same way as other ChatGPT Desktop plugins, from your workspace's plugin settings.
- No action is needed to get the benchmark improvements — they describe the model's existing behavior, not a setting to turn on.

## Source

- [OpenAI: GPT-6 Astra: The next generation in intelligence for work](https://openai.com/index/gpt-6-astra-next-generation-work/)
