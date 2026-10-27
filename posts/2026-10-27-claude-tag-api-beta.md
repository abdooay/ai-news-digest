---
title: "Claude Tag API launches in beta for Claude Enterprise"
date: 2026-10-27
description: Anthropic's new Claude Tag API lets Claude Enterprise organizations read and change Claude Tag settings on Slack channels and workspaces programmatically.
---

## What changed

Anthropic released the **Claude Tag API** in beta on October 23, 2026, for Claude Enterprise organizations. Claude Tag is the feature that brings Claude into Slack, mentioned as "@Claude" (or a similar tag) inside channels and direct messages.

The new API lets you, through code instead of a settings screen:

- Read and change Claude Tag settings on specific Slack channels and on whole Slack workspaces.
- See which settings apply in a given channel, and where each one comes from (for example, a workspace-wide default versus a channel-specific override).
- Attach "Access bundles" (pre-defined sets of permissions or data access) to Claude Tag.

It works through new endpoints under `/v1/organizations/claude_tag/`. To call it, you need:
- The beta header `experimental-claude-tag-2026-10-21`.
- An Admin API key created in claude.ai by your organization's primary owner, with either the `read:claude_tag` scope (to view settings) or `write:claude_tag` scope (to change them).

This API is **not available** to Claude Platform (Claude Console) organizations — only to Claude Enterprise.

## Why it matters

Until now, configuring Claude Tag across many Slack channels and workspaces meant going through the settings UI one at a time. For a large Claude Enterprise organization with many Slack workspaces, that doesn't scale. The Claude Tag API lets an IT or platform team automate that configuration — for example, rolling out the same Claude Tag settings to every channel in a new Slack workspace, or auditing which channels have which permissions, all from a script instead of by hand.

Being able to see "where each setting comes from" is also useful for troubleshooting: if Claude behaves differently in one channel than another, admins can now check programmatically whether that's a channel-level override or a workspace default.

## How to use it

- Confirm you're on a Claude Enterprise plan — this API isn't available on Claude Platform (Console) accounts.
- Have your organization's primary owner create an Admin API key in claude.ai with the `read:claude_tag` scope (for read-only access) or `write:claude_tag` scope (to make changes).
- Send the beta header `experimental-claude-tag-2026-10-21` on requests to the `/v1/organizations/claude_tag/` endpoints.
- See Anthropic's [Claude Tag API reference](https://platform.claude.com/docs/en/manage-claude/claude-tag-api) and the [Claude Tag overview](https://claude.com/docs/claude-tag/overview) for endpoint details.

## Source

- [Claude Platform release notes — October 23, 2026](https://platform.claude.com/docs/en/release-notes/api#october-23-2026)
