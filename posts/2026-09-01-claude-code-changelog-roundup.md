---
title: "Claude Code changelog roundup: v2.1.252 to v2.1.258"
date: 2026-09-01
description: Claude Fable 5.1 becomes the default Fable model in Claude Code, plus a new time-format setting, tighter auto-mode guardrails, and fixes for macOS launch and remote sessions.
---

## What changed

Claude Code is Anthropic's command-line coding agent. Between August 26 and September 1, 2026, it shipped three notable releases: v2.1.252, v2.1.257, and v2.1.258.

**v2.1.252 (August 26) — bug fixes:**
- Fixed Bash commands failing with a "task output swap refused" error on some Macs.
- Fixed "always allow" permission choices not saving in a project that doesn't yet have a `.claude/settings.local.json` file.
- Fixed Remote Control sessions (hosted by Claude Desktop or VS Code) stalling for minutes after a tool finished, when the connection to claude.ai was degraded.
- Fixed background task notifications with very large failure output (for example, git errors on a full disk) causing the conversation to exceed the API's request size limit.

**v2.1.257 (September 1) — new features:**
- **Claude Fable 5.1** (`claude-fable-5-1`) is now the default Fable model — 1M-token context, $10/$50 per million tokens, with cache reads down to $0.25 per million tokens.
- Added a "Time format" setting (`timeFormat`) and `timeZone` setting: choose 12-hour, 24-hour, 24-hour UTC, or a custom time pattern for timestamps shown in the CLI.
- Added a "Containment Escape" rule to auto mode, so that things like fetching cloud metadata credentials, evading network restrictions, or reaching across tenant boundaries are no longer auto-approved unless your environment explicitly marks them as expected.
- Added `CLAUDE_CODE_SUBAGENT_MODEL_FORCE`, an environment variable that forces every subagent (a helper AI process Claude Code spawns) to use the configured subagent model, overriding any per-agent model settings.
- Added a one-time prompt in auto mode the first time a session reads a file outside its working directories, with an option to block such reads entirely (`permissions.blockReadsOutsideWorkingDirectories`).
- Fixed settings inside a `.claude/` folder created after Claude Code had already started — they now get picked up without needing a restart.
- Fixed sessions started from an agent view sometimes starting in the wrong permission mode instead of the one set for that directory or agent.

**v2.1.258 (September 1) — bug fixes:**
- Fixed Claude Code failing to launch on macOS 12 (Monterey), a regression introduced in v2.1.255.
- Fixed remote and scheduled sessions failing with a "user messages must have non-empty content" error after a re-sent permission approval couldn't be applied.

## Why it matters

The Fable 5.1 default change means anyone running Claude Code with the Fable model line gets the bigger context window and cheaper cache pricing automatically, without changing any configuration. The Containment Escape rule in auto mode is a real security tightening: it closes a gap where auto mode could previously approve actions like fetching cloud credentials or crossing tenant boundaries without asking. The macOS 12 launch fix matters specifically if you were on that older macOS version and Claude Code stopped starting after v2.1.255.

## How to use it

- Update with `claude update`, or through your package manager.
- To pick a fixed time display format, set `timeFormat` (and optionally `timeZone`) in your Claude Code settings.
- To block reads outside your working directory in auto mode, set `permissions.blockReadsOutsideWorkingDirectories`.
- No action is needed for the bug fixes or the Fable 5.1 default switch — they apply automatically after updating.

## Source

- [Claude Code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [v2.1.252 changelog commit](https://github.com/anthropics/claude-code/commit/cad6304)
- [v2.1.257 changelog commit](https://github.com/anthropics/claude-code/commit/a1e64dc)
- [v2.1.258 changelog commit](https://github.com/anthropics/claude-code/commit/aef74af)
