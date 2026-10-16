---
title: "Claude API roundup: Fast mode graduates for Opus 5.5, Compliance API gets more preference data"
date: 2026-10-16
description: Claude Opus 5.5's Fast mode no longer needs a beta header or request, and the Compliance API can now return each user's saved custom instructions.
---

## What changed

Three updates landed on the Claude API's release notes page on October 15, 2026:

- **Fast mode for Claude Opus 5.5 is out of research preview.** [Fast mode](https://platform.claude.com/docs/en/build-with-claude/fast-mode) is a faster response option. You no longer need to request access, and requests to Claude Opus 5.5 no longer need the `fast-mode-2026-02-01` beta header (requests that still send it keep working). Claude Opus 5.5 now has a default fast-mode rate limit on the Start, Build, and Scale usage tiers. Fast mode for Claude Opus 5 and Claude Opus 4.8 is still in research preview, and those models still need the beta header.
- **Fast mode for Claude Opus 5.5 is now available on Claude in Microsoft Foundry**, for deployments hosted on Azure.
- **The Compliance API** — a tool for enterprise admins to retrieve organizational data for compliance purposes — now returns the text each organization member saved as "Instructions for Claude" in claude.ai, and as "Global instructions" in Cowork. This is in beta, for Claude Enterprise organizations. It's retrieved by calling `GET /v1/compliance/organizations/{org_uuid}/user_preferences` with an existing Compliance Access Key and the `read:compliance_user_data` scope.

## Why it matters

If you build on Claude Opus 5.5 and were using Fast mode, you can now remove the beta header from your requests — one less thing to manage, and it's officially supported rather than a preview feature. If your organization runs Claude on Microsoft Azure via Claude in Microsoft Foundry, you can now get the same faster responses there too. The Compliance API change is narrower: it's useful for Claude Enterprise admins who need to audit what custom instructions employees have set, for example to check compliance with internal policy.

## How to use it

- **Fast mode on Opus 5.5**: just send requests to `claude-opus-5-5` as normal; the beta header is no longer required (though it's harmless to still include it).
- **Fast mode on older Opus models** (Opus 5, Opus 4.8): keep sending the `fast-mode-2026-02-01` beta header — these remain in research preview.
- **Compliance API user preferences**: call `GET /v1/compliance/organizations/{org_uuid}/user_preferences` with your Compliance Access Key and the `read:compliance_user_data` scope. See Anthropic's [List user preferences](https://platform.claude.com/docs/en/manage-claude/compliance-org-data#list-user-preferences) docs for the full request format.

## Source

- [Claude API release notes — October 15, 2026](https://platform.claude.com/docs/en/release-notes/api#october-15-2026)
