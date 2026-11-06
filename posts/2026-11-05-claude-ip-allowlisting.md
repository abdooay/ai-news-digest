---
title: Claude adds IP allowlisting for organizations (beta)
date: 2026-11-05
description: Organization admins can now restrict Claude Platform and Claude Enterprise access to a list of trusted IP addresses, so a leaked key or stolen sign-in is harder to use.
---

## What changed

As of November 5, 2026, organization admins and owners can turn on **IP allowlisting** (in beta) for their organization. An IP allowlist is a list of network addresses that are allowed to connect — anything outside the list is refused.

Once it's on:
- **Claude Platform organizations**: the Claude Console, and API endpoints including Messages, Message Batches, Token Counting, Models, Files, and Skills, plus the Claude Managed Agents and Admin/Compliance APIs, only accept requests from allowed addresses. A blocked API call gets a 403 error.
- **Claude Enterprise organizations**: Claude on the web, desktop and mobile apps, Claude Code (when signed in with a Claude account), Claude in Chrome, the Office add-ins, Cowork, and Remote Tools are all covered. A blocked user sees a page saying their network can't access the organization.

You can list IPv4 or IPv6 addresses, as single addresses or CIDR ranges (no broader than /8 for IPv4 or /32 for IPv6), up to 1,000 entries per organization. Changes can take up to 15 minutes to take effect.

Some things it doesn't cover: Claude in Amazon Bedrock, Claude Platform on AWS, Claude Models on Google Cloud, Claude in Microsoft Foundry, Claude Design, Claude in Slack, and Claude Academy are all outside the allowlist's reach. It also limits *where* a key or sign-in works, not *how long* it stays valid.

## Why it matters

If an API key or a user's sign-in leaks, an attacker normally can use it from anywhere. An IP allowlist shrinks that risk: even with a stolen key, the attacker's request still has to come from an address you've approved, so it's much harder to use the key to pull data or rack up usage charges. For enterprise users, the same logic applies to a stolen login.

This matters most to organizations with fixed infrastructure — offices, data centers, CI systems — where the set of networks people actually connect from is small and predictable. It's less useful if your team connects from constantly changing home or mobile addresses, since those have to be added manually and can change without notice.

It's not a replacement for other protections. Anthropic recommends also setting short expiration on API keys, or moving off static keys entirely to Workload Identity Federation, since an allowlist alone doesn't limit how long a leaked key keeps working.

## How to use it

1. Go to your settings page: the **Identity and access** page in the Claude Console (Claude Platform), or **claude.ai > Organization settings > Organization and access** (Claude Enterprise).
2. Turn on the **IP allowlist** toggle. Nothing changes until you save.
3. Add every network your servers, CI jobs, and users connect from — including the one you're connecting from right now — as individual addresses or CIDR ranges.
4. Before saving, check the box to let admins (owners, in Claude Enterprise) reach the settings page from any IP address, so you don't lock yourself out if you make a mistake.
5. Save and confirm, then watch your traffic for unexpected 403 `permission_error` responses (including jobs that only run daily or weekly) over the next while, and add any address you missed.

If you do get locked out, reconnect from a listed network, ask another admin/owner on a listed network to add your address, or contact Anthropic support as a last resort.

## Source

- [Claude API release notes — November 5, 2026](https://platform.claude.com/docs/en/release-notes/api#november-5-2026)
- [IP allowlisting docs](https://platform.claude.com/docs/en/manage-claude/ip-allowlist)
