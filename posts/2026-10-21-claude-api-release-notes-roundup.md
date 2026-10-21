---
title: "Claude API roundup: inference hooks GA, end-customer user profiles, organization webhooks"
date: 2026-10-21
description: Claude Platform release notes from October 20, 2026 — inference hooks leave beta, platforms can now tag API requests by end customer, and the Admin API adds webhooks for enforcement actions.
---

## What changed

Highlights from the Claude Platform release notes, published October 20, 2026:

- **Inference hooks are generally available.** Inference hooks — a feature that lets Claude Enterprise organizations intercept and act on API requests as they run — are now out of beta for Claude Enterprise organizations.
- **New user profiles feature.** You can now tell Anthropic which of your own end customers a given API request is for. This matters if you operate a platform, gateway, or resell API access to others: if Anthropic ever has to take a safety enforcement action, it can now apply to one specific end customer instead of your entire organization. The SDK and the `ant` command-line tool support the new `/v1/user_profiles` endpoints.
- **New organization webhooks (beta).** The Admin API — used to manage an organization's Claude account — now has webhooks, in beta behind the `webhooks-2026-10-07` beta header. Webhooks are automatic notifications sent to a URL you control when something happens, instead of you having to repeatedly check for it. The new `/v1/organizations/webhooks` endpoints support two event types: one fires when Anthropic restricts or bans one of your registered end-customer user profiles, and another fires when that restriction or ban ends. Access requires contacting your Anthropic account team.

## Why it matters

User profiles and the new webhooks work together and matter most to companies that resell or front Claude API access for others — for example, a SaaS product with many customers sharing one Anthropic account. Before this, a safety violation by one end customer could risk action against your whole organization's API access. Now you can register individual customers, and if Anthropic ever restricts one of them, you can find out automatically via webhook and respond (for instance, suspending just that customer) instead of everyone being affected or you finding out by surprise. Inference hooks reaching general availability means Enterprise organizations can rely on this request-level control without a beta label.

## How to use it

- Inference hooks are available to Claude Enterprise organizations without a beta flag — no extra setup needed to turn on the underlying feature (check Anthropic's inference hooks documentation for configuration details).
- To register your end customers, use the new `/v1/user_profiles` endpoints, supported in the Claude SDK and the `ant` CLI.
- To receive enforcement-action notifications, register a webhook endpoint via the new `/v1/organizations/webhooks` endpoints, sending the `webhooks-2026-10-07` beta header, and contact your Anthropic account team to request access.

## Source

- [Claude Platform release notes — October 20, 2026](https://platform.claude.com/docs/en/release-notes/api#october-20-2026)
