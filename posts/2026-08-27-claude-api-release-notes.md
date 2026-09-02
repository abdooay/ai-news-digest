---
title: "Claude API: Files and Skills endpoints drop beta headers, personal API keys added"
date: 2026-08-27
description: SDK updates remove beta requirements for the Files and Skills APIs, and Anthropic adds personal and service account API keys to the Claude Console.
---

## What changed

On August 27, 2026, Anthropic shipped two updates to the Claude Platform (the API and developer console):

**SDK updates (Python 1.2.0, TypeScript 0.122.0, Go 1.68.0, Java 2.59.0, Ruby 1.67.0, C# 12.44.0):**
- `client.beta.files` and `client.beta.skills` no longer need a beta header — these had already come out of beta in a previous release, and now the SDKs stop requiring the extra header for them.
- `client.beta.skills.delete()` now deletes a Skill along with all of its versions, instead of just one version.
- The `BetaSkill` type was renamed to `BetaContainerSkill`.

**Personal and service account keys:**
Organizations can now create personal and service account API keys directly in the Claude Console (Anthropic's web dashboard for managing API access).
- A personal key acts with the same permissions as the account it's linked to, and stops working automatically if that account is removed from the organization.
- Keys can be scoped to a single workspace or set to work across all of an organization's workspaces.
- Workspace API keys (the older option) still work and remain supported.

## Why it matters

The beta-header change is a small cleanup: if your code was already using the Files or Skills APIs with the beta header, it keeps working, but you can now drop the header from new code. The bigger practical change is personal and service account keys — they make it easier for an admin to see which key belongs to which person or service, and keys tied to a person automatically stop working when that person leaves, which reduces the risk of orphaned, forgotten API keys still having access.

## How to use it

- Update your SDK to the versions above to drop the beta header requirement for Files and Skills calls.
- If your code references the `BetaSkill` type, rename it to `BetaContainerSkill`.
- To create a personal or service account key, go to the Claude Console and choose to scope it to one workspace or across your organization.

## Source

- [Claude Platform release notes, August 27, 2026](https://platform.claude.com/docs/en/release-notes/api#august-27-2026)
