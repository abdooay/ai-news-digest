---
title: "GPT-6 Astra gets much better at legacy and low-resource programming languages"
date: 2026-10-25
description: OpenAI's new MultiLangBench shows GPT-6 Astra scoring 87.4% versus 26.8% for GPT-5.6 Sol on coding tasks in 20 different programming languages, including older ones like COBOL and Fortran.
---

## What changed

OpenAI published results on October 19, 2026, on how well its models handle "low-resource" programming languages — languages like COBOL and Fortran that have far less training data available online than popular languages like Python or JavaScript, because fewer people write and publish code in them.

OpenAI built a new benchmark called MultiLangBench to test this. It asks a model to build a SQLite-compatible database engine (a small, well-defined, but non-trivial piece of software) from scratch, separately, in 20 different programming languages. On this test, GPT-6 Astra scored an average pass rate of 87.4% across the 20 languages, up from 26.8% for the older GPT-5.6 Sol model.

OpenAI also ran a separate evaluation specifically on COBOL, an old language still widely used in banking and government systems. That test asks a model to port (translate) COBOL programs to a different language while keeping the output byte-for-byte identical. GPT-6.1 Sol scored 86.6% on that test at "low effort" settings.

OpenAI notes both evaluations were designed and run internally, and says real-world use would need further expert review and validation before relying on this for production systems.

## Why it matters

A huge amount of the world's software — especially in banks, insurers, airlines, and government agencies — still runs on old languages like COBOL and Fortran that few new developers learn. Finding and training people to maintain or migrate that code is slow and expensive. If a model can reliably read, write, and translate code in these languages, it could make modernizing old systems, or just keeping them running, much cheaper and faster. The gap between the old and new model (26.8% to 87.4%) also shows these older languages were a real weak spot for earlier models, not just a minor gap.

## How to use it

There's no new API or product to install here — this is a research and benchmark result. If you maintain legacy systems in COBOL, Fortran, or similar languages, GPT-6 Astra is likely a meaningfully better fit for working with that code than earlier models were. OpenAI's own caveat is worth repeating: these are internal benchmarks, so test carefully against your own codebase (and keep the byte-for-byte output checks OpenAI used, since silent behavior changes in financial or legacy systems can be costly) before trusting output in production.

## Source

- [Advancing coding in low-resource programming languages (OpenAI)](https://openai.com/index/low-resource-programming-languages/)
