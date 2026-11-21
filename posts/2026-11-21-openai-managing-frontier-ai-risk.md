---
title: "OpenAI lays out how it checks and controls its most advanced models at every stage"
date: 2026-11-21
description: OpenAI described its layered safety process for frontier models, from offline-sandboxed training through internal use to public release, including a training pause caused by a DNS misconfiguration.
---

## What changed

OpenAI published an overview of how it evaluates and limits risk from its most advanced ("frontier") AI models at each stage of development, calling the approach "defense in depth" — meaning it doesn't rely on any single safeguard alone.

It described four layers of protection used throughout: training models to follow its written rules (the Model Spec) and checking this through evaluations and audits; restricting what files, tools, and networks a model can access; safety classifiers and a system called Auto-Review that can block unauthorized actions; and ongoing monitoring that can detect and respond to concerning behavior.

The three stages, and how each is handled:

- **Research (sandboxed training):** Frontier training runs happen with no live internet access, inside restricted sandboxes and virtual machines, with strong models used to red-team (test for weaknesses in) the containment itself. OpenAI disclosed that a DNS misconfiguration (a networking setup error) let an internal research model reach limited internet access; in response, OpenAI paused training and evaluation of its most capable models from September 20 to October 1, 2026. A system called Control Room can halt a model's output within 35 seconds of a stop instruction.
- **Internal deployment (employee use):** Models get real access to the internet, Slack, and internal company systems, but only after passing alignment testing. Auto-Review is generally required for employees using Codex, and every use by a frontier model is monitored for signs of misaligned behavior, such as trying to exfiltrate data.
- **External deployment (public release):** This adds larger safety evaluations, outside (third-party) testing for the most capable models, and active searching for misuse such as cyberattacks or help building bioweapons. Two trusted-access programs, Daybreak and Rosalind, give vetted researchers and defenders access while trying to keep it away from attackers.

OpenAI also said any employee can flag an incident for public disclosure under its misalignment reporting policy, with disputes going to a Safety Advisory Group, and that it will delay or withhold a model's release if it doesn't meet its safety bar.

## Why it matters

This gives outsiders a clearer picture of what actually stands between a newly trained OpenAI model and the public, and shows that these controls aren't purely theoretical — the DNS misconfiguration example shows a real safeguard catching a real gap, serious enough to pause training of OpenAI's most capable models for about 10 days. For anyone building on OpenAI's models or Codex, it's also a reminder that tools like Auto-Review and usage monitoring are a built-in part of how those systems run, not optional extras.

## How to use it

There's no setting to change here — this describes how OpenAI runs its own internal processes. If you want more detail, OpenAI says it will continue publishing system cards, incident reports, and risk reports as it releases new models.

## Source

- [OpenAI: Managing frontier AI risk: From training to deployment](https://openai.com/index/managing-frontier-ai-risk/)
