---
title: "Anthropic publishes measurements of how fast AI development is moving inside its own labs"
date: 2026-09-18
description: Anthropic released three internal metrics tracking how much of its own AI research is now done by Claude instead of humans, and how well it can monitor autonomous AI agents.
---

## What changed

Anthropic published a set of internal measurements meant to show, with actual numbers, how quickly AI development is moving inside a frontier AI lab. There are three of them:

- **AI-led R&D automation**: how much of Anthropic's own research and development work is done by Claude rather than by people. Anthropic scores this on a scale from AL0 (no AI involvement) to AL5 (fully autonomous). As of August 2026, Claude "leads" about 26% of Anthropic's AI R&D work, up from under 1% in February 2026. Claude is not yet operating fully autonomously.
- **AI agent oversight**: how well Anthropic can monitor and step in on actions taken by its own autonomous AI agents running on internal systems. It's tracked with three numbers: how much of agent activity is monitored (coverage), how fast flagged activity gets reviewed (review latency), and how often actions get blocked or flagged (escalation rate). Anthropic says about 30,000 agents were running at once on its main internal platform, and automated monitors blocked about 0.002% of agent decisions — roughly 1 in 47,000.
- **Compute allocation**: how Anthropic splits its computing power between safety research and other R&D. About 6% of all AI R&D compute went to safety work; that rises to 12% when looking only at compute used by AI systems themselves (as opposed to humans).

To build the automation number, Anthropic surveyed a sample of about 20% of relevant staff, catalogued roughly 15,000 specific tasks, organized them into a tree with 542 categories, and had Claude estimate automation levels for each one, which humans then checked.

## Why it matters

Normally, only people inside an AI lab know how much of its own research is being automated by its own models, or how well it can supervise autonomous agents running on its systems. Anthropic is publishing these numbers so outsiders — researchers, policymakers, other labs — have some real data instead of guesses. Anthropic suggests these kinds of measurements could eventually be used as triggers for safety-related rules, or compared across different AI companies if the methodology becomes standard. The 26%-and-rising automation figure is also a concrete signal of how fast Claude is being folded into Anthropic's own research process.

## How to use it

This isn't a product change, so there's nothing to install or configure. If you follow AI policy or safety research, the source page has the full methodology and numbers, including how the task tree was built and how the compute classifier worked.

## Source

- [Measurements for understanding the pace of AI development inside frontier labs](https://www.anthropic.com/institute/measuring-pace-of-ai-development)
