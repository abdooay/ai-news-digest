---
title: Anthropic previews a standard for letting AI agents control lab hardware
date: 2026-08-27
description: The Model Hardware Standard lets AI agents operate microscopes, liquid handlers, and other lab equipment through a shared, model-agnostic interface.
---

## What changed

Anthropic released a research preview of the **Model Hardware Standard (MHS)**, developed with HHMI Janelia Research Campus. It's a shared specification that lets AI agents safely control physical lab and manufacturing equipment — such as microscopes, liquid handlers, and robotic arms — including operating several instruments at the same time.

How it works: MHS uses standardized "drivers" that translate between different devices and the AI agent through simple commands like "read" and "write." Devices announce themselves in a standard format, so there's no need to write custom translation code for each new piece of equipment. The standard is model-agnostic (it works with any AI model that has a programmable interface) and supports the Model Context Protocol (MCP), a common way of connecting AI models to external tools and data.

Anthropic says integrating a new piece of lab hardware normally takes a lab "weeks, if not months." MHS is meant to cut that down to hours or minutes.

Early results cited from partners:
- **Genentech**: automated protein assay steps across multiple instruments.
- **Carnegie Mellon**: cut the time to run dose-response curve experiments to roughly a third of what it took before.
- **QuEra Computing**: used AI-controlled laser stabilization with a 99.3% recovery success rate.
- **University of Washington**: remote lab monitoring and automated handling of sample plates.

MHS is still a research preview. Anthropic says it plans to release it as open source once safety evaluations are complete.

## Why it matters

Right now, connecting an AI agent to physical lab equipment usually means custom, one-off integration work for every device. A shared standard means that integration work happens once per device rather than once per lab. That translates directly into research speed: the examples above show experiments that used to take weeks now taking hours.

## How to use it

MHS isn't generally available yet — it's a research preview, with open-source release planned after Anthropic finishes safety evaluations. There's no general sign-up step yet; labs interested in early access would need to follow Anthropic's research preview channels directly.

## Source

- [Previewing the Model Hardware Standard](https://www.anthropic.com/news/model-hardware-standard-research-preview)
