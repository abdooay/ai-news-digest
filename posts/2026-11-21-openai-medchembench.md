---
title: "OpenAI introduces MedChemBench, a test of AI reasoning for drug design"
date: 2026-11-21
description: OpenAI's new benchmark tests whether AI models can reason about real medicinal chemistry problems, and its best model, GPT-6.2 Astra, scored 84.5%.
---

## What changed

OpenAI introduced MedChemBench, a benchmark (a standard test used to measure and compare AI models) that checks whether AI models can reason like a medicinal chemist — someone who designs drug molecules.

The benchmark has 99 problems, drawn from 117 published papers and patents, covering 761 real molecules. Each problem drops the model into a real research program at a certain point: it's given the target the researchers are chasing, the compounds studied so far, and some of the findings, then asked to reason about what comes next. This matters in drug design because improving one property of a molecule — like how strongly it attacks a disease target — often makes another property worse, like how well the body absorbs it.

Models are graded on four things: whether they get a molecule's atomic structure right, whether their explanations are backed by the evidence given, whether their rankings and compound choices meet the stated goals, and whether their numerical predictions (like a potency value) are close to the real measured number.

OpenAI tested eleven of its GPT models at different "reasoning effort" settings (how much computation the model spends thinking before answering). At the highest settings tested, the scores were:

- GPT-6.2 Astra: 84.5%
- GPT-6 Astra: 83.3%
- GPT-6.1 Sol: 82.0%
- GPT-6.1 Terra: 75.1%
- GPT-5.6 Sol: 58.2%

GPT-6 Astra was best at reconstructing correct molecule structures and explaining evidence, but its scores for ranking compounds and predicting exact numbers were roughly half the available credit. In one structure test requiring an 18-atom ring to stay intact, GPT-6 Astra got it right in all ten tries, while GPT-5.6 Sol and GPT-5.6 Luna both failed every time, producing a wrong-sized ring or disconnected pieces.

OpenAI is clear about the limits: this only tests reasoning from historical evidence in a single attempt, with no tools, lab feedback, or new experiments. It doesn't show whether a model can actually discover a new drug.

## Why it matters

Drug discovery involves exactly this kind of trade-off reasoning — chasing one improvement without breaking another. A model that reliably reasons through those trade-offs could help chemists explore options faster, but a model that gets structures or numbers wrong could waste a researcher's time or mislead them. The clear gap between models (GPT-6.2 Astra's 84.5% versus GPT-5.6 Sol's 58.2%) shows this kind of chemistry reasoning is still a real differentiator between models, not something every modern AI model does equally well.

## How to use it

OpenAI has published a preprint paper describing MedChemBench in detail (linked from the source below). The announcement does not say whether the benchmark's problems or dataset are publicly downloadable, or how to run it yourself, so there's no hands-on setup to describe yet.

## Source

- [OpenAI: Introducing MedChemBench](https://openai.com/index/introducing-medchembench/)
