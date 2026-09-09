---
title: "An OpenAI model claims progress on a $1 million unsolved math problem"
date: 2026-09-09
description: OpenAI says an internal, unreleased model produced a proof addressing part of the Navier–Stokes existence and smoothness problem, one of the Clay Institute's seven Millennium Prize Problems.
---

## What changed

OpenAI published ["An OpenAI model proposes a solution to the Navier–Stokes problem"](https://openai.com/index/navier-stokes-solution/) on September 8, 2026. The Navier–Stokes equations describe how fluids (like water or air) move. Mathematicians have not been able to prove whether these equations always have smooth, well-behaved solutions, or whether a fluid that starts out smooth can develop a "singularity" — a point where the math breaks down — in finite time. This is one of seven Millennium Prize Problems, each with a $1 million prize from the Clay Mathematics Institute, and it has been unsolved for roughly 90 years.

OpenAI says an internal, unreleased model — described only as "significantly more capable than GPT-6 Astra" — produced a proof addressing two of the four official sub-statements of the problem (labeled C and D by the Clay Institute), showing that an initially smooth fluid at rest can develop a singularity in finite time.

The work used a multiagent setup: about 10,000 AI agents worked concurrently in coordinating groups, with access to cached internet data and the ability to run code. Different groups explored different variants of the problem, and OpenAI's Codex tool merged the most promising insights across groups. The main effort took about 88 hours, from September 1 to September 5, 2026, using roughly 2.7 million agent messages and about 130 billion output tokens. GPT-6 Astra (OpenAI's current publicly-rolling-out model, covered in our earlier post) then spent about 17 hours formally verifying the proof in Lean, a programming language used to machine-check mathematical proofs.

OpenAI explicitly says it does not intend to claim the $1 million Millennium Prize for this work, and describes it as "a snapshot in time" rather than a finished, final result. OpenAI also notes it cannot fully rule out that anonymized data from other users' product usage around the same time helped improve the model that did this work.

## Why it matters

If this proof holds up, it would be a real result in a famous unsolved area of mathematics — but formal peer review of Millennium Prize claims takes time, and OpenAI itself is not claiming victory. It's also worth knowing that an outside mathematician (NYU's Tristan Buckmaster) and an Anthropic researcher (Levent Alpöge) reportedly reached a related but different result — a proof for a version of the Euler equations with forcing — around the same time, so this is an active area with more than one group making progress at once.

Practically, this is a demonstration of what a large number of coordinated AI agents can attempt on a single hard problem, using a huge compute budget over several days, rather than something you'd deploy on an everyday task.

## How to use it

There's no product or feature here to use directly. If you want to check on how this claim holds up, watch for independent verification of the Lean-formalized proof or commentary from mathematicians in the field — OpenAI's own formal write-up wasn't published alongside this announcement.

## Source

- [OpenAI: An OpenAI model proposes a solution to the Navier–Stokes problem](https://openai.com/index/navier-stokes-solution/)
