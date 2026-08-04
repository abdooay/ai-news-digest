---
title: OpenAI rebuilt its realtime voice system for GPT-Live
date: 2026-08-04
description: OpenAI replaced its Python-based voice pipeline with a new Go-based system that listens and speaks at the same time and hands off mid-call without dropping the connection.
---

## What changed

On August 3, 2026, OpenAI published details of a rewrite of the realtime voice system behind GPT-Live, the model that powers ChatGPT's voice features. OpenAI calls it their "third-generation voice system."

Key changes described in the post:
- The new system is **full-duplex**: the model can listen and speak at the same time, instead of waiting for a "turn detector" to decide when the user has stopped talking before it can respond. OpenAI says this removes the turn detector from the audio path entirely.
- The underlying voice-handling code was rewritten from Python (using `asyncio`) to **Go**, which OpenAI says brought the 95th-percentile (p95) response latency down to roughly what the old system's median (p50) latency was.
- The system separates the core voice path (audio in, audio out) from application logic, so the model can consult a more powerful "frontier" model — OpenAI names GPT-5.5 as an example — mid-conversation without interrupting the flow of speech.
- A **seamless handoff** mechanism lets OpenAI swap in a new model instance with the current conversation's context while the old instance keeps running, and a **dynamic context compaction** step trims long-running call history when needed, both without interrupting the audio stream.
- Connections use WebRTC as the transport layer, plus a custom protocol OpenAI calls **WARP** to speed up the initial connection handshake, and an **Instant Connect** feature that pre-negotiates connection parameters without reserving server capacity ahead of time — OpenAI says this cut the data needed to start a session down to a single network packet.
- Before switching over, OpenAI tested the new system by gradually routing a small, increasing share of real production voice sessions to it alongside the old system, comparing results directly.

## Why it matters

For users, a full-duplex, lower-latency voice system means conversations with ChatGPT's voice mode should feel less like a walkie-talkie (wait for a beep, then talk) and more like a normal back-and-forth conversation, since the model can react while you're still speaking and doesn't need to fully re-establish a slow handshake to start a call. OpenAI says this system already powers expanded ChatGPT Voice features, including letting the voice assistant control your computer and coordinate other agents on your behalf.

## How to use it

This is infrastructure behind ChatGPT's existing voice features, not a new setting — there's nothing to turn on. OpenAI says a public **GPT-Live API** is planned, which would let developers build on this system directly, along with expansion to more devices, apps, and modalities. Watch OpenAI's developer documentation for that API to ship before building against it.

## Source

- [OpenAI: "Continuous voice interaction with GPT Live"](https://openai.com/index/continuous-voice-interaction-with-gpt-live/)
