---
title: Anthropic is retiring the legacy Workbench and its experimental prompt-tool APIs
date: 2026-07-21
description: The old Workbench in the Claude Console shuts down on August 17, 2026, along with the experimental APIs for generating, improving, and templatizing prompts.
---

## What changed

On July 17, 2026, Anthropic announced that the legacy **Workbench** — the prompt-testing tool in the Claude Console, previously at platform.claude.com/workbench — is being sunset. Access ends on **August 17, 2026**. Saved prompts, variables, and evals (automated tests that score prompt outputs) from the old Workbench are not supported in the newer replacement, called Workbench, at platform.claude.com/playground.

At the same time, three related experimental API endpoints are being retired on the same date: `/v1/experimental/generate_prompt`, `/v1/experimental/improve_prompt`, and `/v1/experimental/templatize_prompt`. These let a program ask Claude to write, improve, or turn a prompt into a reusable template. After August 17, 2026, requests to these endpoints will return an error.

## Why it matters

If you have saved prompts, variables, or evals in the old Workbench, they will not carry over automatically — you need to export what you want to keep before the cutoff. If your code calls the experimental prompt-generation, prompt-improvement, or prompt-templatizing endpoints, those calls will start failing on August 17, 2026, so any integration using them needs to be updated or removed before then.

## How to use it

- Export any saved prompts, variables, or evals you want to keep from the banner in the old Workbench, or from your organization's settings, before August 17, 2026.
- Switch to the current Workbench at [platform.claude.com/playground](https://platform.claude.com/playground) for prompt testing going forward.
- If your code calls `/v1/experimental/generate_prompt`, `/v1/experimental/improve_prompt`, or `/v1/experimental/templatize_prompt`, stop relying on them before the retirement date — there's no stated replacement endpoint, so budget time to adjust your workflow.

## Source

- [Claude Platform release notes](https://platform.claude.com/docs/en/release-notes/api)
- [How do I use the Workbench? (Claude Help Center)](https://support.claude.com/en/articles/8606378-how-do-i-use-the-workbench)
