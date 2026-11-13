---
title: "Claude Code v2.1.323: Code Mode lets Claude write JavaScript to call its tools"
date: 2026-11-13
description: Claude Code's new experimental Code Mode has Claude write small JavaScript programs to call its tools instead of calling them one at a time, plus dozens of smaller fixes.
---

## What changed

Claude Code, Anthropic's command-line coding agent, shipped version 2.1.323. It's a large release — the changelog lists well over 150 fixes and additions — but the headline feature is **Code Mode**.

Normally, when Claude Code wants to do several things — read a file, run a command, check the result, run another command — it makes one tool call, waits for the result, then makes the next one. Code Mode is a new experimental, opt-in mode where Claude instead writes a short piece of JavaScript that calls its tools directly, and that whole script runs before Claude sees the combined output. It's off by default; the changelog points to `https://code.claude.com/docs/en/code-mode` to turn it on, or for an organization to turn it off.

Other notable additions in this release:
- A new options menu (stop, switch to usage credits, or upgrade) appears when a model needs usage credits that are turned off or used up.
- The Artifact tool's asset uploads now support `.docx` files.
- A one-time startup notice now names the `CLAUDE_CODE_PERFORCE_MODE` environment variable when Perforce settings are detected but the mode is off.
- In VS Code, Claude Code now asks you to trust a folder before starting a session there, and shows the live output of a running Bash or PowerShell command directly under its card in the chat.
- Many Claude Code on the web (cloud sessions) and Remote Control reliability fixes: better messages when a file upload fails, reconnect buttons for disconnected sessions, and fixes for sessions getting stuck showing "Sending" or "Disconnected."

The rest of the release is bug fixes and small quality-of-life improvements across permissions, MCP (Model Context Protocol) servers, plugins, OpenTelemetry logging, and the Windows and VS Code integrations — too many to list individually here; see the full changelog linked below.

## Why it matters

Calling tools one at a time is simple but slow when a task needs many small steps: each step is a round trip through the model. Code Mode's idea — write code that chains several tool calls together and runs them before coming back — can cut down on that back-and-forth for tasks that are naturally a sequence of steps, similar to patterns other coding tools (like Cloudflare's "Code Mode" or OpenCode) have also been exploring. Because it's experimental and opt-in, it won't change how Claude Code behaves for anyone who doesn't turn it on.

Most people won't notice this release at all beyond a smoother, more reliable experience: the long fix list touches permission checks, sign-in handling, and cloud session stability, which mainly show up as "fewer weird bugs" rather than new things to learn.

## How to use it

- Update with `claude update`, or through your package manager, to get version 2.1.323.
- To try Code Mode, follow the instructions at `code.claude.com/docs/en/code-mode`. Organizations that want to prevent it can turn it off the same way.
- No action is needed for the other fixes — they apply automatically once you're on this version.

## Source

- [Claude Code CHANGELOG.md — v2.1.323](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21323)
