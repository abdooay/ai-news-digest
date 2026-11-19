---
title: "OpenAI launches GPT-6.2 Astra and GPT-6.2 Sol"
date: 2026-11-19
description: OpenAI released two new models, GPT-6.2 Astra and GPT-6.2 Sol, in ChatGPT Work, Codex, and the API, with Astra cutting cost per task to under a third of GPT-6 Astra.
---

## What changed

OpenAI announced, on November 17, 2026, that two new models are now available: **GPT-6.2 Astra** and **GPT-6.2 Sol**.

- **Availability:** Both are live in ChatGPT Work and Codex for Plus, Pro, Enterprise, and Edu subscribers, and developers can call them through the OpenAI API as `gpt-6.2-astra` and `gpt-6.2-sol`.
- **Ultrafast (a faster response mode):** Pro 500 subscribers can use Ultrafast with either model. Pro 200 subscribers get Ultrafast for the first time, starting with GPT-6.2 Sol. Ultrafast is also available through the API.
- **GPT-6.2 Astra** is described as a frontier model (OpenAI's top tier) for harder, professional and scientific work. OpenAI says it sets new highs on its evaluations across professional work and scientific research, at less than a third of the cost per task compared to the earlier GPT-6 Astra. On an internal benchmark called "Agents' Last Exam," OpenAI says 6.2 Astra (run at its "xhigh" effort setting) scores 5.2 points above GPT-6 Astra (run at "max" effort), at less than half the cost per task. OpenAI also calls it its most capable model yet for cybersecurity tasks, citing a 22-point jump over GPT-6 Astra on an internal benchmark called "ExploitBench Internal Port."
- **GPT-6.2 Sol** is described as an efficient, everyday-work model, good at multi-step agentic tasks (where the model takes a series of actions on its own) and at writing clearly. On a coding benchmark called "FrontierCode 2.0," OpenAI says Sol nearly matches Astra's rate of producing merge-ready code changes, at about one-fifth the cost.
- **Pricing (API, per million tokens):** GPT-6.2 Astra costs $8.00 for input and $40.00 for output. GPT-6.2 Sol costs $2.00 for input and $10.00 for output.
- **Safety:** Because of their increased cybersecurity-related capability, OpenAI says it is launching both models with tighter safeguards for higher-risk cybersecurity assistance, and is working to bring them to its "Daybreak" program so that vetted defenders can use them with fewer refusals.

All of the benchmark numbers above (Agents' Last Exam, ExploitBench, FrontierCode 2.0) are OpenAI's own internal results, not independently verified figures.

## Why it matters

If you're a developer or ChatGPT subscriber already using GPT-6 Astra or GPT-6.1 Sol, these are direct upgrades: OpenAI is claiming better quality at meaningfully lower cost, which matters a lot for anyone running agentic workflows (automated, multi-step tasks) where API costs add up quickly. The cybersecurity capability jump — and the accompanying safeguards — signal that OpenAI sees these models as strong enough at exploit-related tasks to warrant extra restriction, which is worth knowing if you build security tooling on top of OpenAI's models.

## How to use it

- In ChatGPT Work or Codex, the new models should already be selectable if you're on a Plus, Pro, Enterprise, or Edu plan.
- Through the API, call them by their model names: `gpt-6.2-astra` or `gpt-6.2-sol`.
- To use Ultrafast, you need a Pro 500 subscription (either model) or a Pro 200 subscription (GPT-6.2 Sol only for now), or request it via the API.
- Check current API pricing against your usage before switching production workloads, since Astra and Sol have different cost profiles ($8/$40 vs. $2/$10 per million tokens for input/output).

## Source

- [OpenAI — Introducing GPT-6.2 Astra and Sol](https://openai.com/index/introducing-gpt-6-2-astra-sol)
- [OpenAI Community — GPT-6.2 Astra and Sol are now available](https://community.openai.com/t/gpt-6-2-astra-and-sol-are-now-available/1417531)
