---
title: "Claude Code changelog roundup: v2.1.299 and v2.1.300"
date: 2026-10-15
description: Claude Code adds idle auto-compaction for long terminal conversations, lets plugin authors draw overlay text in the prompt box, and adds an /advisor command on AWS.
---

## What changed

Claude Code is Anthropic's command-line coding agent. On October 14, 2026, it shipped v2.1.299 and v2.1.300.

**v2.1.299:**
- Added **idle compaction** in the terminal: if a conversation grows past 200,000 tokens and then sits idle for about 54 minutes, Claude Code now compacts it (summarizes older history to save space) before the hour-long prompt cache expires. That way your next message doesn't have to reprocess the whole conversation from scratch. `CLAUDE_CODE_IDLE_COMPACT_MIN_TOKENS` changes the 200K threshold, and setting `"idleCompaction": false` in settings.json turns it off.
- Added `CLAUDE_CODE_DISABLE_FILE_MENTIONS`: normally, `@`-mentioning a file sends its contents to Claude; with this environment variable set, Claude instead just gets the file's path and reads it itself with its own tools.
- Added `/effort` and `/fast` support inside "agent view" (the view for managing background agents), so you can set what new sessions start with directly from there.
- Added `/usage` warnings for max effort mode, workflows, always-on context, and large tool results — all things that can burn through usage limits faster than expected.
- Many fixes, including: scheduled wakeups no longer failing to fire while a background task is running; memory growth under heavy debug logging; and an MCP connection hang fixed (GitHub issue #99014).

**v2.1.300:**
- Added `virtualText`: plugin authors ("mods") can now draw text directly in the prompt box that's visible on screen but never becomes part of what you actually type or submit — useful for inline hints.
- Added `/advisor` on Claude Platform on AWS. No advisor runs by default; you have to explicitly pick one, and `CLAUDE_CODE_DISABLE_ADVISOR_TOOL=1` turns the feature off entirely.
- Added support for a mod's `agent.spawn` hook to rewrite a workflow agent's prompt and model, not just refuse it as before.
- Added a `prompt.change` hook for mods, which fires when the prompt box's text changes without you actually typing — for example, recalling history, clearing, undoing, or a plugin auto-filling it.
- Split cache-related OpenTelemetry tracing data (`cache_creation_5m_tokens` / `cache_creation_1h_tokens`) by how long the cache write lives for, for people monitoring usage.
- Many fixes across sessions, worktrees, subagents, MCP servers, and the VS Code, cloud, Claude Tag (Slack), and Code Review integrations — including a fix for cloud sessions sometimes incorrectly blaming an organization policy for blocking a host when it was actually the session's own network settings.

## Why it matters

Idle compaction (v2.1.299) is the most broadly useful change here: anyone running long coding sessions in the terminal has likely hit the situation where a conversation grows huge, you step away, and when you come back the prompt cache has expired — meaning your next message reprocesses everything at full cost and latency. This fixes that automatically, with no action needed. The `virtualText` and hook additions in v2.1.300 are developer-facing — they matter if you build Claude Code plugins, not for typical day-to-day use.

## How to use it

- Update with `claude update`, or through your package manager.
- Idle compaction is on by default for conversations over 200K tokens; adjust the threshold with `CLAUDE_CODE_IDLE_COMPACT_MIN_TOKENS` or turn it off with `"idleCompaction": false` in settings.json.
- To stop `@` file mentions from sending file contents directly, set `CLAUDE_CODE_DISABLE_FILE_MENTIONS`.
- `/advisor` is opt-in on Claude Platform on AWS — run `/advisor` to pick one.

## Source

- [Claude Code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [v2.1.299 changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21299)
- [v2.1.300 changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21300)
