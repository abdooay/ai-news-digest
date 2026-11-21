---
title: "OpenAI's models are now helping design real chips, from its own Jalapeño to AMD GPUs"
date: 2026-11-21
description: OpenAI says its models helped shrink and speed up parts of its Jalapeño inference chip, and cut AMD's chip design work by up to 14% on performance, power, and area.
---

## What changed

OpenAI described how its AI models are being used to help design computer chips, with concrete, measured results on three fronts: its own custom chip, a chip partner's hardware, and open-source processor designs used for testing.

**Jalapeño (OpenAI's own inference chip):** Engineers started using an OpenAI model (GPT-o3 mini) in early 2025 to help design parts of Jalapeño, OpenAI's custom chip for running trained models. The model proposed redesigns to the chip's vector and matrix math circuits — the parts that do the heavy numerical computation. One multiplier redesign cut the physical circuit area needed by about 15% and reduced its delay from two clock cycles to one. Overall, OpenAI estimates the model's suggested changes reduced circuit area by about 13% in the vector unit and about 10% in the matrix unit, and these changes were actually built and tested in real silicon.

**AMD collaboration:** Using an OpenAI model to rewrite AMD's chip design code (while AMD's own tools checked that behavior didn't change), AMD measured up to 14% improvement in PPA — power, performance, and area, the three core measures chip designers optimize — on its flagship graphics chip design, compared to a baseline AMD had already heavily optimized by hand. OpenAI describes this as roughly a year of normal progress achieved in under 5 months. AMD has included some of these changes in a chip design already sent for manufacturing, and added others to files for future chip versions. AMD separately confirmed smaller, single-digit percentage gains on its upcoming next-generation CPU.

**Open-source test chips:** OpenAI also tested its models on two small, open-source processor designs (PicoRV32 and Ibex) in two tasks — improving existing chip code, and designing a chip from a written specification. Its newest model, GPT-6.2 Astra, scored highest on both tasks among the models tested, and on one test scored roughly twice as well as its predecessor, GPT-6 Astra.

OpenAI also announced it's partnering with chip-design software maker Synopsys to train a new model, called "GPT-Synopsys," meant to use Synopsys's professional chip-design tools the way a human expert would.

## Why it matters

Chip design has traditionally been slow, specialized human work. These results are a sign that AI models can meaningfully speed up parts of it — not just suggesting ideas, but producing changes precise enough to go into real manufactured chips, as happened with both Jalapeño and AMD's hardware. Faster, cheaper chip design could eventually mean faster-improving hardware for running AI itself, which is part of why OpenAI is investing in its own chip (Jalapeño) alongside this kind of tooling.

## How to use it

This work is specific to OpenAI's internal chip design process and its partnership with AMD and Synopsys — it isn't a product end users or most developers can access directly. There's no new API or setting to adopt from this announcement.

## Source

- [OpenAI: Advancing chip design with OpenAI models](https://openai.com/index/advancing-chip-design-with-our-models/)
