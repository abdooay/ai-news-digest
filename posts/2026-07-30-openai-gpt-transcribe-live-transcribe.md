---
title: OpenAI launches GPT-Transcribe and GPT-Live-Transcribe
date: 2026-07-30
description: Two new speech-to-text models replace Whisper and gpt-4o-transcribe, one for finished audio files and one for low-latency live streaming.
---

## What changed

OpenAI released two new transcription models in its API:

- **GPT-Transcribe** — turns speech into text for completed audio files, streamed file transcripts, and finished turns in Realtime sessions. It works through the standard transcription endpoint (`v1/audio/transcriptions`) and the Realtime transcription endpoint (`v1/realtime/transcription_sessions`).
- **GPT-Live-Transcribe** — a streaming model built for low-latency transcription of live audio, so an app can get text back in near real time as someone speaks. It's only available through the Realtime transcription endpoint.

Both models let a developer pass extra context to improve accuracy: free-form background text about the recording, a list of keywords (like names or technical terms likely to appear), and a list of expected input languages.

On OpenAI's own benchmarks, accuracy improved over the previous models: across 22 languages the error rate dropped from 20.33% to 19.70%, and on a set of real-world audio in nine languages it dropped from 11.65% to 9.60%. Adding free-form context to GPT-Live-Transcribe raised semantic accuracy from 38.5% to 44.6%.

Pricing: GPT-Transcribe costs $0.0045 per minute of audio. GPT-Live-Transcribe costs $0.017 per minute of realtime audio.

## Why it matters

"Transcription" means converting spoken audio into written text. If you build apps that caption live audio (like meeting notes or voice assistants), GPT-Live-Transcribe is meant to replace older models for that job with faster, more accurate output. If you process recorded files after the fact (podcasts, call recordings, uploaded videos), GPT-Transcribe is the one to use, and it's cheaper per minute than the previous whisper-1 and gpt-4o-transcribe models. The added context options (keywords, languages) mean fewer garbled results on names, jargon, or accents that older models tended to mishear.

## How to use it

- For finished audio files, call `v1/audio/transcriptions` with `model` set to `gpt-transcribe`.
- For live or streaming audio, open a session on `v1/realtime/transcription_sessions` with `model` set to `gpt-live-transcribe` (or `gpt-transcribe` for transcript deltas on committed turns).
- Optionally pass a `prompt` (free-form context), `keywords`, and expected `languages` to improve accuracy on domain-specific audio.

## Source

- [OpenAI Developer Community: "GPT-Live-Transcribe and GPT-Transcribe: Two New Transcription Models in the API"](https://community.openai.com/t/gpt-live-transcribe-and-gpt-transcribe-two-new-transcription-models-in-the-api/1388318)
- [OpenAI API docs: GPT Transcribe model](https://developers.openai.com/api/docs/models/gpt-transcribe)
- [OpenAI API docs: GPT Live Transcribe model](https://developers.openai.com/api/docs/models/gpt-live-transcribe)
