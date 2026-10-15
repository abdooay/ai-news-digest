---
title: "Claude Code changelog roundup: v2.1.294 to v2.1.296"
date: 2026-10-15
description: Claude Code hooks now actually block what they're written to block, failed hooks can halt an action instead of letting it through, and subagents get their own auto-compact window.
---

## What changed

Claude Code is Anthropic's command-line coding agent. Between October 8 and October 9, 2026, it shipped three releases: v2.1.294, v2.1.295, and v2.1.296.

**v2.1.294 — hook reliability fix:**
- Fixed `prompt` and `agent` hooks written as plain-English instructions (for example, "Block commands that...") sometimes allowing exactly what they were supposed to block. A "hook" here is a rule you set up that runs automatically — this fix makes those plain-English rules actually enforce what they say.
- Improved how `prompt` hooks on Stop and SubagentStop (rules written like "Carry on if the build is broken") are judged, so Claude is less likely to stop a task early when it shouldn't.

**v2.1.295 — new features and fixes:**
- Added `onFailure: "block"` for command and HTTP hooks: if a hook can't start, times out, or exits with an error, the action it was guarding is now blocked instead of being let through by default.
- Added Program Status Protocol (OSC 7501) support, so compatible terminals can show whether Claude Code is working, waiting on you, or done — without you having to look at the window.
- Many smaller fixes: remote MCP servers (external tool connections) no longer get stuck in reconnect loops after an outage; `claude -p` (non-interactive mode) no longer drops earlier responses when background work starts a new turn; and several Windows-specific and VS Code fixes.

**v2.1.296 — new features and fixes:**
- Added `autoCompactWindow` to subagent definitions, so a subagent (a helper AI process Claude Code spawns for a subtask) can be set to auto-compact its conversation earlier than the main session does. "Compacting" means summarizing older conversation history to free up space.
- Added `CLAUDE_CODE_OVERLOADED_RETRY_MAX_DELAY_MS`, an environment variable to set a longer maximum wait time when Claude Code retries after a "server overloaded" (529) error.
- Added an `allow_large` option to the Read tool, letting Claude read an oversized text file in full in one call when it genuinely needs the whole thing.
- Updated pricing shown in `/cost` and the status line: Claude Sonnet 5.5 prompt cache reads now show as $0.10 per million tokens, down from $0.20 — matching the price cut Anthropic made on the API side.
- Fixed token counts for Claude Haiku 5.5 and other "adaptive thinking only" models, which were being counted incorrectly behind some gateways.
- Fixed a bug where resumed subagents could be wrongly told that you'd rejected a tool call, when it was actually a session shutdown that interrupted it.

## Why it matters

The v2.1.294 hook fix is the most important of the three for anyone relying on plain-English hook rules for safety or compliance: if your "block dangerous commands" rule was silently not blocking anything, it's fixed now. The `onFailure: "block"` option in v2.1.295 is a meaningful default-safety change — previously, if a safety hook crashed or timed out, the action it was supposed to stop could go through anyway; now you can make a broken hook fail closed instead of fail open.

## How to use it

- Update with `claude update`, or through your package manager.
- To make a hook fail closed instead of open, set `onFailure: "block"` on that hook's definition.
- To give a subagent its own compaction window, set `autoCompactWindow` in its frontmatter or `--agents` definition.
- No action is needed for the pricing display update or the other bug fixes — they apply automatically after updating.

## Source

- [Claude Code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [v2.1.294 changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21294)
- [v2.1.295 changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21295)
- [v2.1.296 changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#21296)
