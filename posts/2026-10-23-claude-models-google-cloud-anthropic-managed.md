---
title: "Claude API now available as \"Claude Models on Google Cloud (Anthropic managed)\""
date: 2026-10-23
description: Anthropic launched a way to use the Claude API through a Google Cloud project, with Google handling billing and access control instead of Anthropic directly.
---

## What changed

Anthropic's Claude Platform release notes for October 22, 2026 announce "Claude Models on Google Cloud (Anthropic managed)" — a new way to reach the Claude API where Anthropic still runs the models, but you access and pay for it through your Google Cloud project instead of directly through Anthropic.

Under this setup, Google Cloud IAM (Google's identity and access management system) controls who on your team can use it, and Google Cloud Marketplace handles billing, rather than Anthropic's own console. Setting it up creates a new, separate Anthropic organization tied to your Google Cloud project — separate from any existing Anthropic organization your company already has, including a Claude Enterprise one.

Alongside this, Fast mode (a Claude feature that trades some flexibility for lower latency) is now available for Claude Opus 5.5 on this Google Cloud offering.

## Why it matters

This is aimed at companies that already route their vendor spending and access control through Google Cloud and would rather manage Claude that way than set up a separate relationship with Anthropic. It's a different product from Anthropic's existing "Claude on Vertex AI" style offerings — the release notes point to a comparison page for picking between the Google Cloud options. If you're not using Google Cloud for billing or access control, this doesn't change anything for you.

## How to use it

- To set this up, you need permission to purchase in Google Cloud Marketplace on your billing account, permission to enable services on the project, and an IAM role that lets you open the Claude Console.
- Subscribe to the "Claude Models on Google Cloud (Anthropic managed)" listing in Google Cloud Marketplace, then follow the setup steps in Anthropic's documentation.
- If your company already has an Anthropic organization with a negotiated discount, contact your Anthropic or Google Cloud account representative before starting — discounts can't be applied retroactively.
- If you want to move an existing Anthropic organization onto this setup, see the "moving from an existing Anthropic organization" section of the docs rather than starting fresh.

## Source

- [Claude Platform release notes — October 22, 2026](https://platform.claude.com/docs/en/release-notes/api#october-22-2026)
- [Claude Models on Google Cloud (Anthropic managed) docs](https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/anthropic-managed)
