---
title: Admins can now sign a Claude Enterprise member out everywhere
date: 2026-11-05
description: A new beta Admin API endpoint lets admins instantly end a member's sign-ins on every device and app, without removing them from the organization.
---

## What changed

As of November 5, 2026, there's a new beta endpoint that lets an admin sign a Claude Enterprise (claude.ai) member out of Claude on every browser and device at once, **without removing them from the organization**. The member keeps their seat and can sign back in right away — this is for emergencies, like a lost or stolen device or a security incident, while you decide what to do next.

Calling it ends:
- The member's sign-in sessions on every browser and device.
- Their "trusted device" registrations for sensitive actions (they'll have to register devices again).
- OAuth tokens issued for that organization, including ones used by Claude Code or third-party apps — those apps need to sign in again.
- The record of browsers that skipped two-step verification, so the next sign-in anywhere asks for it again.
- Push-notification registrations on their phones, desktop apps, and browsers (this part finishes within about a minute).

It does **not**: remove the member, revoke their API keys, end Claude Code cloud sessions or scheduled routines, end sign-ins to other organizations, or delete anything already stored on a device. The organization's **primary owner** can't be signed out this way — they have to use their own account settings.

## Why it matters

Before this, there wasn't a single action to immediately cut off a compromised or lost account across every app and device — an admin had to think about Claude Code tokens, browser sessions, trusted devices, and push subscriptions separately, or just remove the member outright (which also drops their seat and history). Now there's a middle option: kill all active access right away, keep the person's seat and data, and sort out membership later with a clear head.

Note the gaps: it doesn't revoke API keys, so if the concern is a leaked key, you still have to delete that separately in Organization settings. And it doesn't end Claude Code cloud sessions already running, so a background job can keep going for a bit after the sign-out.

## How to use it

- **Without an API key**: as an owner, go to the Members page in claude.ai organization settings and click **Sign out everywhere** next to the member. (Owners can't use this on their own account.)
- **With the Admin API**: create an Admin API key with the `write:members` scope (add `read:members` if you need to look the member up by email), then call:

```bash
curl -X POST "https://api.anthropic.com/v1/organizations/users/USER_ID/sign_out" \
  -H "x-api-key: $ANTHROPIC_API_KEY" \
  -H "anthropic-version: 2026-10-21" \
  -H "anthropic-beta: admin-user-sign-out-2026-10-08"
```

The `anthropic-beta: admin-user-sign-out-2026-10-08` header is required, or the request fails with a 400 error. The request has no body, and `user_id` must be the member's `user_` ID (from the List members endpoint).

- Each sign-out is logged in the audit log export as `org_user_trusted_devices_revoked`, and in the Activity Feed if your organization has the Compliance API.

## Source

- [Claude API release notes — November 5, 2026](https://platform.claude.com/docs/en/release-notes/api#november-5-2026)
- [Sign a member out everywhere docs](https://platform.claude.com/docs/en/manage-claude/user-management#sign-a-member-out-everywhere)
- [Admin API reference](https://platform.claude.com/docs/en/api/beta/organization)
