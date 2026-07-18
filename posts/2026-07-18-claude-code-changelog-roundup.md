---
title: "Claude Code changelog roundup: v2.1.207 to v2.1.214"
date: 2026-07-18
description: A week of Claude Code CLI releases, from auto mode on more cloud providers to a new EndConversation tool and dozens of Windows and background-session fixes.
---

## What changed

Claude Code is Anthropic's command-line coding agent. Between July 11 and July 18, 2026, it shipped seven versions (v2.1.207, v2.1.208, v2.1.209, v2.1.210, v2.1.211, v2.1.212, and v2.1.214). Here are the changes that affect how people actually use it, grouped by release.

**v2.1.207 (July 11)**
- "Auto mode" — a mode that replaces manual permission prompts with automatic background safety checks — no longer needs a manual opt-in on Amazon Bedrock, Google Vertex AI, and Microsoft Foundry (three cloud platforms that host Claude).
- On those same three platforms, the default model changed to Claude Opus 4.8.
- Fixed the terminal freezing or lagging while Claude streamed long responses (big lists, tables, or code blocks).

**v2.1.208, v2.1.209, v2.1.210 (July 14)**
- Added an opt-in **screen reader mode** (plain-text rendering for screen reader users): run `claude --ax-screen-reader`, set `CLAUDE_AX_SCREEN_READER=1`, or add `"axScreenReader": true` to settings.
- Added `vimInsertModeRemaps`, a setting to map two-key sequences like `jj` to Escape for people using Vim-style editing in the terminal.
- Sped up tool calls in scripted/SDK sessions that use many MCP (Model Context Protocol) tools — Anthropic says up to 7x faster tool rounds at high tool counts — and cut memory use by pruning old file-edit history and capping several memory leaks in long sessions.
- Added a live elapsed-time counter on long-running tool calls, so they visibly tick instead of looking stuck.
- Fixed several crash and data-loss bugs in background sessions (sessions that keep running after you step away), including lost replies, crashes on certain network disconnects, and stuck "job not found" errors.
- Reverted a bug that had been blocking dialogs like `/model` inside background sessions.

**v2.1.211 (July 15)**
- Fixed a billing bug: on Bedrock, Vertex, Mantle, and Foundry, a caching regression had been charging the trailing system-context block as fresh input tokens on every request instead of using the cheaper cached-token rate.
- Added a `--forward-subagent-text` flag so scripted output can include a subagent's text and reasoning.
- Fixed subagents (helper agents spawned during a session) reverting to the parent session's model instead of keeping their own explicitly-set model after being resumed.
- Fixed `/clear` not resetting the on-screen cost counter back to $0.
- Security fix: permission-approval previews sent to chat channels (like Slack) could be visually altered using invisible or look-alike characters; these are now stripped so what you approve is what was actually requested.

**v2.1.212 (July 17)**
- `/fork` now copies your current conversation into a new background session instead of spawning an in-session helper; the old in-session behavior moved to a new `/subtask` command.
- Added session-wide limits on web searches (default 200) and subagent spawns (default 200) to stop runaway loops, both configurable via environment variables.
- MCP tool calls that run longer than 2 minutes now move to the background automatically instead of blocking the session.
- Fixed plan mode letting file-changing commands (like `touch` or `rm`) run without asking for permission first — a real safety bug.

**v2.1.214 (July 18)**
- Added an **EndConversation** tool: Claude can now end a session on its own when a user is highly abusive or attempting a jailbreak, matching behavior already used on claude.ai.
- Several permission-check fixes, including commands that could previously bypass approval prompts on Windows PowerShell 5.1 and in certain Bash redirect forms.
- Added permission prompts for `docker` commands that redirect to a remote Docker daemon (previously these ran without asking).
- Fixed a crash when a feature-flag check returned an unexpected null value.

## Why it matters

Most of these are incremental fixes, but three stand out. First, the Bedrock/Vertex/Mantle/Foundry billing fix in v2.1.211 means people running Claude Code through those cloud platforms may have been overpaying for input tokens that should have been cheaper cached tokens — that's now corrected. Second, several security fixes (permission-check bypasses on Windows, the chat-preview spoofing fix, the plan-mode safety bug) close real gaps where a command could run without the user's explicit approval. Third, auto mode losing its opt-in requirement on Bedrock, Vertex, and Foundry means more people will hit that automatic-approval behavior by default on those platforms.

## How to use it

- Update Claude Code normally (`claude update`, or your package manager) to get these fixes; version 2.1.214 is the latest as of this post.
- To turn on screen reader mode: `claude --ax-screen-reader` or set `CLAUDE_AX_SCREEN_READER=1`.
- To tune the new runaway-loop limits: set `CLAUDE_CODE_MAX_WEB_SEARCHES_PER_SESSION` and `CLAUDE_CODE_MAX_SUBAGENTS_PER_SESSION`.
- If you use Claude Code on Bedrock, Vertex, Mantle, or Foundry, no action is needed for the billing fix — it's automatic — but check recent invoices if you want to confirm the difference.

## Source

- [Claude Code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [v2.1.207](https://github.com/anthropics/claude-code/commit/d4d8fbb)
- [v2.1.208](https://github.com/anthropics/claude-code/commit/1fb278b)
- [v2.1.209](https://github.com/anthropics/claude-code/commit/988b3e5)
- [v2.1.210](https://github.com/anthropics/claude-code/commit/b7784f2)
- [v2.1.211](https://github.com/anthropics/claude-code/commit/c39cb0f)
- [v2.1.212](https://github.com/anthropics/claude-code/commit/67f390c)
- [v2.1.214](https://github.com/anthropics/claude-code/commit/07dcb0e)
