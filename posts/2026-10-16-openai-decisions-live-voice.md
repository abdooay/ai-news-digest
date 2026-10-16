---
title: OpenAI lets its voice model call Decisions directly, mid-conversation
date: 2026-10-16
description: GPT-Live can now call OpenAI's Decisions API on its own while a user is still talking, or react automatically to what either side just said.
---

## What changed

OpenAI added a "native Decisions integration" to **GPT-Live**, its real-time voice model. GPT-Live runs live voice conversations over the network while a separate backend (usually a model or your own app) handles the actual reasoning and actions.

The **Decisions API** is a separate OpenAI tool that answers fixed-choice questions quickly and in a structured way — you define a question with a set list of possible answers, and it picks one.

Until now, if GPT-Live wanted to trigger an action based on what someone said, it had to go through your app: GPT-Live notifies your app, your app calls Decisions, then reports back. That round trip takes time. Two new options skip or change that:

- **Native delegation**: GPT-Live can call Decisions directly, skipping the round trip through your app entirely. Your app sets this up by including a `delegation` object (with `type: "decisions"`, a model, and a list of fixed-choice questions) when starting the live session.
- **Transcript-triggered decisions**: Decisions can run automatically as the conversation's text arrives — either as the user is speaking (`session.input_transcript.delta` events) or as GPT-Live replies (`session.output_transcript.delta` events). This runs independently of delegation and doesn't need your app to ask for it turn by turn.

OpenAI's example use cases: a car voice assistant where saying "make it warmer" sets the cabin temperature, or "why is my windshield fogging up?" triggers turning on the defogger and explaining why; and a digital on-screen character that reacts with matching facial expressions or gestures while the user is still talking.

## Why it matters

For anyone building voice apps on GPT-Live, this cuts the delay between a user's spoken request and the app actually doing something, because the decision no longer has to bounce through your own server first. It also opens up reactions that happen *while* someone is still speaking, rather than only after they finish — useful for things like live facial expressions on an avatar, or safety-relevant actions (like the defogger example) that shouldn't wait for the full sentence.

## How to use it

- Start with a working GPT-Live connection and the `api.decisions.write` permission — no extra beta header is needed for Decisions.
- For native delegation: in your WebRTC session request, add a `delegation` object with `type: "decisions"`, the model to use, and a list of fixed-choice questions (each with a `name`, `instructions`, and set of `choices`). Add instructions in the session telling GPT-Live when to delegate.
- Listen for `session.delegation.created` to get the delegation ID, then watch `decision.event` messages until one reaches `decision.completed`; read each answer by its question name (an answer of `none` means no action was chosen).
- After your app acts on a decision, report the outcome back with `session.commentary.append`, using the same delegation ID.
- For transcript-triggered decisions, add entries to `session.triggers` naming the event type you want (input or output transcript deltas), and match each result to its trigger using `source_event_id`. Results can arrive out of order, so only apply the newest one for each direction.
- If your app filters which WebRTC events it listens to, make sure `session.delegation.created`, `decision.event`, and the transcript event types are allowed through, or these results won't reach your app.

## Source

- [OpenAI API changelog — October 15, 2026](https://developers.openai.com/api/docs/changelog#2026-10-15-decisions)
- [Connect voice to Decisions (guide)](https://developers.openai.com/api/docs/guides/decisions-voice)
