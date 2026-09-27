---
title: "Claude API roundup: cache diagnostics graduate, refusal billing tweaked"
date: 2026-09-27
description: Small Claude API updates from September 22–24, 2026 — cache diagnostics is out of beta, some previously-free refusals now get billed, and the Compliance API changes what it reveals.
---

## What changed

A few smaller items from the Claude Platform release notes, published between September 22 and 24, 2026:

- **Cache diagnostics is out of beta (Sept 23).** "Cache diagnostics" is a feature that reports details about prompt caching (Anthropic's system for reusing previously-processed context at a lower cost) for a given request. It no longer needs the `cache-diagnosis-2026-04-07` beta header — you opt in just by including a `diagnostics` object on a Messages API request. Every response from `POST /v1/messages` now includes a `diagnostics` field; it's simply `null` if you didn't ask for it.
- **Billing changed for some refusals (Sept 24).** A "refusal" is when Claude declines to answer. Anthropic already billed refusals that happen partway through a response. Now it also bills refusals that happen before any output at all, but only for three specific categories: `"bio"` (biology-related safety refusals), `"frontier_llm"`, and `"reasoning_extraction"` — categories where Anthropic says false positives (wrongly refusing a fine request) are rare. These are billed at the normal rate for whichever model handled the request. Refusals in other categories, before any output, are still free, and "fallback credit" (Anthropic's existing compensation for certain refusals) is unchanged.
- **Compliance API changes (Sept 24).** The Compliance API lets organizations audit how Claude is used inside their company. Two changes: (1) its "local session" endpoints — which cover Claude used inside Microsoft Excel, PowerPoint, Word, and Outlook — are now fully out of beta; (2) its Activity Feed (a log of usage events) no longer includes file names, project document names, or artifact titles in its records, including for past activity. Organizations that need a name or title back can look it up separately using a Compliance Access Key with the `read:compliance_user_data` scope.

## Why it matters

None of these are new features developers need to adopt immediately, but they can affect existing bills and integrations. If your usage touches biology-related, "frontier_llm," or "reasoning_extraction" refusal categories, expect a small increase in billed requests going forward. If you rely on the Compliance API's Activity Feed to see file or document names in an audit log, that data has been removed for privacy reasons — you'll need the separate lookup path if you still need it.

## How to use it

- To see cache diagnostics, add a `diagnostics` object to your Messages API request — no beta header required anymore (though the old header still works if you're already using it).
- No action needed for the refusal billing change — it applies automatically to the `"bio"`, `"frontier_llm"`, and `"reasoning_extraction"` refusal categories.
- If you use the Compliance API's Activity Feed and need file/document/artifact names, request a Compliance Access Key with the `read:compliance_user_data` scope and look up names by the activity's ID.

## Source

- [Claude Platform release notes — September 23, 2026](https://platform.claude.com/docs/en/release-notes/api#september-23-2026)
- [Claude Platform release notes — September 24, 2026](https://platform.claude.com/docs/en/release-notes/api#september-24-2026)
