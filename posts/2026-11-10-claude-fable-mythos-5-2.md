---
title: "Claude Fable 5.2 and Mythos 5.2: faster, fewer false safety blocks"
date: 2026-11-10
description: Anthropic's new Fable 5.2 and Mythos 5.2 models are the same underlying model, run about 30% faster than 5.1, and trigger far fewer unnecessary safety refusals.
---

## What changed

On November 9, 2026, Anthropic released Claude Fable 5.2 and Claude Mythos 5.2. Fable and Mythos are "the same underlying model," according to Anthropic — the difference is who can use them. Fable (`claude-fable-5-2`) is open to everyone, with stronger built-in cybersecurity and biology safeguards. Mythos (`claude-mythos-5-2`) has the same capabilities but is only available to organizations vetted through Anthropic's Cyber and Life Sciences Verification Programs.

Compared with the 5.1 versions, Anthropic reports:
- Outputs up to 30% faster.
- Improvements in coding, reasoning, and vision.
- About 55% fewer unnecessary safety blocks (roughly 60% fewer in cybersecurity contexts, 40% fewer in biology).
- Fable 5.2 reportedly uses fewer tokens at "Medium" reasoning effort, which is the default in Claude apps and Claude Code.

Both models have a 1-million-token context window, a 128,000-token maximum output, and reasoning ("thinking") turned on by default at all times. Both are priced at $8 per million input tokens and $40 per million output tokens. An optional "fast mode" costs more ($16/$80 per million tokens) but delivers up to 2.5x higher output speed; fast mode is available for Fable 5.2 on the Claude API, Claude Code, the Claude Platform, Google Cloud, and Microsoft Foundry (Mythos fast mode is restricted to verified organizations).

A few technical details for API users:
- Both models require 30-day data retention and aren't available with zero data retention unless Anthropic specifically authorizes it.
- "Thinking" blocks (the model's internal reasoning) these models produce only work in the account that generated them, or a linked account.
- They use a new computer-use toolset, `computer_toolset_20260801`. The older `computer_20251124` tool now returns an error on every platform except Amazon Bedrock.
- A new "Advisor" feature (beta) lets one model consult another on hard problems. Every advisor-capable model accepts Fable 5.2 as an advisor, but Fable 5.2 or Mythos 5.2 themselves will only accept each other as advisors.

## Why it matters

The big practical change for developers who already use Fable or Mythos is speed and fewer refused requests: a ~30% speed gain plus a big drop in over-triggered safety blocks means fewer retries and less time spent working around the model declining legitimate requests. That matters most for cybersecurity and biology-related work, where Anthropic says the refusal rate dropped the most.

Anthropic still recommends starting most coding and knowledge work with the mid-tier Claude Opus 5.5, and only reaching for Fable or Mythos on the hardest, most open-ended tasks — these are the most expensive, highest-effort models in the lineup, not a blanket upgrade.

The Mythos access restriction is worth knowing about if you work in cybersecurity or life sciences research: you need to go through Anthropic's verification programs first, and some features (like Mythos fast mode) are gated even further behind that.

## How to use it

- Switch to Fable 5.2 by requesting the model ID `claude-fable-5-2` on the Claude API, or picking it in Claude Code or claude.ai.
- Turn on fast mode by setting `speed: "fast"` in your API request — no beta header needed. Expect roughly double the price per token in exchange for faster output.
- If you rely on computer use, update to the `computer_toolset_20260801` tool definition; the old `computer_20251124` tool will now fail outside Amazon Bedrock.
- If you need Mythos access for cybersecurity or life sciences work, apply through Anthropic's Cyber Verification Program or Life Sciences Verification Program.
- Subscribers on eligible Claude plans get one to three free "Fable resets" depending on subscription length, and Fable is included for up to 50% of weekly usage limits on Pro and standard Team seats.

## Source

- [Anthropic: Introducing Claude Fable 5.2 and Claude Mythos 5.2](https://www.anthropic.com/claude-fable-and-mythos-5-2)
- [Claude Platform release notes — November 9, 2026](https://platform.claude.com/docs/en/release-notes/overview)
