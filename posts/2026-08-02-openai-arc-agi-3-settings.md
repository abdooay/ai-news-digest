---
title: Two API settings tripled GPT-5.6's score on a hard benchmark
date: 2026-08-02
description: OpenAI found that its evaluation harness was quietly crippling GPT-5.6's performance on ARC-AGI-3 — turning on two API settings fixed it.
---

## What changed

OpenAI investigated why GPT-5.6 Sol scored poorly (7.8%, later reported as 13.3% under the official harness) on ARC-AGI-3, a benchmark of 2D puzzle games, despite the same model being able to solve hard math problems elsewhere. OpenAI found the problem wasn't the model — it was the test setup.

The standard benchmark harness (the code that feeds tasks to the model and manages its context) was doing two things that hurt performance:

- After each move in the puzzle game, it threw away the model's private reasoning (its internal step-by-step thinking from the previous move), forcing the model to re-figure out the situation from scratch every turn.
- Once the conversation history passed 175,000 characters, it deleted older parts to make room, so the model lost track of things it had already learned about the puzzle.

OpenAI reran the benchmark using its Responses API (its newer API for building agents) with two settings turned on:

- **Retained reasoning** — keeps the model's private reasoning from previous turns instead of deleting it, which is how the model already behaves inside ChatGPT and Codex.
- **Compaction** — summarizes older parts of the conversation instead of just cutting them off, so earlier information isn't lost outright.

With both settings on, GPT-5.6 Sol's score rose to 38.3%, using about 6 times fewer output tokens per game than before. For comparison, OpenAI says the estimated human baseline on this benchmark is around 48%.

## Why it matters

This is a useful case study, not just a benchmark flex: it shows that how you configure a model's API calls — specifically, whether it keeps its own reasoning and how it handles a growing conversation — can matter as much as the model itself for multi-step, agentic tasks. It's also a caution for reading AI benchmark leaderboards: a low score might reflect a harness limitation rather than the model's real capability, and comparing scores across providers is only fair if everyone's harness handles context the same way.

## How to use it

- If you're building an agent that works over many steps (like a game-playing or long multi-step task), use OpenAI's Responses API rather than the older Chat Completions API, since it's the one that supports these settings.
- Turn on reasoning retention so the model doesn't lose its own prior thinking between steps — OpenAI says this happens automatically when you pass previous response IDs through the Responses API.
- Use compaction (context summarization) instead of hard truncation when your conversation history grows past the model's limit, so older but still-relevant information isn't simply deleted.

## Source

- [OpenAI: "How enabling two settings tripled our scores on the ARC-AGI-3 benchmark"](https://openai.com/index/how-two-settings-tripled-our-arc-agi-3-scores/)
