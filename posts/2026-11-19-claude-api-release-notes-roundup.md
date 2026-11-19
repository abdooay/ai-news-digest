---
title: "Claude API: linked billing beta and wider text watermarking"
date: 2026-11-19
description: Claude's API release notes add a beta for billing through a customer's own Claude organization, and expand text watermarking to four more models.
---

## What changed

Two items appeared in Claude's official API release notes since the last digest:

- **Linked billing (beta), November 17, 2026.** Your app's customers can now pay for their own Claude API usage through their own Claude organization, instead of you billing them yourself. It's enabled by sending the `user-profiles-billing-2026-10-01` beta header and setting a `billing_policy` field on `/v1/messages` or `/v1/chat/completions` requests.
- **Text watermark expanded, November 16, 2026.** Anthropic's invisible text watermarking — a way of marking AI-generated text so it can later be identified as coming from a Claude model — now also covers output from Claude Opus 4.6, Opus 4.5, Sonnet 4.5, and Haiku 4.5, on supported platforms. The release notes warn that a request might not carry the watermark if it sets `temperature`, `top_p`, or `top_k` to a non-default value. This follows an earlier expansion to Claude Mythos 5, Opus 4.7, and Sonnet 4.6 on November 3.

## Why it matters

Linked billing changes who's on the hook for API costs: instead of your app paying Anthropic and then billing your own customers, a customer with their own Claude organization can pay Anthropic directly for the usage your app generates on their behalf. That can simplify billing for apps built on top of Claude, especially ones serving business customers who already have (or want) their own Claude organization.

The watermark expansion mostly matters if you're trying to detect AI-generated text, or if you care whether your own output can be identified as Claude-generated. The caveat about sampling parameters is worth remembering: if your integration customizes `temperature`, `top_p`, or `top_k`, don't assume watermarking is guaranteed on that output.

## How to use it

- To try linked billing: add the `user-profiles-billing-2026-10-01` beta header to your `/v1/messages` or `/v1/chat/completions` requests, and set the `billing_policy` field. Since it's in beta, test it before relying on it in production.
- Text watermarking requires no setup — it's applied automatically on supported platforms for the listed models, as long as you're not overriding `temperature`, `top_p`, or `top_k`.

## Source

- [Claude API release notes — November 17, 2026](https://platform.claude.com/docs/en/release-notes/overview#november-17-2026)
- [Claude API release notes — November 16, 2026](https://platform.claude.com/docs/en/release-notes/overview#november-16-2026)
