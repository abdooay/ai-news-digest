---
title: "Fyxer built an AI executive assistant using dozens of small fine-tuned models"
date: 2026-09-19
description: Fyxer, an AI email and meeting assistant, uses 30-50 specialized models built on OpenAI's models rather than one general model, and says 53% of its draft replies need no edits.
---

## What changed

Fyxer, a company building an AI executive assistant, described its approach to OpenAI. Instead of relying on one general-purpose model for everything, Fyxer built 30 to 50 specialized models, each fine-tuned for a narrow task — classifying how to reply to an email, analyzing intent, predicting likely outcomes, matching tone, and retrieving relevant past conversations. These are built on OpenAI's models using techniques including supervised fine-tuning, LoRA (Low-Rank Adaptation, a method for efficiently customizing a model), and DPO (Direct Preference Optimization, a way to improve a model from user feedback).

Fyxer says this design targets a specific problem: professionals lose track of commitments across many tools and conversations, and the same email may need a different reply depending on the relationship, history, and goals involved — something a single generic reply-drafting model handles poorly.

Fyxer reports that 53% of its AI-drafted email replies are accepted without edits, that over 90% of users are still paying at the 90-day mark, and that its revenue grew from $1 million to $32 million in annual recurring revenue during 2025. Fyxer co-founder Archie Hollingsworth is quoted saying: "Retention is the real flex... over 90% of our users are still paying at the 90-day mark with us."

## Why it matters

This is a useful data point for anyone building AI products: instead of one big general model doing everything, Fyxer's results suggest that a collection of small, narrowly fine-tuned models — each validated with A/B testing before shipping — can produce higher-quality, more trusted output for a specific workflow like email handling. The reported retention and edit-acceptance numbers suggest users found the output reliable enough to build a habit around, which is often the harder bar to clear than a one-time demo.

## How to use it

This describes Fyxer's internal product architecture rather than a tool you can configure directly. If you're building an AI product with narrow, repeatable tasks (like email triage), the relevant takeaway is the pattern itself: many small fine-tuned models for specific sub-tasks, each validated before deployment, rather than one general model handling everything.

## Source

- [How Fyxer built an AI executive assistant people trust](https://openai.com/index/fyxer)
