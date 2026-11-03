---
title: Claude API adds message threads to speed up long conversations
date: 2026-11-03
description: A new beta feature lets you send only new messages in a long conversation instead of re-sending the whole thing every time.
---

## What changed

On November 2, 2026, Anthropic added a beta feature called **message threads** to the Claude API (the Messages API that developers use to send conversations to Claude). It's also available on Claude Platform on AWS, Claude Models on Google Cloud, and Claude in Microsoft Foundry.

Normally, every time you send a new message in a conversation with Claude, your app has to send the *entire* conversation history again — every earlier message, the system prompt, and the list of tools. The API has to re-read and re-check all of that every single time. With a message thread, the API keeps the conversation on its servers for a short time. After the first message, you only need to send the new part.

A thread lasts 5 minutes after its last use, and is automatically deleted within 1 hour of its last use either way.

## Why it matters

For short chats this barely matters, but it adds up fast in **long conversations and AI agents that loop many times** (keep calling Claude back and forth to complete a task). Each loop used to mean re-sending a growing wall of text. With threads, each loop sends only the newest bit, which means:

- Smaller requests, so less data goes over the network each time.
- A lower and steadier "time to first token" (how long you wait before Claude starts responding), even as the conversation grows long.

This is a beta feature, so it may change before it becomes standard, and it isn't eligible for "zero data retention" (a setting where Anthropic promises not to store any of your data) — though Anthropic says a thread's contents are held encrypted in memory, never written to permanent storage, and deleted within an hour of last use.

## How to use it

To try it, add the beta header `message-threads-2026-08-12` to your API request, plus a new `thread` parameter:

1. **First message:** send the full conversation (system prompt, tools, first user message) as usual, but add `"thread": {"type": "create"}`. The response includes an `id` you'll need next.
2. **Follow-up messages:** send only the new message(s), plus `"thread": {"type": "continue", "previous_message_id": "<id from the previous response>"}`. Leave out the system prompt and tools — the thread remembers them.
3. Keep using the latest response's `id` for each new turn.

If a thread expires or can't be continued (the API returns a `thread_not_found` error), just send the full conversation again in a new "create" request — your app should always keep its own full copy of the conversation as a backup, since threads are best-effort and not guaranteed to survive.

Anthropic's official SDKs (Python, TypeScript, Go, Java, C#, PHP, Ruby) include a helper (`client.beta.messages.thread(...)`) that handles the create/continue logic, retries, and edge cases for you.

Pricing and rate limits are unchanged — threads don't cost extra.

## Source

- [Claude API release notes — November 2, 2026](https://platform.claude.com/docs/en/release-notes/api#november-2-2026)
- [Message threads guide](https://platform.claude.com/docs/en/build-with-claude/message-threads)
