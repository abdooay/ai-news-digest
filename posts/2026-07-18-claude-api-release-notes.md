---
title: "Claude API updates: Admin API user management and mid-conversation system messages"
date: 2026-07-18
description: Two Claude Platform release notes from this week — a beta Admin API for managing Claude Enterprise members, and a way to add system instructions mid-conversation without breaking prompt caching.
---

## What changed

Two updates landed in the Claude Platform release notes this week.

**July 14 — Admin API user management (beta).** You can now manage the people in a Claude Enterprise (claude.ai) organization through the Admin API instead of the web console. This covers listing members, looking members up by email, changing a member's role, removing members, sending and withdrawing invites, and managing groups and their membership. It's in beta for all Claude Enterprise organizations. Group and custom-role requests need a beta header (`anthropic-beta: ce-user-management-2026-07-13`); plain member and invite requests don't.

**July 15 — Mid-conversation system messages, generally available.** Anthropic confirmed that "mid-conversation system messages" work on Claude Fable 5, Claude Mythos 5, and Claude Opus 4.8, across the Claude API, Amazon Bedrock, and Google Cloud, with no beta header required. (Anthropic says this note corrects an earlier, less clear availability statement.) This feature is not available on Claude Sonnet 5 — use the regular top-level `system` field there instead.

Mid-conversation system messages let a developer add a new `{"role": "system"}` message partway through a conversation, instead of editing the top-level `system` field that normally holds all system instructions. Normally, changing the top-level `system` field breaks prompt caching (a feature that reuses previously-processed parts of a conversation to save time and money) for everything that follows, because caching depends on the exact text staying identical from the start. Appending a system message partway through leaves everything before it untouched, so the cached portion still gets reused.

## Why it matters

**Admin API:** if your organization manages a lot of Claude Enterprise seats, you can now script user and group management (onboarding, offboarding, role changes) instead of doing it by hand in the console.

**Mid-conversation system messages:** this solves a real cost/performance problem for anyone building long-running or agentic sessions (where Claude keeps working over many turns, e.g., running tools repeatedly). Before this, adding an instruction like "from now on, always use parameterized SQL" partway through a long session meant editing the system prompt — which invalidated the cache and made Anthropic reprocess (and repay for) the entire conversation history so far. Now that instruction can be appended without that penalty. It also carries more authority than a regular user message: Claude treats system-role content as coming from the developer/application, not the end user, so it takes precedence when the two conflict.

## How to use it

**Admin API:**
```bash
curl https://api.anthropic.com/v1/organizations/me \
    -H 'anthropic-version: 2023-06-01' \
    -H "Authorization: Bearer $ANTHROPIC_OAUTH_TOKEN"
```
Enterprise-only features (like RBAC groups) additionally need:
```
-H "anthropic-beta: ce-user-management-2026-07-13"
```

**Mid-conversation system messages:** append a message with `"role": "system"` to the `messages` array at the point where the new instruction becomes relevant, for example right after a tool result in an agentic loop:

```json
{
  "role": "system",
  "content": "From now on, every suggestion must include explicit type annotations."
}
```

Rules to know: a system message can't be the first entry in `messages` (use the top-level `system` field for that), and it must immediately follow a `user` turn (including one carrying tool results) and either end the list or be immediately followed by an `assistant` turn — placing it between a `tool_use` block and its `tool_result` returns a 400 error. It only saves money if prompt caching is already turned on (via the `cache_control` field); without caching enabled there's no cached prefix to protect.

## Source

- [Claude Platform release notes](https://platform.claude.com/docs/en/release-notes/api)
- [Admin API reference](https://platform.claude.com/docs/en/api/admin)
- [Mid-conversation system messages](https://platform.claude.com/docs/en/build-with-claude/mid-conversation-system-messages)
