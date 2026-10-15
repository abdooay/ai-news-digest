---
title: "How Anthropic is preparing Claude for the 2026 US midterms"
date: 2026-10-15
description: Anthropic shared usage data, bias test scores, and new abuse-detection measures ahead of the 2026 US midterm elections.
---

## What changed

On October 14, 2026, Anthropic published an overview of what it's doing ahead of the 2026 US midterm elections. Five things stood out:

- **Usage data.** Anthropic looked at a random sample of 250,000 US Claude.ai conversations from late September 2026. About 5.75% touched on politics, policy, or social issues; about 0.51% were about elections or voting specifically. Only about 0.01% asked who to vote for, and only about 0.002% broke Claude's election integrity rules.
- **Voting information.** Claude shows a banner pointing to TurboVote (a nonpartisan voter information service run by Democracy Works) for questions about registration, polling places, and election dates. Later in October, Claude will start pulling official, state-specific voting information directly from Democracy Works for US users — answering things like where to vote and what ID to bring. On election night and after, Claude will show the latest official results.
- **Bias testing.** Anthropic tests each model for political bias before release. It says its Opus, Sonnet, and Haiku 5.5 models scored 99% on its internal "evenhandedness" evaluation. Three outside groups reviewed how Claude handles free expression and found it sometimes adds unsolicited caveats, and hedges unevenly — more often on right-leaning arguments than left-leaning ones. Anthropic says it's working on this: improving yes/no answers, tuning when caveats appear, and expanding its tests to cover candidates and voting directly.
- **Policy and campaign guidance.** The Usage Policy bans using Claude to deceive voters or disrupt elections (see Anthropic's related policy update, also published this week). Anthropic has a separate guide spelling out what campaign-related use is allowed (drafting materials, analyzing turnout data) versus banned (fake personas, fake news sites).
- **Abuse detection.** Anthropic added new automated detectors aimed at multi-step misuse, fake accounts and fake news sites, financially motivated election scams, and foreign state actors — plus extra cyber protections for election infrastructure and specific safeguards for the US, Israel, and Brazil. Independent red-teaming by the Institute for Strategic Dialogue and the McCain Institute found Claude reliably refuses a single harmful request, but can miss abuse that's split across several smaller, individually harmless-looking steps — which is what led to the new multi-step detectors. Anthropic says it has already banned accounts tied to a foreign fake-news operation covering the midterms, and to financially motivated fake-news schemes.

## Why it matters

The headline number for most users is reassuring: actual election-rule violations are rare (about 1 in 50,000 conversations, by Anthropic's own sample). The more useful detail is the bias-testing result — three independent reviewers found a real, if subtle, asymmetry in how Claude hedges political arguments, and Anthropic is naming it instead of just claiming perfect neutrality. The multi-step abuse detection point is also a genuine methodology upgrade: catching abuse split into harmless-looking pieces is a much harder problem than catching a single bad request.

## How to use it

- If you're a US Claude.ai user with election questions, look for the voting-information banner — official, state-specific information is rolling out through Democracy Works later this month.
- If you're building campaign-related tools on Claude, check Anthropic's campaign-use guide (linked from the announcement) for what's allowed versus prohibited before you build.

## Source

- [Preparing for the 2026 US midterms](https://www.anthropic.com/news/2026-us-midterms)
