---
title: "Claude Code v2.1.305–306: Linux sandbox option for Chromium/podman, Code Review re-review fix"
date: 2026-10-21
description: Claude Code v2.1.305 adds a Linux sandbox setting for tools like Chromium and rootless podman and fixes a tool-search regression on gateways, while v2.1.306 fixes two bugs in cloud sessions.
---

## What changed

Claude Code is Anthropic's command-line coding agent. Two versions shipped this week.

**v2.1.305** (the bigger of the two):
- **New `sandbox.allowNestedUserNamespaces` setting.** Claude Code can run commands in a sandbox that limits what they can touch on disk. Some programs — Chromium and rootless podman are the examples given — need to create their own "user namespaces" (an operating-system feature for isolating processes) to work at all. This setting lets you allow that, but doing so lets those sandboxed commands get around some of the sandbox's file protections.
- **New `CLAUDE_CODE_RETRY_WATCHDOG_USAGE_LIMIT_RECHECK_MS` variable.** If you run Claude Code unattended with automatic retry on (`CLAUDE_CODE_RETRY_WATCHDOG`), this controls how often it rechecks whether a usage limit that blocked it has since been lifted early, instead of waiting for the limit's full reset time.
- **Fixed a request-failure regression from v2.1.304.** Every request was failing on Amazon Bedrock, Google Vertex AI, and other providers when the endpoint or a gateway in front of it rejected "tool search" (a feature for finding tools) or left it out of an allowed-tools list. Claude Code now retries without it instead of failing.
- **Fixed `/effort` and `/autocompact` settings silently not applying** when the model name differed from a configured override only by letter case or by a trailing `[1m]` tag (used for long-context model variants).
- **Code Review improvements.** Organizations using Claude's automated Code Review feature get two fixes: a re-review of a pull request no longer opens by saying "LGTM" (looks good to me) while earlier blocking findings from the same review are still open, and Code Review now reliably reviews the newest commit when several pushes land on a pull request close together.
- A long list of smaller reliability fixes across worktrees, MCP servers, subagents, `/usage` display, screen-reader support, and the self-hosted runner.

**v2.1.306** (a small follow-up):
- Fixed `claude -p` (headless/non-interactive mode) wrongly reporting "Not logged in" when run inside a cloud session without that session's environment variables.
- Fixed a bug where, in sessions using many MCP tools (external tools connected via the Model Context Protocol), a normal API error could get replaced by a misleading "prompt is too long" message, along with an unnecessary compaction (summarizing the conversation to save space) that didn't need to happen.

## Why it matters

The sandbox namespace setting matters mainly if you've hit Chromium or rootless podman failing inside Claude Code's sandbox — it gives you a way to let those tools work, with the trade-off that the sandbox protects your files less strictly for those commands. The tool-search fix is worth knowing about if you run Claude Code behind Bedrock, Vertex AI, or a custom gateway: v2.1.304 introduced a bug that broke every request in that setup, and v2.1.305 fixes it. The Code Review fixes reduce false "all clear" signals on pull requests, which matters to any team relying on it to gate merges.

## How to use it

- Update with `claude update`, or through your package manager, to get these changes.
- If a sandboxed command needs to create Linux user namespaces (for example, to run Chromium or rootless podman), set `sandbox.allowNestedUserNamespaces` to `true` in your settings — understanding that this weakens some of the sandbox's file protections for those commands.
- If you run Claude Code unattended with `CLAUDE_CODE_RETRY_WATCHDOG` set, you can tune how often it rechecks an early-lifted usage limit with `CLAUDE_CODE_RETRY_WATCHDOG_USAGE_LIMIT_RECHECK_MS`.
- No action is needed for the bug fixes — they apply automatically once you update.

## Source

- [Claude Code CHANGELOG.md — v2.1.305](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21305)
- [Claude Code CHANGELOG.md — v2.1.306](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21306)
