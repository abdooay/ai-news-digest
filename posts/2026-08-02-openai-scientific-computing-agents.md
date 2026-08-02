---
title: OpenAI's field report on AI coding agents in scientific software
date: 2026-08-02
description: A study of eight science projects that used Codex and Claude Code found agents speed up coding but can't judge whether results are scientifically correct.
---

## What changed

OpenAI published a field report looking at eight real projects where scientists used AI coding agents to build or modernize scientific software, mostly in life sciences (biology, genomics, and related fields). Five projects used OpenAI's Codex alone; three used a mix of Codex and Claude Code. The work ranged from routine maintenance to rewriting systems in a different programming language and redesigning software to run on GPUs.

Key findings from the report:

- Coding agents clearly sped up the software-writing part of the work, letting small teams take on projects that would normally need specialized engineers.
- The hard part wasn't writing the code — it was checking whether the code's output was scientifically correct. Agents could sound confident about code that was actually wrong, so someone had to set up clear ways to check the results (like comparing outputs against known-good data, or checking that a new tool's output matches an older, trusted tool's output).
- Projects worked best when done in small stages with feedback along the way, rather than trying to do everything in one big pass. The last bit of polishing — fixing edge cases and small numerical differences — took a disproportionate amount of the total effort.
- The report warns that because building new tools is now cheaper, there's a risk of many one-off, abandoned tools appearing instead of contributions to existing, maintained projects. It recommends coordinating with existing maintainers and planning who will maintain new code before starting.

One example: an agent helped modernize the build system of `cyvcf2`, a genomics library, and the tool's maintainer noted that agents make it easy to move fast, but expert judgment is still needed to make sure the science stays right.

## Why it matters

This report matters beyond scientific labs: it's a real-world data point on where AI coding agents genuinely save time (writing and refactoring code) versus where a human still has to do the work (deciding if the result is actually correct, and taking responsibility for maintaining it). Anyone using coding agents for anything more serious than a quick script — not just scientists — can take away the same lesson: set up a clear way to verify the agent's output before trusting it, and don't skip planning who maintains the result.

## How to use it

- If you're using an AI coding agent (Codex, Claude Code, or similar) for a project where correctness matters, set up an objective check before you start — for example, compare the new code's output against a trusted reference, rather than just reading the code and assuming it's right.
- Break large projects into small stages with a way to verify each stage, instead of asking the agent to do everything in one go.
- Before starting a rewrite or new tool, check whether an existing project already covers the need, and plan who will maintain the new code afterward.

## Source

- [OpenAI: "Scientific computing in the age of agentic AI"](https://openai.com/index/scientific-computing-agentic-ai/)
