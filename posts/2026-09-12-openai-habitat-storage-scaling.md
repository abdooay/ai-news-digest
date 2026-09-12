---
title: "How OpenAI scaled the storage system behind ChatGPT to 1 billion weekly users"
date: 2026-09-12
description: OpenAI describes Habitat, the storage platform behind ChatGPT, and how it grew from a small Python library into a service now rewritten in Rust.
---

## What changed

On September 11, 2026, OpenAI published the first of a two-part engineering post about Habitat, the internal storage platform that every OpenAI product uses to read and write data — logins, settings, conversations, and more. Habitat now handles more than 70 million requests per second, serves over 1 billion people each week across about 40 regions, and stores more than 500 petabytes of data (a petabyte is about a million gigabytes).

Habitat started in 2023 as a simple Python library that talked directly to a database (Azure Cosmos DB). As OpenAI's traffic grew more than 10x per year for three years straight, that library became too hard to change safely — updating it meant coordinating rollouts across dozens of services at once, which was slow and caused at least one outage. OpenAI's engineers rebuilt Habitat as a standalone service so changes could be made in one place instead of everywhere at once.

Running that service in Python (rather than a faster language) was a deliberate short-term tradeoff to keep moving quickly. The team found and fixed several performance problems along the way: CPU-heavy background work (like periodically re-reading feature-flag configuration) was delaying other requests; a common connection-reuse strategy was making already-slow servers get more traffic instead of less; and having many server processes risked overwhelming the database with connections. They fixed these with faster background-task scheduling, switching connection reuse from "most recently used" to "first in, first out," and routing traffic through Envoy (networking software) to share and limit connections centrally.

In Q2 2026, with 2 engineers using OpenAI's own Codex and GPT-5.5 tools, the team rewrote the entire service in Rust. The Rust version now handles 95% of production traffic and is reported to be 6x more CPU-efficient and 15x more memory-efficient than the Python version, with lower latency. OpenAI plans to fully retire the Python version soon and says a second post will cover the database layer itself.

## Why it matters

This is a case study in scaling infrastructure under fast growth, aimed at engineers rather than end users — there's no new product feature here. Two points are broadly useful beyond OpenAI: first, deliberately accepting a slower technology (Python) short-term to avoid blocking product work, then migrating later once growth justifies the cost, is a real tradeoff many teams face. Second, the specific bugs described (a connection-pool strategy that concentrates load on already-overloaded servers, and CPU work that stalls I/O-bound processes) are common failure patterns in high-traffic backend systems, not unique to OpenAI.

## How to use it

There's no setting or API to turn on here — this is an engineering write-up, not a product change. Teams running similar high-throughput services may find two concrete techniques worth borrowing: using FIFO (first in, first out) instead of LIFO (last in, first out) connection reuse to avoid piling more traffic onto already-slow servers, and routing traffic through a shared proxy like Envoy to pool and limit connections centrally instead of letting each server process manage its own.

## Source

- [Rapidly scaling online storage to serve over 1 billion ChatGPT users](https://openai.com/index/scaling-storage-one-billion-users-part-one/)
