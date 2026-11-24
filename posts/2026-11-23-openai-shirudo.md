---
title: "OpenAI and Cisco launch Shirudo, a live-patching shield for Linux servers"
date: 2026-11-23
description: Shirudo is a new open-source tool from OpenAI and Cisco that blocks a vulnerable code path on a running Linux server, without restarting it, while a real patch is prepared.
---

## What changed

OpenAI and Cisco announced Shirudo (Japanese for "shield"), an open-source runtime that protects running Linux systems while a security patch is still being written and tested.

The problem it addresses: once a vulnerability is found, building and rolling out a proper patch can take days or weeks. During that gap, attackers can exploit the same weakness that a legitimate request might also use, so simply blocking the vulnerable operation outright risks taking the service down.

Shirudo works with eBPF, a Linux feature that lets small programs run at specific points inside the operating system kernel, without changing the kernel itself. Using eBPF, Shirudo can:

- Block a specific vulnerable code path on a running server — a "shield" — without restarting it, and let an operator watch how a proposed shield affects the application before turning it on fully.
- Let an AI agent investigate a vulnerability, build a targeted shield, and test it against both exploit attempts and normal traffic, while a human security team decides what actually gets deployed.
- Cryptographically sign and verify each shield before it loads; the eBPF verifier and kernel controls check it against safety rules and restrict who can change it.
- Use a Trusted Platform Module (TPM, a hardware security chip) to keep a verifiable record of when protections were loaded or removed.

In a demonstration, OpenAI's Codex (its AI coding tool) generated a shield that added an input check to Java's Base64 decoder. Attached to a running Elasticsearch server, that shield blocked an attempted "Java4Shell" exploit while Elasticsearch kept running normally.

Shirudo is released under the BSD 2-Clause license, with its eBPF programs dual-licensed under BSD and GPL.

## Why it matters

This targets the gap between "a vulnerability is discovered" and "a tested patch is deployed everywhere" — a window attackers regularly exploit. Instead of choosing between leaving a known hole open or taking a service offline to patch it, a team can use Shirudo to block just the dangerous operation while keeping the service running, then apply the real fix on their own schedule. Letting an AI agent draft and test the shield (with a human approving what actually deploys) could make this kind of response much faster than a fully manual process, which matters most in the hours right after a vulnerability becomes public.

## How to use it

- Try the quickstart in a virtual machine at docs.shirudo.dev, which walks through signing, loading, and verifying a test protection.
- Practice with Isovalent's self-guided lab.
- Watch the Linux Plumbers Conference walkthrough, or attend OpenAI and Cisco's technical deep-dive webinar on December 15, 2026.
- The code, documentation, and contribution guide are on GitHub under the BSD 2-Clause license (BPF programs are dual BSD/GPL).

## Source

- [OpenAI: Introducing Shirudo](https://openai.com/index/introducing-shirudo/)
