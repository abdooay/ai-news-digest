---
title: "OpenAI's proposed scorecard for AI spending: \"useful intelligence per dollar\""
date: 2026-07-22
description: OpenAI leadership proposes measuring AI investment by useful work done, true cost per task, accuracy, and how those numbers change with scale, instead of by adoption rates.
---

## What changed

OpenAI published a framework for how organizations should judge whether their AI spending is paying off, arguing that standard software metrics — like how many people adopted a tool — don't capture what matters for AI. The proposed central measure is "Useful Intelligence per Dollar," broken into four parts:

1. **Useful work accomplished** — track concrete outcomes inside a specific workflow, such as customer issues resolved by a support workflow or code changes shipped by an engineering workflow, rather than general usage numbers.
2. **Cost per successful task** — count the full cost of a task, including employee time, human review, retries, and rework, not just the price per token. A more expensive model that gets a task right on the first try can end up cheaper overall than a cheaper model that needs several attempts.
3. **Dependability and accuracy** — track three outcomes for AI-produced work: ready to use as-is, needing correction, or needing to be escalated to a person. This shows whether AI is actually cutting total effort or just producing drafts that still need rework.
4. **Scalability economics** — as usage grows, the number of successfully completed tasks should grow faster than total cost. If it doesn't, the investment isn't actually getting more efficient with scale.

## Why it matters

This is a follow-up to the kind of guidance OpenAI gave in mid-July about managing AI budgets (covered here on July 19): tracking token price alone hides the real cost of AI work, because retries, human review, and rework all add cost that a per-token price doesn't show. Teams that adopt "cost per successful task" as their metric get a much more honest comparison between models or vendors than teams comparing sticker prices.

## How to use it

- For any AI-assisted workflow you run, define what a "successful task" looks like concretely (a resolved ticket, a merged code change, etc.) before measuring anything else.
- Calculate cost per successful task by adding token cost, review time, and rework time — not token cost alone.
- Track the split between results used as-is, results needing correction, and results escalated to a human, so you can see whether AI is actually reducing total effort.
- As you scale a workflow up, check whether your successful-task count is growing faster than your total spend. If cost is growing faster, the workflow isn't getting more efficient — it's just getting bigger.

## Source

- [A scorecard for the AI age](https://openai.com/index/a-scorecard-for-the-ai-age)
