---
title: "OpenAI brings GPT-Live-1's natural voice conversations to the API"
date: 2026-09-11
description: GPT-Live-1, OpenAI's voice model that can listen and speak at the same time, is now available to developers in the API at $0.05 per minute.
---

## What changed

On September 10, 2026, OpenAI released **GPT-Live-1** in the API. GPT-Live-1 first shipped inside ChatGPT; this release makes it available for developers to build into their own voice apps. It's a "full-duplex" voice model, meaning it can listen and speak at the same time — handling interruptions, pauses, and background noise the way a person would, rather than waiting for a person to finish talking before responding (as older "turn-based" voice systems do).

Key details:
- **One model instead of a pipeline.** Traditional voice agents chain together three separate systems — speech-to-text, a text-based reasoning model, and text-to-speech — with each handoff adding delay and losing some of the conversation's natural timing. GPT-Live-1 reasons over incoming and outgoing audio together in a single model, removing those handoffs for the conversational layer.
- **Delegates reasoning to a backend model.** GPT-Live-1 handles the real-time conversation, but can pass deeper reasoning or tool calls to a separate backend model, such as GPT-6 Astra or a third-party model — so a developer might pair it with a fast, cheap model for routine tasks like scheduling, and a more capable model for complex customer issues.
- **Developer controls.** Developers can shape the agent's tone, pace, and conversational style through the system prompt, and the model natively supports turn detection (so you can still build around explicit turn boundaries if you want) alongside its full-duplex mode.
- **Telephony support**, for building voice agents that handle phone calls.
- **New voice options.** OpenAI is expanding from a small set of real-time voices to a wider selection of accents, dialects, and languages.
- **Benchmarks.** OpenAI reports GPT-Live-1 improves on its "Full Duplex Bench" evaluation by 30 percentage points over the previous GPT-Realtime-2.1 model, and that pairing it with GPT-6 Astra ranks first on Tau3, an evaluation of end-to-end voice-agent task performance. In an early evaluation with the language-learning company Speak, GPT-Live-1 cut conversation interruptions by almost 80% compared with the previous turn-based system.

## Why it matters

Voice apps built the traditional way (chaining separate speech-to-text, reasoning, and text-to-speech systems) tend to feel stilted, because each handoff adds delay and makes natural interruptions hard to handle gracefully. A single model that processes both directions of audio at once can respond and get interrupted more naturally, which matters for anything meant to feel like a real conversation — customer support lines, reservation systems, or language tutoring. Letting the voice layer delegate deep reasoning to a separate backend model also means developers aren't forced to choose one model for both the conversational feel and the intelligence behind it — they can optimize each independently.

## How to use it

- GPT-Live-1 is available in the API today, priced at $0.05 per minute for the front-end voice layer (separate from whatever backend model you pair it with).
- Pair it with a backend model — such as GPT-6 Astra for complex reasoning, or a lighter model for simple, high-volume tasks — through OpenAI's Realtime/Live API guide.
- Shape the voice's tone and style through the system prompt, and choose from the expanded set of voice options.
- For access to custom or restricted voice options, contact OpenAI sales.

## Source

- [Build more natural voice experiences with GPT-Live-1 in the API](https://openai.com/index/introducing-gpt-live-1-in-the-api/)
