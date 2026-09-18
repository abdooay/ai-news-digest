---
title: "Claude's Compliance API can now pull transcripts from Claude in Chrome sessions"
date: 2026-09-18
description: Claude Enterprise organizations can now retrieve session transcripts from the Claude in Chrome browser extension through the Compliance API, in beta.
---

## What changed

Anthropic's Compliance API — an API that lets Claude Enterprise organizations retrieve records of how Claude is being used, for legal and regulatory purposes — now also returns transcripts from Claude in Chrome sessions. Claude in Chrome is Anthropic's browser extension that lets Claude act inside your browser. These sessions show up with a `product_surface` value of `claude_in_chrome`. This is in beta, for Claude Enterprise organizations only.

To use it, an organization needs an existing Compliance Access Key and the `read:compliance_user_data` scope — the same access already required for other Compliance API session data.

## Why it matters

Before this, Claude Enterprise compliance teams could pull transcripts for other Claude products but not for Claude in Chrome sessions running on employees' machines. That was a gap for any organization that needs to retain or review Claude usage for legal, security, or audit reasons. This closes that gap, so Claude in Chrome activity is now covered by the same compliance tooling as the rest of Claude Enterprise.

## How to use it

- You need Claude Enterprise, an existing Compliance Access Key, and the `read:compliance_user_data` scope.
- Query the Compliance API's local session endpoints; sessions from the Chrome extension will appear with `product_surface: claude_in_chrome`.
- See the "Sessions on users' machines" documentation for the retrieval details.

## Source

- [Claude API release notes — September 18, 2026](https://platform.claude.com/docs/en/release-notes/api#september-18-2026)
- [Compliance API docs](https://platform.claude.com/docs/en/manage-claude/compliance-api)
- [Sessions on users' machines](https://platform.claude.com/docs/en/manage-claude/compliance-sessions#retrieve-local-sessions)
