---
title: "OpenAI Presence: a managed product for running AI agents in production"
date: 2026-07-22
description: OpenAI launched Presence, a managed enterprise product for deploying AI voice and chat agents that can use company systems and take approved actions.
---

## What changed

On July 22, 2026, OpenAI introduced Presence, a product for enterprises that want to run AI agents in production for things like customer support, sales, and internal help-desk work, across both voice and chat.

Presence is not just a model. It bundles together the pieces a company needs to run an agent reliably: written policies and procedures for the agent to follow, guardrails that can step in when a conversation goes outside allowed bounds, a list of "approved actions" the agent is allowed to take, testing tools (simulations and evaluations) to check behavior before launch, and an improvement loop powered by Codex (OpenAI's coding-agent system) that reviews real production conversations and proposes fixes.

Each deployment is scoped to one specific job — for example, resolving a billing issue or an insurance claim, or handling an internal IT request. The agent only gets access to the systems and information needed for that job, and the company decides what the agent can do on its own, when it needs approval, and when it should hand off to a person.

OpenAI says Presence already powers its own English-language phone support line, where it resolves 75% of inbound calls without a human, and where the Codex-based improvement loop cut human handoffs by 15 percentage points in 10 days. Early customers named in the announcement include BBVA Mexico (voice banking support), SoftBank Corp. (Japanese-language customer service), and IAG's Retail Insurance Australia (support during high-demand events like severe weather).

## Why it matters

Companies have already been able to build chat and voice agents on top of OpenAI's models. What's new here is that OpenAI is packaging the surrounding work — policy enforcement, testing, monitoring, and ongoing fixes — as a product, rather than leaving it to each company to build. That's a bet that the hard part of production AI agents isn't the model anymore, it's everything around it: keeping the agent's behavior predictable as products and policies change.

For now, this only matters directly if you're a large enterprise, since it's not self-serve.

## How to use it

Presence is available today, but only through a limited general-availability program — it is **not** self-service. Deployments are led by OpenAI's own Forward Deployed Engineers or selected systems integrators. If you want to explore it, OpenAI says to contact your OpenAI account team. If you just want API access to OpenAI's models for your own voice or chat agent, that continues to be available separately through the standard OpenAI API.

## Source

- [Introducing OpenAI Presence](https://openai.com/index/introducing-openai-presence/)
