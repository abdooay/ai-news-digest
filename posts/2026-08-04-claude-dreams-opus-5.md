---
title: Claude Managed Agents' Dreams feature now supports Opus 5
date: 2026-08-04
description: Anthropic's Dreams research preview, which reorganizes an agent's memory, added support for Claude Opus 5.
---

## What changed

On August 1, 2026, Anthropic's Claude Platform release notes announced that Dreams, a research-preview feature of Claude Managed Agents, now supports Claude Opus 5.

Dreams is a feature that reads an existing memory store (saved information an agent has accumulated) together with past session transcripts, and produces a reorganized memory store: duplicate entries are merged, stale entries are replaced, and new insights are surfaced. It was already available for other models; this update adds Opus 5 to the list of supported models.

## Why it matters

If you're running Claude Managed Agents with a memory store on Opus 5, you can now use Dreams to periodically clean up and improve that memory without switching to a different model just for that step.

## How to use it

Dreams is still a research preview, gated behind a beta header, and requires requesting access. See Anthropic's supported-models list for Dreams to confirm current availability before using it in a Managed Agents setup.

## Source

- [Claude Platform release notes](https://platform.claude.com/docs/en/release-notes/overview) (entry for August 1, 2026)
