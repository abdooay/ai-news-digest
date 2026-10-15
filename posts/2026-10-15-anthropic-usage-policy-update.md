---
title: "Anthropic updates its Usage Policy, effective November 12"
date: 2026-10-15
description: Anthropic's annual Usage Policy update consolidates deceptive-activity rules, narrows the elections section, and clarifies weapons, surveillance, and autonomous-hardware rules.
---

## What changed

On October 8, 2026, Anthropic published its yearly update to the **Usage Policy** — the rules that govern what people are and aren't allowed to do with Claude. The new version takes effect November 12, 2026. Anthropic says the changes mostly clarify existing rules, in response to new misuse patterns it has observed (in influence operations, weapons development, and surveillance) and to Claude increasingly doing longer, more independent work.

The main changes:

- **New section: "Do Not Engage in Deceptive Campaigns or Artificial Activity."** This pulls together rules that used to be scattered across the elections, fraud, privacy, and disinformation sections. It bans deceptive activity in general — political or commercial — including fake accounts and tools for running influence campaigns.
- **Elections section narrowed.** Renamed "Do Not Undermine Democratic Processes," it now focuses specifically on deceiving voters or disrupting elections. The old blanket ban on personalized vote and campaign targeting is gone, so legitimate campaign work (like targeted voter outreach) is allowed — but deceptive targeting, and misuse of voters' personal data, are still banned under other sections.
- **Weapons rule spelled out.** The ban now explicitly covers software and components that make weapons work, and arming drones or other autonomous vehicles. Anthropic says this just states clearly what it already enforced.
- **Surveillance and law enforcement rewritten.** Claude may not be used to track people without their consent (in real time or using previously collected data), and may not be used to decide or recommend who should be investigated, arrested, or charged, or to build surveillance tools. Consented tracking (like fraud monitoring), content moderation, journalism, and legal research are still allowed.
- **High-risk use cases clarified.** The core rule is unchanged — a qualified human must be able to review and override Claude's recommendations, and people affected must be told AI was involved. New: if Claude is controlling physical hardware that takes autonomous action, a qualified human operator must be able to watch and stop the equipment, and the equipment must default to a safe state if it loses its connection to Claude.
- **New rule against abusing Claude.** Sustained, pointless cruelty toward Claude (not ordinary frustration, dark creative writing, or testing) is now explicitly prohibited. Claude's existing ability to end abusive conversations is the main way this gets enforced.
- **Supported Regions clarified.** The policy spells out that the ban on use from unsupported regions applies to people physically there, companies based there, and companies majority-owned or controlled by parties there.

## Why it matters

If you build on Claude, read the new policy before November 12: the elections change actually loosens one restriction (personalized campaign targeting is no longer blanket-banned), while the deceptive-activity, weapons, surveillance, and autonomous-hardware sections are tightened or made more explicit. If your product controls physical equipment through Claude, you now need a human who can observe and stop it, and the equipment needs a safe default state for when the connection drops — that's a concrete engineering requirement, not just a policy statement.

## How to use it

- Read the new Usage Policy before it takes effect on November 12, 2026, especially if your use case touches elections/campaigns, weapons-adjacent software, surveillance, or hardware that Claude controls autonomously.
- If Claude controls physical hardware in your product, make sure a qualified human can observe and stop it, and that the hardware has a safe fallback state if it loses connection.

## Source

- [2026 Usage Policy update](https://www.anthropic.com/news/2026-usage-policy-update)
