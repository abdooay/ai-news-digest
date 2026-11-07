---
title: "OpenAI API roundup: GPT-6-Cyber, GPT-Image-2.6, and outbound SIP calling"
date: 2026-11-07
description: OpenAI's API changelog added GPT-6-Cyber for authorized security testing, two new GPT-Image-2.6 models with markup-guided editing, and outbound phone calling through the Live API.
---

## What changed

Three items landed in OpenAI's developer API changelog over the past week:

**GPT-6-Cyber (November 5, 2026).** A new model for cybersecurity work: investigating vulnerabilities, reproducing them in an authorized test environment, and verifying fixes. It's gated behind "Daybreak," OpenAI's set of cybersecurity access programs (Daybreak Blue and Daybreak Red). To use GPT-6-Cyber you need Daybreak Red access and extra model approval from OpenAI, and requests must set a field called `access_programs.cyber` to `daybreak_red`. OpenAI is explicit that this field only "selects behavior within your approved access; it doesn't grant access" — approval has to come first. Daybreak Red organizations also have to require SSO and enforce MFA for the organization holding Cyber access, enable the program per-project, and set up an IP allowlist before sending requests.

**GPT-Image-2.6 Sunburst and Flare (November 4, 2026).** Two new image generation and editing models, reachable through the existing `/v1/images/generations` and `/v1/images/edits` endpoints. OpenAI describes Sunburst as suited to detailed visual work and Flare to fast iteration, though it gives no further technical specifications distinguishing the two. Both support:
- **Adjustable complexity** — a new `complexity` field (`low`, `medium`, or `high`, defaulting to `high`) that controls how much the model plans before rendering an image. Lower complexity suits quick, focused edits; higher complexity helps with dense text or complex layouts, at the cost of more latency and a higher chance of unwanted changes. This is separate from the existing `quality` field and doesn't carry a separate fee.
- **SVG and animated GIF output**, in addition to normal raster images.
- **Markup-guided editing**, also added to supported GPT Image 2.5 and 2.6 models: you send the original image plus a transparent annotation layer (such as a circle or sketch) as a new `markup` parameter on `/v1/images/edits`, along with a text prompt describing the change. The annotation layer must match the original image's dimensions and can't be flattened into it, and `markup` can't be combined with the existing `mask` parameter.

**Outbound SIP calling, generally available (November 2, 2026).** The Live API (OpenAI's real-time voice API, used by GPT-Live) can now place outbound phone calls through a SIP trunking provider, for all organizations. To use it you need a SIP provider that supports TLS signaling and SDES-SRTP encrypted audio, trunk credentials, and phone numbers in E.164 format (the standard international format, e.g. `+14155551234`). You start a call by sending a session-creation request to `/v1/live/sessions` with a `transport` object set to `type: "sip"`; a successful response means the session started, not that the call was answered. You then attach a WebSocket to track call progress events like `transport.ringing` and `transport.answered`, and use separate controls for hangup, call transfer, and DTMF (phone keypad) tones. Ringing times out after 3 minutes, and a connected call is capped at 2 hours.

## Why it matters

GPT-6-Cyber is narrowly aimed at authorized security teams — penetration testers, red teams, and similar — and is deliberately hard to get access to, with SSO, MFA, IP allowlisting, and per-project approval all required before the first request. It's not something a typical developer can turn on casually.

The GPT-Image-2.6 changes matter more broadly: adjustable complexity gives developers a lever to trade off speed against image quality on a per-request basis, and markup-guided editing offers a more precise way to tell the model exactly what part of an image to change, instead of relying only on a prompt or a hard mask. SVG and animated GIF output also open up use cases — like icons, logos, or short looping animations — that plain raster image generation doesn't cover well.

Outbound SIP calling matters for anyone building voice agents that need to place real phone calls — for example, automated appointment reminders or outbound customer support — without routing everything through a separate telephony platform.

## How to use it

- **GPT-6-Cyber**: contact your OpenAI account team to confirm Daybreak Red access and model approval, then send Responses API requests with `model: "gpt-6-cyber"` and `access_programs.cyber: "daybreak_red"`.
- **GPT-Image-2.6**: call `/v1/images/generations` or `/v1/images/edits` with `model` set to `gpt-image-2.6-sunburst` or `gpt-image-2.6-flare`, and add `complexity: "low" | "medium" | "high"` to control planning effort. For markup-guided edits, send the original image as the first input image plus a same-size transparent PNG annotation layer as `markup`, with a prompt describing the change — don't combine `markup` with `mask`.
- **Outbound SIP calling**: set up a SIP trunking provider with TLS and SRTP enabled, then send a `POST` to `/v1/live/sessions` with a `transport` object (`type: "sip"`, destination number, and trunk settings), and attach a WebSocket to `wss://api.openai.com/v1/live/sessions/{session_id}/attach` right away to monitor call progress.

## Source

- [OpenAI API changelog — GPT-6-Cyber, November 5, 2026](https://developers.openai.com/api/docs/changelog#november-5-2026)
- [OpenAI API changelog — GPT-Image-2.6, November 4, 2026](https://developers.openai.com/api/docs/changelog#november-4-2026)
- [OpenAI API changelog — outbound SIP calling, November 2, 2026](https://developers.openai.com/api/docs/changelog#november-2-2026)
- [Daybreak and GPT-6-Cyber setup guide](https://developers.openai.com/api/docs/guides/daybreak)
- [Image generation guide — GPT-Image-2.6](https://developers.openai.com/api/docs/guides/image-generation)
- [SIP voice guide](https://developers.openai.com/api/docs/guides/voice-sip?api=live)
