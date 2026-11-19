---
title: "Claude Code v2.1.326–328: auto mode expands, /code-review changes, more permission tightening"
date: 2026-11-19
description: Three Claude Code releases bring auto mode to more model gateways, split /code-review from cleanup checks, and keep narrowing what runs without asking.
---

## What changed

Claude Code, Anthropic's command-line coding agent, shipped three versions since the last digest: 2.1.326, 2.1.327, and 2.1.328. Together they're mostly fixes (well over 300 combined), but a few changes stand out:

- **Auto mode reaches more platforms (2.1.328).** Auto mode — where Claude Code decides for itself whether an action is safe enough to run without asking — is now available for Claude Opus 4.6 and Sonnet 4.6 on Amazon Bedrock, Google Cloud's Agent Platform, Microsoft Foundry, and the Claude apps gateway. On these platforms, interactive sessions with no permission mode chosen now start in auto mode by default.
- **`/code-review` and `/simplify` split apart (2.1.328).** `/code-review` now reports only bugs and CLAUDE.md rule violations on most models, and marks each finding "Important," "Pre-existing," or "Nit," ending with a suggested fix. For reuse, simplification, and efficiency suggestions, run `/simplify` instead — that's a separate command now.
- **New `/status` diagnostics (2.1.327).** `/status` now lists broken agent, skill, command, and output-style files; keybinding errors; an unavailable sandbox; permission settings being ignored; and hook rules that never match anything. 2.1.326 added a row to `/status` for when your provider or an environment variable (like `DISABLE_TELEMETRY`) has turned a feature off.
- **Keep MCP (Model Context Protocol) tokens out of your command history (2.1.327).** `claude mcp add-json <name> -` now reads a server's JSON configuration from standard input, so you can pipe in a config that contains a secret token without it ending up in your shell history. (Not available inside a running Claude Code session.)
- **More permission tightening (2.1.326, 2.1.327, 2.1.328, continuing a trend from recent releases).** Sandboxed commands can now write to fewer folders by default; some `cp` and `mv` commands now ask first; Claude Code's own sign-in files and some device/process files are now protected from file-tool writes; and a WebFetch call now refuses URLs over 2,000 characters before it even shows a permission prompt.
- **Reliability fixes across all three releases:** a zsh bug where commands starting with `=` (like `echo ====`) failed with a "not found" error is fixed; automatic compaction (summarizing a long conversation to save space) no longer reuses a stale system prompt; remote MCP servers that drop out during a long outage (like a VPN disconnect) are now retried in the background for about a day instead of staying disconnected; and several Code Mode (Claude's scripting mode) bugs around resumed sessions and background tasks are fixed.

## Why it matters

The permission and sandbox changes are the throughline across all three releases, continuing a pattern from recent versions: Anthropic keeps narrowing the set of actions that run silently, in favor of asking first or refusing outright. If you run Claude Code unattended — scheduled tasks, `/loop`, CI pipelines — it's worth re-checking your permission allow-list after each update, since something that ran quietly before may now pause for approval.

The `/code-review` and `/simplify` split matters if you have scripts or habits built around `/code-review` doing double duty as a cleanup pass — it no longer does that by itself.

Auto mode's expansion to Bedrock, Google Cloud's Agent Platform, and Microsoft Foundry is useful if your organization runs Claude Code through one of those gateways rather than directly through the Anthropic API — you now get the same "ask only when needed" behavior there.

## How to use it

- Update with `claude update` (or your package manager) to get version 2.1.328.
- If auto mode starts for you by default and you don't want that, set `disableAutoMode` in your settings.
- Use `/simplify` for reuse/simplification/efficiency reviews; use `/code-review` for bugs and CLAUDE.md violations.
- Check `/status` after updating — it will now flag broken config files and permission rules that silently never apply.
- To add an MCP server config containing a secret without it touching your shell history, pipe JSON into `claude mcp add-json <name> -`.

## Source

- [Claude Code CHANGELOG.md — v2.1.328](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21328)
- [Claude Code CHANGELOG.md — v2.1.327](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21327)
- [Claude Code CHANGELOG.md — v2.1.326](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21326)
