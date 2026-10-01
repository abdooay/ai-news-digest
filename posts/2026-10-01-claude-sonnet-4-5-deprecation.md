---
title: Claude Sonnet 4.5 is being retired from the Claude API on November 30, 2026
date: 2026-10-01
description: Anthropic announced that Claude Sonnet 4.5 will stop working on the Claude API on November 30, 2026; it recommends migrating to Claude Sonnet 5.5.
---

## What changed

Anthropic announced the deprecation of the Claude Sonnet 4.5 model (model ID `claude-sonnet-4-5-20250929`) on the Claude API. The model is scheduled for retirement on November 30, 2026. After that date, API calls using this model ID will stop working.

Anthropic recommends migrating to Claude Sonnet 5.5, Anthropic's current Sonnet-tier model, and has published a migration guide covering the differences between the two models.

## Why it matters

"Deprecation" means a model is marked for shutdown, and "retirement" means it actually stops responding to API requests on that date. If you have an application, script, or integration that calls the Claude API with the Sonnet 4.5 model ID, it will break on November 30, 2026, unless you switch to a different model before then. Anthropic already made Sonnet 5.5 the default Sonnet model and reports it is faster and cheaper to run than Sonnet 5 at the same list price, so for most Sonnet 4.5 users the migration should be a straightforward upgrade rather than a downgrade.

## How to use it

- Check your code, scripts, or configuration for any hardcoded reference to `claude-sonnet-4-5-20250929`.
- Update the model ID to `claude-sonnet-5-5` and test your application against it before November 30, 2026.
- Read Anthropic's migration guide for specific differences to watch for when moving from Sonnet 4.5 to Sonnet 5.5.
- General background on how Anthropic handles model retirements is in its model deprecations page.

## Source

- [Claude API release notes — September 30, 2026](https://platform.claude.com/docs/en/release-notes/api#september-30-2026)
- [Migrating from Sonnet 4.5](https://platform.claude.com/docs/en/models/sonnet-5-5/migration-guide#migrating-from-sonnet-45)
- [Model deprecations](https://platform.claude.com/docs/en/about-claude/model-deprecations)
