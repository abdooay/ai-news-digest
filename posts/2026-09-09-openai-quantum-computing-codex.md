---
title: "MIT researcher uses Codex agents to run overnight quantum computing experiments"
date: 2026-09-09
description: A graduate student at MIT connected GPT-5.6 Sol to lab software through Codex so it could run and adjust quantum chip measurements without a person watching.
---

## What changed

OpenAI published ["How GPT-5.6 Sol helps run quantum computing experiments"](https://openai.com/index/codex-quantum-computing-experiments/) on September 8, 2026, describing work by Beatriz Yankelevich, a graduate student at MIT's Engineering Quantum Systems Group. She connected GPT-5.6 Sol (an OpenAI model) to Codex (OpenAI's coding-agent tool), which in turn was set up to interact with her lab's measurement software.

The agent ran measurements on a six-qubit superconducting chip — qubits are the basic units of information in a quantum computer, similar to how a bit is the basic unit in a regular computer. The agent identified the chip's transition frequencies, calibrated the control pulses used to manipulate the qubits, and measured how long the chip retained quantum information — a process called characterization, which normally takes a researcher several days per chip. The agent analyzed each result and decided on its own what to measure next, letting it run overnight or while Yankelevich was doing other lab work.

OpenAI's account notes real limits: when a signal from the chip was weak or noisy, the agent sometimes struggled and needed a person to step in, rather than reliably working through ambiguous data on its own.

## Why it matters

This is one example of AI agents handling a repetitive, well-defined scientific task (running standard measurement sequences on known hardware) largely on their own, freeing a researcher's time for planning and analysis instead. It's not evidence that agents can independently run experiments end-to-end without oversight — the noted difficulty with noisy signals shows the same pattern seen elsewhere: current agents do well on clearly-defined, repeatable steps but still need a person for judgment calls on messy or ambiguous data.

## How to use it

This describes a research lab's internal setup rather than a packaged product — there's no specific tool to install. If you work in a lab with software you can script against, the general approach (a coding agent connected to your instrument-control software, with clear, repeatable measurement routines) is what made this work; OpenAI's post doesn't share the specific code or configuration used.

## Source

- [OpenAI: How GPT-5.6 Sol helps run quantum computing experiments](https://openai.com/index/codex-quantum-computing-experiments/)
