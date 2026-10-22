---
title: "Claude API version 2026-10-21: major SDK versions, Apache 2.0 license, user profile enforcement status"
date: 2026-10-22
description: Anthropic released a new Claude API version and major new SDK versions now licensed under Apache 2.0, plus a way to check if an end customer has been restricted or banned.
---

## What changed

Anthropic's Claude Platform release notes for October 21, 2026 cover three changes:

- **New API version `2026-10-21`.** Anthropic published a migration guide explaining how to move existing integrations to it.
- **New major SDK and CLI versions that default to this API version**: Python SDK 2.0.0, TypeScript SDK 1.0.0, C# SDK 13.0.0, Go SDK 2.0.0, Java SDK 3.0.0, PHP SDK 1.0.0, Ruby SDK 2.0.0, and the `ant` command-line tool 2.0.0. These versions also include breaking changes unrelated to the API version switch, and are now licensed under the Apache 2.0 license instead of the MIT license.
- **New `enforcement_status` and `enforcement_actions` fields on user profiles.** User profiles let a platform or reseller tag API requests as belonging to a specific end customer. The new fields let you see whether Anthropic has restricted or banned one of those customers. You can filter the list of your profiles for ones with an open restriction or ban using the new `enforcement_status[]` filter on the list endpoint.

## Why it matters

The jump to major version numbers across every official SDK (Python 2.0, TypeScript 1.0, Go 2.0, Java 3.0, and more) signals breaking changes — code using an older SDK version will need review before upgrading, even separate from the API version change. The license change from MIT to Apache 2.0 is also worth noting for any company with its own open-source license compliance rules, since Apache 2.0 has different terms (for example, an explicit patent grant) than MIT.

The `enforcement_status` fields extend a feature Anthropic shipped the day before (October 20): if you run a platform where many end customers share your Anthropic account, you can now check programmatically whether a specific customer has been restricted or banned, instead of only finding out through a webhook notification or by asking your account team.

## How to use it

- Read the [migration guide for API version 2026-10-21](https://platform.claude.com/docs/en/api/migration-2026-10-21) before upgrading, and check its SDK and CLI changes section for the breaking changes that aren't tied to the API version itself.
- Upgrade to the new SDK/CLI versions when ready: Python 2.0.0, TypeScript 1.0.0, C# 13.0.0, Go 2.0.0, Java 3.0.0, PHP 1.0.0, Ruby 2.0.0, or `ant` CLI 2.0.0.
- To check an end customer's status, call the [list user profiles endpoint](https://platform.claude.com/docs/en/api/user_profiles/list) with the `enforcement_status[]` filter.

## Source

- [Claude Platform release notes — October 21, 2026](https://platform.claude.com/docs/en/release-notes/api#october-21-2026)
