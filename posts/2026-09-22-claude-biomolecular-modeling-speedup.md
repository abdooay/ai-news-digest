---
title: "Claude speeds up open-source protein modeling tools by 4x"
date: 2026-09-22
description: Anthropic used Claude to optimize over 30 biomolecular modeling programs, cutting research costs by about 100x, and is launching a $1M protein design competition with Adaptyv Bio.
---

## What changed

Anthropic says it used Claude to rewrite and speed up more than 30 open-source deep learning tools that scientists use to predict and design protein structures. Claude did this optimization work in under four weeks. On average, the optimized programs run about 4x faster than before, with only a small loss in precision (accuracy). Some optimizations kept the exact same output while still running nearly 2x faster.

One specific improvement, called "FlashPairformer," speeds up two core calculation steps (called "triangle attention" and "triangle multiplication") used in structure-prediction models. It beat the previous best versions of these calculations by 2.7-2.9x and 1.7-3.2x.

Claude also built a "Big" mode that lets researchers model very large biological structures — over 10,000 "tokens" (units the model processes, roughly corresponding to amino acids here) — on a single graphics card (GPU) instead of needing a large cluster. Using this, Anthropic modeled structures with more than 70,000 tokens, including the human "mitochondrial complex I" and the "70S ribosome," both large molecular machines inside cells.

On cost: Anthropic says a typical research campaign that used to cost about $10,000 and 2,500 hours of high-end GPU time can now be done for around $150 in total compute and Claude usage — about 100 times fewer GPU hours for comparable results.

Alongside this, Anthropic and Adaptyv Bio (a biotech company) are launching a protein design competition. It offers up to $1 million in Claude credits, up to $250,000 in compute credits from Modal, and free DNA synthesis from Twist Bioscience, to test more than 5,000 AI-generated protein designs in a real ("wet") lab at no cost to participants. The competition covers five specific hard problems in protein design, including designing proteins that work across species and proteins that respond to different pH (acidity) levels.

## Why it matters

Protein structure prediction and design (figuring out the 3D shape of biological molecules, and creating new ones for uses like drugs) is normally slow and expensive, needing large amounts of specialized compute. Making these open-source research tools dramatically faster and cheaper — while keeping accuracy similar — could let more academic labs and smaller biotech companies run this kind of research without needing large GPU budgets.

The competition is a practical way for outside researchers to test whether AI-designed proteins actually work, since the winning entries get validated in a physical lab rather than just checked by simulation.

## How to use it

- The speed improvements are being contributed to the existing open-source biomolecular modeling tools, so researchers who already use these tools should get the gains automatically once the updates land in the relevant projects.
- Anthropic hasn't published a single combined "how-to" guide for these optimizations in this article; the changes are described as contributions to each affected open-source project.
- Applications for the protein design competition with Adaptyv Bio are open now for anyone interested in submitting protein designs for lab testing.

## Source

- [How Claude is uplifting biomolecular modeling](https://www.anthropic.com/research/claude-uplifts-biomolecular-modeling)
