---
title: "Claude API: Opus 4.5 deprecation, Enterprise Frontier Safeguards beta"
date: 2026-11-23
description: Anthropic deprecated Claude Opus 4.5, launched Enterprise Frontier Safeguards (a stricter data-retention option) in beta, and added two webhook events for it.
---

## What changed

Anthropic's Claude API release notes for November 23, 2026 cover three changes:

- **Claude Opus 4.5 deprecated**: the models `claude-opus-4-5-20251101` and `claude-opus-4-5` are now deprecated, with retirement from the Claude API set for January 22, 2027. Anthropic recommends migrating to Claude Opus 5.5.
- **Enterprise Frontier Safeguards (EFS), beta**: a new option on Claude Platform, Claude Platform on AWS, and Claude Models on Google Cloud (Anthropic-managed). EFS is a form of Zero Data Retention (ZDR — Anthropic does not keep your prompts and responses) for eligible organizations using Claude's most capable models. Instead of Anthropic storing nothing at all, encrypted copies called "Sealed Safety Data" are sent to a storage bucket in the customer's own cloud account. A workspace that uses Anthropic-managed storage is not eligible for EFS, because in that setup Anthropic itself would be storing the Sealed Safety Data.
- **Two new webhook events, beta**: organization webhooks now include `external_storage.failed` (sent when a customer-owned storage bucket used for EFS fails Anthropic's daily check) and `external_storage.recovered` (sent when it passes again).

## Why it matters

If you're using Claude Opus 4.5 in production, you have until January 22, 2027 to move to a newer model before it stops working on the API. Enterprise Frontier Safeguards is aimed at organizations with strict data-handling requirements: it lets them keep encrypted copies of prompts and responses under their own control, in their own cloud account, rather than trusting Anthropic to retain nothing or to store the only copy. The new webhook events let those organizations monitor their storage bucket's health automatically instead of finding out about a failure after the fact.

## How to use it

- If you use `claude-opus-4-5-20251101` or `claude-opus-4-5`, plan a migration to Claude Opus 5.5 before January 22, 2027. See Anthropic's migration guide for Opus 4.5.
- To request access to Enterprise Frontier Safeguards, use the setup guide linked from Anthropic's Enterprise Frontier Safeguards documentation; it requires one of Claude's most capable models and is currently in beta.
- To watch for storage problems under EFS, subscribe to the `external_storage.failed` and `external_storage.recovered` events on your organization's webhooks (beta).

## Source

- [Claude API release notes, November 23, 2026](https://platform.claude.com/docs/en/release-notes/overview#november-23-2026)
