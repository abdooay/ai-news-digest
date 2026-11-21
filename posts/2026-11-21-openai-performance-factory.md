---
title: "OpenAI built a Codex-powered system that finds and fixes its own ChatGPT performance bugs"
date: 2026-11-21
description: OpenAI's Performance Factory uses Codex agents to investigate ChatGPT slowdowns automatically, with engineers reviewing proposed fixes before they ship.
---

## What changed

OpenAI described the Performance Factory, an internal system that uses Codex (OpenAI's coding agent) to investigate and fix performance problems in ChatGPT, such as slowdowns or availability issues, with much less manual engineering work.

Its first workflow, the Regression Workflow, works like this: a performance alert fires, which opens a task. An AI agent investigates, finds a likely root cause, and writes up its findings. Another agent proposes a fix for an engineer to review. Once the fix ships, a further agent checks whether performance actually returned to normal.

Over about three months, the system tracked more than 1,700 investigations and found a root cause for more than 600 of them — roughly 17 automated investigations a day. When engineers manually reviewed 100 of the AI's root-cause explanations, 70% were graded accurate; the rest needed refinement or didn't fully prove the cause.

The system is built from four parts: a task service that defines workflows in configuration files and plain-language prompts; a dispatch loop that starts Codex sessions when a task is ready; Codex itself, running in the cloud with access to code and monitoring tools under a scoped service identity (so its permissions and actions are traceable); and a subscription mechanism that resumes a waiting task when something relevant happens, like a code review comment or a failed test.

To catch mistakes, OpenAI uses adversarial review: a separate Codex session tries to poke holes in the first session's diagnosis or proposed fix. In one case, this caught a wrong diagnosis that didn't explain why failures were still happening.

OpenAI says engineer review and merging of fixes is now the main bottleneck, and it's exploring whether safe, low-risk fixes could eventually ship without a human checking them first.

## Why it matters

This is a real example of AI agents handling a chunk of software engineering work end to end — not just writing code when asked, but noticing something is wrong, diagnosing it, and proposing a fix, with other AI agents checking the work along the way. For engineering teams elsewhere, it's a template: break a recurring task into stages, assign an agent to each stage, and have a second agent adversarially check the first one's work before a human signs off.

## How to use it

This is an internal OpenAI tool, not something external developers can install or use directly. The practical takeaway is the pattern it demonstrates: encode a recurring investigation process as a reusable "skill" (OpenAI calls theirs `perf-forensics`), test it against past incidents, and add a second AI pass that specifically tries to disprove the first pass's conclusion before a person reviews it.

## Source

- [OpenAI: How OpenAI's Performance Factory keeps ChatGPT fast](https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/)
