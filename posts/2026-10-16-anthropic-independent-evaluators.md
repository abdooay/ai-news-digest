---
title: Anthropic brings in outside groups to check its safety claims
date: 2026-10-16
description: Anthropic is giving outside evaluators, starting with the nonprofit METR, deep access to its systems so they can independently check its safety work and publish what they find.
---

## What changed

Anthropic announced it is letting outside organizations look closely at its safety practices, instead of only describing them itself.

The first and deepest arrangement is with **METR**, a nonprofit that evaluates frontier AI models. Six METR employees now get "employee-like access" to Anthropic: company hardware, office space, and internal tools similar to what Anthropic's own risk-assessment teams use. They can share most of what they learn, except for three narrow categories: customer data, attorney-client privileged material, and model architecture details (which carry high leak risk and need explicit internal approval to share). METR will publish its own analysis of risk levels, incidents, and practices. Anthropic cannot block publication, but it can require redaction of those three categories — and METR can publicly say whether it thinks the redactions were fair, without revealing what was redacted.

Anthropic also named two other partners:
- **SecureBio** is reviewing the chemical and biological weapons chapter of Anthropic's August 2026 Risk Report, after a pilot review of an earlier report (which SecureBio published).
- **Accenture**, working with **Faculty**, is pursuing a broader partnership on model evaluation, red-teaming (deliberately trying to break or trick a model to find weaknesses), alignment assessment, and safeguard testing.

Anthropic is also in early talks with other groups, including Hugging Face.

The company described a **three-tier access model** for these arrangements:
- **Tier 1**: Narrow, specific investigations. Anthropic picks what evaluators can see, and must approve publication.
- **Tier 2**: Broader access. Evaluators can publish without Anthropic's approval, though Anthropic can still require specific redactions.
- **Tier 3**: The METR-style arrangement — employee-like access and publication rights similar to Tier 2. Anthropic says it hopes several evaluators reach this tier.

This follows a commitment Anthropic made last month to stronger independent assessment, and its signing of the White House Accord on Super Intelligence, where companies pledged to work with independent external auditors.

## Why it matters

Until now, the public has mostly had to take Anthropic's word for its own safety claims. This gives outside experts — with no equity or financial stake in Anthropic — real access to check those claims and publish their own conclusions, similar to how bank regulators place examiners inside large banks. For developers and companies relying on Claude, it's a signal (though not a guarantee) that safety claims about the models are getting independent scrutiny rather than resting on self-reporting alone.

## How to use it

This is a policy and transparency change, not a product feature — there is nothing to configure or turn on. If you want to follow the independent findings as they're published, METR and SecureBio are expected to publish their own assessments; Anthropic's announcement is the place to watch for links as those come out.

## Source

- [An update on independent evaluators](https://www.anthropic.com/news/an-update-on-independent-evaluators)
