---
title: "Claude Code v2.1.307–308: API version migration command, safety telemetry, @claude review stop"
date: 2026-10-22
description: Claude Code v2.1.307 adds a command to migrate Claude API code to a newer API version plus new safety telemetry and a Code Review stop command; v2.1.308 is a small reliability-only release.
---

## What changed

Claude Code is Anthropic's command-line coding agent. Two versions shipped this week.

**v2.1.307** (the bigger of the two):
- **New `/claude-api api-version` command.** This helps migrate code that calls the Claude API from an older API version to a newer one, instead of doing it by hand.
- **New safety telemetry event.** A new OpenTelemetry (an open standard for collecting operational data) event, `claude_code.safety_event`, now records whenever a permission rule, auto mode, a safety check, a hook, or the sandbox stops or redirects a tool call. Organizations that monitor Claude Code usage can now see this centrally instead of only in the session transcript.
- **New Code Review command.** Teams using Claude's automated Code Review feature on pull requests can now comment `@claude review stop` to stop an in-progress review.
- **Bug fixes**, including: errors with `[1m]` long-context model aliases being wrongly reported as "model not found"; beta headers being sent to gateways or Microsoft Foundry where they have no effect; several MCP (Model Context Protocol) server issues on macOS and Linux, including sleep-related timeouts and duplicate tool calls; repeated unnecessary auto-compaction ("autocompact thrashing"); and WebFetch and Artifact tool errors.
- **Other changes**: Claude Code now retries up to twice when a tool call comes back malformed instead of failing immediately; the message warning about running low on web-search budget now also tells Claude not to work around the limit using a browser or computer-use tool; checkout hooks (scripts that run when switching code versions) now time out after 30 minutes by default instead of running indefinitely; and VS Code gets several fixes, including to voice dictation and LaTeX paste handling.

**v2.1.308** (a small follow-up):
- Bug fixes and reliability improvements only — the changelog doesn't list individual items beyond this.

## Why it matters

The `/claude-api api-version` command matters if you have code calling the Claude API directly and want to move it onto a newer API version without manually rewriting requests. The new safety telemetry event is useful for any organization that wants a central, auditable record of when Claude Code's guardrails actually intervened, rather than having to check each session individually. The 30-minute default timeout on checkout hooks is worth knowing about if you have a long-running hook script — it will now be killed after 30 minutes unless you configure it differently.

## How to use it

- Update with `claude update`, or through your package manager, to get these changes.
- Run `/claude-api api-version` to migrate Claude API calls in your code to a newer API version.
- To collect the new safety event, set up OpenTelemetry export and watch for `claude_code.safety_event`.
- Comment `@claude review stop` on a pull request to stop an in-progress Code Review.
- No action is needed for the bug fixes in either version — they apply automatically once you update.

## Source

- [Claude Code CHANGELOG.md — v2.1.307](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21307)
- [Claude Code CHANGELOG.md — v2.1.308](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21308)
