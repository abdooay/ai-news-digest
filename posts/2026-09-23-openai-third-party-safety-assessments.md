---
title: OpenAI commits to deeper, ongoing outside safety testing of its models
date: 2026-09-23
description: OpenAI published its principles for letting outside groups test its models for safety risks throughout training and deployment, not just before launch.
---

## What changed

On September 22, 2026, OpenAI published "Priorities and principles for effective third party assessments," setting out how it will let outside organizations test its AI models for safety. The shift is from one-off benchmark checks to what OpenAI calls "sustained, trusted access" — letting external assessors examine models across training, evaluation, and deployment, rather than only reviewing a finished model right before release.

OpenAI names three kinds of outside work it supports:
- **Independent evaluations** — outside groups measuring a model's capabilities and the risks that come with them.
- **Methodology reviews** — outside groups checking whether OpenAI's own safety testing is designed well.
- **Subject-matter expert probing** — specialists testing specific risk areas using their own domain expertise.

To do this, assessors get access that OpenAI describes as beyond what a typical customer gets: secure access to early, unreleased model versions and some evaluation results; "zero-data-retention" testing setups with fewer safety restrictions in place, so the model can be examined more freely under controlled conditions; and, under strict security controls, direct access to a model's chain-of-thought — the step-by-step reasoning text it produces internally before answering. OpenAI says this is specialized access for assessment work, not something regular customers should expect to get.

Groups that have previously published this kind of work on OpenAI's models include METR, Apollo Research, and Irregular. The risk areas OpenAI says are being tested include long-horizon autonomy (a model acting on its own over many steps), scheming and deception, attempts to evade human oversight, biological "wet lab" planning feasibility, and offensive cybersecurity capability.

## Why it matters

Independent testing is a check on a company grading its own homework — outside experts are more likely to catch blind spots or downplayed risks than a team testing its own product. Giving assessors access to chain-of-thought and pre-release checkpoints is a meaningfully deeper level of access than a typical red-teaming exercise done just before launch.

OpenAI is explicit about the limits, though: this kind of assessment gives "additional risk context" about a model in general, but it can't tell a specific business whether their own use of that model — a particular support workflow or automated decision process — is safe for their situation. That judgment still falls on whoever deploys the model.

## How to use it

This is a policy and process change at OpenAI, not a tool or setting you configure. There's nothing for developers to turn on. If you're a safety researcher or organization that does this kind of independent assessment work, OpenAI's announcement is the place to look for how to get involved.

## Source

- [Priorities and principles for effective third party assessments](https://openai.com/index/priorities-principles-third-party-assessments/)
