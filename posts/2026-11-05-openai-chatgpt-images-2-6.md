---
title: "ChatGPT Images 2.6 adds GIFs, reusable reference images, and two new API models"
date: 2026-11-05
description: OpenAI's new image model lets you make animated GIFs and save reference images for reuse, and ships as two new, faster API models.
---

## What changed

OpenAI announced **ChatGPT Images 2.6** on November 4, 2026, an update to its image generation tool in ChatGPT, alongside two new image models for developers: **GPT-Image-2.6 Flare** and **GPT-Image-2.6 Sunburst**.

New features in ChatGPT:
- **Animated GIFs**: turn a prompt or an existing image into an animated GIF. You can adjust the playback speed and edit individual frames.
- **Reusable reference images**: save reference images of yourself, pets, or characters once, then reuse them in new creations without uploading them again.

For developers, the two new API models:
- **GPT-Image-2.6 Flare** is the faster model, generating images in as little as six seconds. OpenAI says image generation across the update is up to 50% faster than before.
- **GPT-Image-2.6 Sunburst** is the higher-quality option, aimed at more detailed compositions and more consistent results across repeated edits.

Both models support image generation and editing (not chat, audio, or other API endpoints), plus a "complexity" setting, markup-guided edits, and SVG export. Both are priced the same: $5 per 1 million input text tokens ($1.25 cached), and for images, $8 per 1 million input tokens ($2 cached) and $30 per 1 million output tokens. OpenAI's own pricing page does not list a flat per-image price; it points developers to a cost calculator in its image generation guide instead.

## Why it matters

The GIF and reference-image features save repeated work: instead of re-uploading a photo of the same person or pet every time, you keep it saved and reuse it. GIFs mean you no longer need a separate tool to animate an image you made in ChatGPT.

For developers, having two models with identical pricing but different strengths — Flare for speed, Sunburst for quality and consistency across edits — makes it easier to pick the right tradeoff for a given feature without a cost penalty either way.

## How to use it

- In ChatGPT, the GIF and reference-image features are available directly in the image tool — no setup needed.
- To make a GIF, generate or upload an image, then use the new GIF option to animate it, adjust speed, and edit frames.
- To reuse a reference image, save it once when generating; it stays available for future prompts without re-uploading.
- Developers: call the API with model `gpt-image-2.6-flare` for faster generation or `gpt-image-2.6-sunburst` for higher-quality, more consistent edits, using the `v1/images/generations` or `v1/images/edits` endpoints. Check the [pricing page](https://developers.openai.com/api/docs/pricing) and each model's page for exact rate limits before switching production workloads.

## Source

- [OpenAI Community: Images, upgraded — introducing ChatGPT Images 2.6](https://community.openai.com/t/images-upgraded-introducing-chatgpt-images-2-6/1412901)
- [GPT-Image-2.6 Flare model page](https://developers.openai.com/api/docs/models/gpt-image-2.6-flare)
- [GPT-Image-2.6 Sunburst model page](https://developers.openai.com/api/docs/models/gpt-image-2.6-sunburst)
