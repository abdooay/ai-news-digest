---
title: "Claude API: request a conversation summary on demand"
date: 2026-09-16
description: The Messages API can now compact (summarize) a conversation whenever you ask, as a background request that doesn't interrupt the active task.
---

## What changed

On September 14, 2026, the Claude Platform release notes announced on-demand compaction for the Messages API (the core API developers use to send conversations to Claude). "Compaction" means asking Claude to summarize older parts of a conversation so it takes up less space in the context window (the limited amount of text a model can consider at once).

Claude API already had automatic, threshold-based compaction, which kicks in when a conversation gets close to the context limit. This is different: it's a compaction you request yourself, at any point, using the new `compaction` parameter. It's in beta, turned on by sending the `compact-2026-09-04` beta header with your request.

How it works: you send a request with `compaction` set, and instead of a normal reply, the API returns a signed "compaction block" — a summary of the messages you sent. On your next request, you send that block in place of the original messages it summarizes, which shortens what you send while keeping the gist. This request runs separately from your normal conversation turns and returns only the summary, so it can happen in the background without blocking the actual task. You can also choose to keep some recent messages word-for-word instead of folding them into the summary. On models that support preserved thinking (keeping a model's step-by-step reasoning valid across turns), the thinking in those word-for-word turns stays valid.

## Why it matters

For long, multi-step tasks — for example, an agent that makes many tool calls over a long-running job — conversation history can grow large enough to crowd out useful context or slow things down. Automatic compaction handles this reactively, but it happens as part of the live conversation turn. On-demand compaction lets a developer summarize proactively, on their own schedule, as a background request that doesn't interrupt or delay the actual task the model is working on. Being able to keep the most recent turns word-for-word also means recent, detailed context isn't lost to summarization even while older history is condensed.

## How to use it

- Add the beta header `compact-2026-09-04` to your Messages API request (this is a different header from the one used for automatic threshold compaction, `compact-2026-01-12`).
- Send a request with the top-level `compaction` parameter set (for example, `compaction="summarize"`). The API returns a `compaction` block instead of a normal reply.
- On your next request, replace the summarized messages with that `compaction` block, keeping any recent messages you want preserved exactly as they were.
- Use the `/v1/messages/count_tokens` endpoint if you want to check the token count after swapping in the compaction block.

## Source

- [Claude Platform release notes — September 14, 2026](https://platform.claude.com/docs/en/release-notes/api#september-14-2026)
- [Compact a conversation on demand with the `compaction` parameter](https://platform.claude.com/docs/en/build-with-claude/compaction#compact-on-demand-with-the-compaction-parameter)
