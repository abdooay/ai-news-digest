---
title: "Anthropic's September threat report: state hackers used Claude to run whole attacks"
date: 2026-09-11
description: Anthropic's latest threat intelligence report documents cases from December 2025 to August 2026 where state-linked and criminal groups used Claude to automate cyberattacks and influence operations, and explains how it disrupted them.
---

## What changed

On September 10, 2026, Anthropic published its latest **threat intelligence report**, covering cases of Claude misuse it found and shut down between December 2025 and August 2026. The report groups cases into two main areas: cyber operations and influence operations (coordinated fake or deceptive online activity).

Notable cyber cases:
- A suspected Russian state-sponsored group (tracked as GTG-20006) used Claude to automate most of an attack chain against Ukrainian and European government targets — from building tools and infrastructure, to phishing, to maintaining access and stealing data. The group also used AI to watch for its malware being detected and rewrite the code to evade security software.
- A financially motivated group (GTG-50014, linked to "ShinyHunters") used AI to harvest stolen login credentials at scale, and used stolen AI API keys taken from victims to launch further attacks on other organizations.
- A group Anthropic calls a "Chinese exploit foundry" (GTG-10007) ran continuous, largely unsupervised research to find security vulnerabilities in security products, producing several previously unknown ("zero-day") exploits.

Notable influence-operation cases:
- A Russian state-aligned operation in the Central African Republic used Claude to produce propaganda for a local radio station while hiding that it was Russian-funded.
- A France-based marketing firm built roughly 70 fake news websites in multiple languages, promoted by more than 250 fake social media accounts, sometimes pushing opposite arguments to different audiences.
- A firm in Istanbul sold a platform for manipulating Malaysian elections, running about 1,000 fake accounts and generating fabricated dossiers targeting opposition politicians.

Anthropic says it banned every account and organization involved, shared technical details with government agencies, industry partners, and affected victims, and used what it learned to improve its detection systems.

## Why it matters

The report's central point is that AI has lowered the skill and staffing needed to run sophisticated attacks. Operations that used to require a team of specialists — state-level cyber espionage, industrial-scale credential theft, coordinated propaganda campaigns — can now be run by individuals or small groups with AI doing most of the technical and content-generation work. Anthropic states plainly that "sophistication has stopped being a reliable signal of who is behind an operation" — meaning a technically advanced attack is no longer good evidence that a well-resourced government is behind it, since a small group with AI assistance can now do similar work. For developers and businesses, it's a reminder that AI providers' abuse-detection systems are an active, ongoing part of the security landscape, not a one-time filter — and that stolen API keys are now a real form of currency for attackers, since they can be used to run further attacks that get attributed to the original key owner.

## How to use it

This report doesn't come with product changes to configure. What is directly useful:
- If your organization holds API keys for Claude or other AI models, treat them like any other sensitive credential — rotate them regularly and monitor for unusual usage, since stolen keys were used in several of the cases described.
- Security teams can read the full case write-ups for concrete tactics (like AI-driven malware modification to evade detection) worth checking for in your own environment.
- If you suspect misuse of Claude, Anthropic's report describes channels for reporting it, including collaboration with industry partners and government authorities.

## Source

- [Detecting and countering misuse of AI: September 2026](https://www.anthropic.com/threat-intelligence-report-september-2026)
