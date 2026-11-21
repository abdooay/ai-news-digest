---
title: "OpenAI's research shows AI coding agents are speeding up its own AI research, unevenly"
date: 2026-11-21
description: OpenAI's updated self-tracking report shows its coding agents now finish 46% of multi-hour research tasks on their own, up from 23% in March, with big gaps between task types.
---

## What changed

OpenAI published an update to a report it first released in September 2026 that tracks how much AI tools, mainly coding agents, are speeding up OpenAI's own work building AI. OpenAI calls this measuring "recursive self-improvement" (RSI) — AI helping build better AI — and says publishing this data is meant to let outsiders watch the trend, not an announcement that it intends to let AI fully run its own improvement.

Some key numbers from the report:

- On tasks estimated to take a skilled person 2 to 4 hours, AI agents working on their own now succeed 46% of the time, up from 23% in March 2026. On 4-to-8-hour tasks, success rose from 13% to 35%.
- Success varies a lot by task type: agents succeed 79% of the time monitoring training runs, but only 25% of the time writing the code that serves a trained model to users, and 29% building the test environments used to evaluate other AI systems. OpenAI says these weaker areas could become the bottleneck limiting further speedups.
- Researchers' spending on AI agents rose sharply: the typical (median) researcher spent about $2,400 a day on agentic AI in October, up 62% from September. The heaviest users (90th percentile) spent about $23,000 a day.
- The number of agent-days of work per researcher rose from 0.5 to 5.7 — an elevenfold increase — in the period measured. By mid-October, over two-thirds of researchers were running at least 4 AI agents at once at peak, and over 10% were running 16 or more at once.
- In a survey, researchers said that without current coding agents, their teams would need about three months to produce what they now produce in one month.
- Time spent on safety and alignment research rose 77% from January to September 2026 — the biggest increase of any research area — and OpenAI says this picked up after a security incident with Hugging Face in July 2026.

The report also notes that for its newest models (GPT-6 Astra and GPT-6.2 Astra), researchers say people still came up with the key ideas, with AI mostly helping to implement them — though some researchers said they developed ideas through conversations with Codex.

## Why it matters

This is OpenAI's own evidence that AI coding tools are measurably speeding up how fast it can build and test new AI models — not just writing boilerplate code, but running experiments, debugging, and scanning large amounts of data. The uneven results matter too: tasks requiring judgment, like deciding what to test or writing clearly, still lean heavily on humans, while routine, well-defined tasks are increasingly automated. That unevenness is why OpenAI calls this a "jagged frontier" rather than a smooth takeover by AI.

## How to use it

This is a research and transparency report, not a product. There's nothing to install or configure. If you're a researcher or policy-watcher, the practical value is in the numbers themselves — they're a rare public look at how fast an AI lab's own output is being reshaped by AI tools, and OpenAI says it plans to keep publishing updates.

## Source

- [OpenAI: Research acceleration: The jagged frontier](https://openai.com/index/research-acceleration-jagged-frontier/)
