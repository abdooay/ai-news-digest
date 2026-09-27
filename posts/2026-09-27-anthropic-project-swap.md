---
title: "Anthropic tests AI agents trading on people's behalf"
date: 2026-09-27
description: In an internal experiment called Project Swap, Claude agents negotiated book trades for 201 employees — and preference understanding, not negotiating skill, was the main bottleneck.
---

## What changed

On September 24, 2026, Anthropic published "Project Swap: What happens when agents trade for us?" — a follow-up to an earlier experiment called Project Deal. In it, 201 Anthropic employees across six offices each brought in a book they wanted to give away. Each person had a short (around five-minute) chat with a Claude model about what they like to read, and then a Claude-powered agent went onto a shared digital "trading floor" to pitch, haggle, and strike book-swap deals with other people's agents — without further input from the human.

The intake conversations mainly used Claude Fable 5, and the trading agents were built on a range of models: Claude Haiku 4.5, Sonnet 4.5, Opus 4.8, and Fable 5.

Key results:
- From just a five-minute chat, an agent's ranking of books matched its own person's ranking on 61% of book pairs — better than guessing randomly (50%) or just picking generally popular books (53%).
- On average, people ended up with a book ranked about 0.55 out of a possible 1.0 on their personal preference scale (roughly their 5th choice out of the pool), versus a theoretical best-possible outcome of 0.89.
- Anthropic attributes about 85% of that shortfall to the agent not fully understanding the person's preferences, and only about 15% to imperfect trading/negotiating.
- Stronger models did better as traders: agents built on Haiku averaged 0.75 on the outcome scale, while agents built on Opus averaged 0.88 — model quality mattered more than how the agent's instructions were written.
- Average participant satisfaction was 7.2 out of 10. About 30% of participants said they'd trust an agent with their whole year's book budget; about 40% said they'd trust a well-read friend to do the same.

## Why it matters

This is a useful, concrete look at what limits "agents acting on your behalf" in a real marketplace: it's not the negotiating itself that's hard for current models, it's correctly figuring out what the person actually wants from a short conversation. Anthropic argues that as more agent-to-agent commerce shows up in the real world, businesses and platform designers will need ways to verify that an agent truly represents its human's interests, clear rules about agent identity and how disputes get resolved, and privacy protections that still allow enough transparency to check an agent's behavior.

## How to use it

This was an internal research experiment, not a product release, so there's nothing to enable or configure. It's a signal for anyone building AI shopping, negotiating, or trading agents: invest in gathering and checking user preferences accurately, since that — more than clever negotiation prompting — is likely to be the main limiting factor.

## Source

- [Project Swap: What happens when agents trade for us?](https://www.anthropic.com/research/project-swap)
