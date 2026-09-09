---
title: "ChatGPT Images 2.5: faster image generation, sketch-to-image, and two new API models"
date: 2026-09-09
description: OpenAI's new image model produces sharper, more consistent images up to 50% faster than the previous version, adds a sketch tool, and ships as two new models in the API.
---

## What changed

OpenAI announced ["Introducing ChatGPT Images 2.5"](https://openai.com/index/introducing-chatgpt-images-2-5/) on September 8, 2026, an update to its image generation model. OpenAI says people already create more than 3 billion images per week across ChatGPT Images and the GPT-Image models in its API.

Compared with the previous version (Images 2.0), OpenAI says Images 2.5:
- Produces sharper details, more natural lighting, and richer textures.
- Preserves the subject of an image more consistently, especially across multiple edits in a row.
- Understands complex instructions better and handles transparent backgrounds.
- Generates images with up to 50% lower latency (the time you wait for an image to appear).

New features in ChatGPT itself:
- **Sketch**: draw a rough layout or concept directly in ChatGPT as a visual reference, which the model then uses to generate a finished image.
- **Templates**: preset formats for common needs like posters or merchandise designs.
- **Commenting**: place comments directly on specific parts of an image to guide a more targeted edit.
- **Prompt sharing**: share the prompt behind an image so someone else can try the same idea with their own photos or details.

This rolls out starting September 8 to ChatGPT, ChatGPT Work, and Codex users across all plan tiers, on desktop, mobile, and web. For developers, OpenAI is also releasing two new API models: GPT-Image-2.5 Flare (the default, with the ~50% latency reduction) and GPT-Image-2.5 Sunburst (a slower, higher-precision option). OpenAI's announcement did not include specific pricing for either the consumer rollout or the two new API models.

## Why it matters

If you use ChatGPT for image generation or editing, the update should apply automatically with no setup — faster results and better consistency across edits are the main practical gains. The Sketch feature is useful if you already have a rough idea of layout or composition and want the model to follow it rather than generating from a text description alone. For developers, having two model options (a fast default and a higher-precision alternative) lets you trade off speed against image quality depending on the use case, similar to how OpenAI offers different tiers of its text models.

## How to use it

- In ChatGPT, ChatGPT Work, or Codex, image generation and editing now use Images 2.5 by default — no setting to change.
- Try the Sketch tool when starting a new image: draw a rough layout first, then describe what you want, and the model uses your sketch as a reference.
- Use Templates for common formats like posters or merch designs instead of describing the layout from scratch.
- Developers: call the API with model `gpt-image-2.5-flare` for faster, lower-cost generation, or `gpt-image-2.5-sunburst` for higher-precision output. Check OpenAI's API documentation for exact parameters and current pricing before switching production workloads.

## Source

- [OpenAI: Introducing ChatGPT Images 2.5](https://openai.com/index/introducing-chatgpt-images-2-5/)
