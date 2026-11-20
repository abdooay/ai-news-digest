---
title: "GPT-Live-1.1 arrives in the OpenAI API, with a cheaper standby mode"
date: 2026-11-20
description: OpenAI's voice model GPT-Live-1.1 is now available to developers through the API, along with a new lower-cost standby mode for quiet moments in a call.
---

## What changed

OpenAI made **GPT-Live-1.1** available in its API on November 20, 2026. GPT-Live is OpenAI's model for building voice agents — software that has spoken conversations with people. GPT-Live-1.1 has already been powering voice chats in ChatGPT Plus and Pro since October 15; now developers can use the same model in their own apps with the model ID `gpt-live-1.1`.

OpenAI says the model gives more natural and consistent accents across languages, understands precise details like letters and numbers more reliably, and follows instructions and completes tasks more consistently than before. It can also listen while it is speaking, and it can hand off complex work to a separate "backend" model of the developer's choice without breaking the flow of the conversation.

Alongside the model, OpenAI added a new feature called **standby**, available for both GPT-Live-1 and GPT-Live-1.1. Standby lets a developer set an idle timeout of 5 to 60 seconds. If nobody speaks for that long, the model pauses while the call's connection (over WebRTC, the technology browsers use for live audio and video) stays open. The conversation picks back up as soon as someone speaks again.

Standby is billed at $0.02 per minute, compared with the normal active rate of $0.05 per minute. The cost of the backend model and any tools it uses is billed separately.

## Why it matters

For developers building voice assistants, standby is a direct cost saver: a call that sits quiet — someone thinking, stepping away, or a pause between questions — now costs less than one where the model is actively listening and responding. Previously, a quiet moment in a call cost the same as an active one.

The accuracy improvements (accents, precise details like numbers and letters, instruction-following) matter for use cases like phone support or data entry by voice, where getting a detail wrong is costly. The ability to delegate to a separate backend model while still talking means a voice agent can do heavier reasoning or lookups without the conversation feeling like it froze.

## How to use it

- Call the API with model ID `gpt-live-1.1` to use the new model.
- To turn on standby, set an idle timeout between 5 and 60 seconds in your GPT-Live session configuration, as described in OpenAI's [live conversations guide](https://developers.openai.com/api/docs/guides/live-conversations#configure-standby).
- Standby works with both `gpt-live-1` and `gpt-live-1.1`.
- See the [model documentation](https://developers.openai.com/api/docs/models/gpt-live-1.1) for full details before switching a production voice app.

## Source

- [OpenAI Community: GPT-Live-1.1 has arrived in the API](https://community.openai.com/t/gpt-live-1-1-has-arrived-in-the-api/1418537)
