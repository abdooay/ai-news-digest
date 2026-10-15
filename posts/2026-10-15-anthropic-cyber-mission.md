---
title: "Anthropic launches the Cyber Mission to help defenders use AI"
date: 2026-10-15
description: Anthropic's new Cyber Mission gives critical-infrastructure security firms access to Claude and engineers, and offers free vulnerability scans to open-source projects.
---

## What changed

On October 8, 2026, Anthropic announced the **Cyber Mission**, a long-term effort to help the people who defend computer systems ("defenders") use AI more effectively. It starts with two programs:

**1. Critical Infrastructure Defense Program (CIDP).** This gives trusted security companies access to Anthropic's most capable Claude models, on-site Anthropic engineers, and Anthropic's own threat research. The focus is operational technology (OT) — the specialized computer systems that run power grids, water systems, transportation networks, and government systems. Eleven companies are founding partners: Accenture, Booz Allen, CrowdStrike, Deloitte, Dragos, Hitachi, Insane Cyber, Nozomi Networks, Palo Alto Networks, PwC, and Rockwell Automation. Some are already using Claude to help fix vulnerabilities. Anthropic is starting with a small group of providers and plans to expand.

This builds on an earlier program from June, where Anthropic offered Claude and support to state, local, tribal, and territorial governments. Anthropic says that program has reached more than half of US states and some large public infrastructure operators.

**2. OSS Scanner.** This is a free, opt-in service for open-source software projects. Anthropic's AI models periodically scan an enrolled project's code and send a report that includes a proof of concept, an explanation of the problem, and a suggested fix where possible. Anthropic says it expects these AI-written reports to be correct more than 90% of the time, but warns that the reports are not reviewed by a human before being sent, so some may be wrong.

To pay for this, Anthropic funded several open-source foundations: the Python Software Foundation, Alpha-Omega, OpenSSF (through the Linux Foundation), and the Apache Software Foundation. Money comes partly from the "Defender Advantage Fund," a fund Anthropic launched in August for this kind of work.

A related earlier effort, called Project Glasswing, which scanned hundreds of popular open-source projects, has now been folded into Anthropic's separate Cyber Verification Program (open-source maintainers can apply there for deeper access, or to Claude for Open Source for free subscriptions).

## Why it matters

Anthropic's argument is that offense and defense in cybersecurity are currently unbalanced: AI has made it cheaper to find and exploit software flaws, but finding, verifying, and actually fixing those flaws is still slow, manual work. In the Glasswing pilot, Anthropic says months often passed between finding a bug and getting it fixed. These two programs are aimed directly at that gap — giving critical-infrastructure defenders dedicated access to frontier models and engineers, and giving open-source projects (which often have no dedicated security budget) free automated scans.

Anthropic also states a prediction worth noting: it expects AI to meaningfully favor defenders within about two years, but acknowledges the near term could look different — i.e., attackers may benefit first.

## How to use it

- **Security companies and critical-infrastructure operators:** register interest in the Critical Infrastructure Defense Program through the form linked on Anthropic's announcement page.
- **Open-source maintainers:** you can opt in to the free OSS Scanner if your project can handle AI-generated reports (which aren't human-reviewed). If your project needs human-verified disclosures instead, Anthropic's existing coordinated vulnerability disclosure process still applies.
- **Open-source maintainers wanting broader access:** apply to Claude for Open Source (free Claude Max subscriptions) or the Cyber Verification Program.

## Source

- [Introducing the Anthropic Cyber Mission](https://www.anthropic.com/news/anthropic-cyber-mission)
