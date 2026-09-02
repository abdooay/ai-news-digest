---
title: Anthropic previews Enterprise Frontier Safeguards for zero-data-retention customers
date: 2026-09-01
description: A new system lets enterprises keep zero data retention with Claude while still getting misuse-detection alerts, by storing monitoring data in the customer's own cloud account.
---

## What changed

Anthropic announced Enterprise Frontier Safeguards (EFS), built with more than 100 enterprise customers plus AWS, Google Cloud, and Microsoft Azure. It's aimed at organizations that want "zero data retention" — meaning Anthropic keeps no copy of what's sent to Claude — but still need protection against misuse that only becomes visible when you look across many sessions or accounts over time.

How it works:
- Any data needed for misuse detection is stored in the customer's own cloud account (Amazon S3, Azure Blob Storage, or Google Cloud Storage), not on Anthropic's servers.
- The customer controls the encryption keys for that storage.
- Detection runs through automated monitoring only; Anthropic says no Anthropic employee reviews the data, and detection signals go straight to the customer.
- It's opt-in: turning it on doesn't change model behavior, pricing, or rate limits.
- Anthropic isn't charging extra for EFS itself; customers pay their cloud provider's normal storage costs.

It's designed to support Claude Code, Claude Enterprise, the Claude Platform (API), Amazon Bedrock, Google Cloud, and Microsoft Foundry. Rollout is planned in phases starting fall 2026. Until EFS is available, eligible customers get standard zero data retention on Claude Fable 5 and 5.1.

Anthropic's stated reasoning: some misuse can only be spotted by correlating data across sessions and accounts over time — a single interaction that's deleted instantly doesn't reveal the pattern. In Anthropic's words: "It is not sufficient to run automated analysis on each interaction separately and then instantaneously discard the data."

## Why it matters

Companies in regulated industries (the announcement names financial services, healthcare, manufacturing, telecom, law, retail, and the public sector) often require zero data retention as a condition of using an AI vendor at all. Until now, that meant giving up any cross-session misuse monitoring. EFS is Anthropic's answer to that trade-off: the customer keeps full control of the data (their own storage, their own encryption keys) while still getting automated alerts if something looks like misuse.

## How to use it

- EFS is a rollout preview, not generally available yet — Anthropic says phased rollout starts fall 2026.
- It's opt-in and won't change how Claude behaves, what it costs, or your rate limits.
- Enterprise customers who want zero data retention now can already get it on Fable 5 and 5.1 while EFS is being built out.

## Source

- [Developing Enterprise Frontier Safeguards with our customers](https://www.anthropic.com/news/enterprise-frontier-safeguards)
