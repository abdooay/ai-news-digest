---
title: OpenAI built an AI that automatically attacks its own models to make them safer
date: 2026-07-19
description: OpenAI's new internal system, GPT-Red, finds prompt-injection weaknesses in its models faster than human testers and feeds the fixes back into training.
---

## What changed

On July 16, 2026, OpenAI described GPT-Red, an internal AI system built to automatically find "prompt injection" weaknesses in its models. Prompt injection is when hidden or disguised instructions — for example, buried in a webpage or document an AI is reading — trick the AI into ignoring its real instructions and doing something else instead.

GPT-Red works like a human security tester, often called a "red-teamer": it sends a prompt, watches how the target model responds, and adjusts its next attempt, repeating this many times. It's trained with self-play reinforcement learning, meaning an "attacker" version and a "defender" version of the system train against each other, and both sides improve over time.

OpenAI reports that GPT-Red beat human red-teamers on a new safety test: it succeeded at attacks 84% of the time, versus 13% for the human testers. The attacks GPT-Red finds are folded back into model training. OpenAI says this made its newest model, GPT-5.6, six times less likely to fail against direct prompt-injection attacks compared with the model it released four months earlier, and that GPT-5.6 Sol now fails on only about 0.05% of GPT-Red's own attacks.

## Why it matters

Prompt injection is one of the more serious real-world risks for AI systems that browse the web, read documents, or take actions on a person's behalf — a hidden instruction could make an AI leak data or do something the user never asked for. This isn't a product feature developers turn on; it's part of how OpenAI tests and trains its models before release. But it affects anyone using GPT-5.6 or later, since it means fewer prompt-injection failures out of the box. It's also a sign OpenAI is using its own models to find and fix safety weaknesses at a scale human testers can't match alone.

## How to use it

There's nothing to install or configure here — this is an internal safety and training process, not a public tool or API. If you build applications where a model reads untrusted content (web pages, emails, documents) and can take actions, it's still worth adding your own safeguards, such as limiting what actions a model can take automatically, since OpenAI's own reporting shows the model still fails on a small fraction of attacks.

## Source

- [GPT-Red: Unlocking Self-Improvement for Robustness (OpenAI)](https://openai.com/index/unlocking-self-improvement-gpt-red/)
