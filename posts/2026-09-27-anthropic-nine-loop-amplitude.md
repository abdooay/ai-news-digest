---
title: "Claude helps solve a nine-loop physics problem"
date: 2026-09-27
description: A physicist asked AI companies to compute a hard particle-physics quantity, and a Claude model produced a correct nine-loop result on an academic budget.
---

## What changed

On September 25, 2026, Anthropic published "Yes, Claude can do Nine Loops," a guest post by physicist and science writer Matt von Hippel. He had challenged AI companies to compute a "nine-loop scattering amplitude" in N=4 super Yang-Mills theory — a simplified ("toy") model that particle physicists use to test new calculation techniques before applying them to real-world physics. A "loop" here refers to how many rounds of a certain calculation step are involved; each extra loop makes the problem dramatically harder.

Anthropic's Claude Fable 5.1, running inside Claude Science (Anthropic's platform for scientific research), was given the problem statement and worked for several hours with only periodic check-ins from the physicists — no step-by-step guidance. It solved the problem two different, independent ways: a "bootstrap" method and a separate "form-factor" approach. The bootstrap run cost about $100, using computing power equivalent to 96 processors (CPUs) running for a week.

The result matched a calculation done at the same time, by hand and by computer, by a human-led research group at the Chinese Academy of Sciences. Lance Dixon, a physicist at SLAC who had previously computed the equivalent result at eight loops, independently checked and confirmed Claude's answer.

## Why it matters

This isn't a case of the AI being told exactly what steps to follow — it had to plan, organize, and carry out a long, technically demanding calculation by itself and get a graduate-level physics research answer right. Dixon noted the achievement wasn't just getting the right number, but successfully executing every step of a "complicated recipe" without a human physicist supervising each move. That's a meaningful data point for how much unsupervised research work current models can already handle in narrow, well-defined technical domains, and it did so cheaply enough for an ordinary academic budget.

## How to use it

This was a research collaboration rather than a product launch, so there's no new setting or API to try. Researchers interested in similar work can apply to use Claude Science, Anthropic's platform that gives scientists access to Claude for research projects.

## Source

- [Yes, Claude can do Nine Loops](https://www.anthropic.com/research/yes-claude-can-do-nine-loops)
