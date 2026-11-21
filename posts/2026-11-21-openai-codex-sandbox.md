---
title: "OpenAI explains how the Codex sandbox limits what its coding agent can touch"
date: 2026-11-21
description: OpenAI detailed the Codex sandbox, the system that restricts file and network access for its coding agent, and how developers can configure or reuse it.
---

## What changed

OpenAI published a technical explanation of the Codex sandbox — the system that limits what files Codex (OpenAI's coding agent) can read or write, and whether it can reach the network, when it runs commands on your machine.

By default, using the built-in `:workspace` profile with a Git repository as the base folder:

- Codex can write files inside your project folder, but folders like `.git` and `.codex` stay read-only, so it can't directly edit Git's internal files or its own configuration.
- Codex can read broadly outside the project (subject to your operating system's normal permissions), because build tools often need files elsewhere.
- Codex has no network access by default, so it can't upload anything or download new dependencies on its own.

OpenAI notes one gap: Codex could still modify a locally installed package (like a formatting tool in `node_modules`) that Git doesn't track, and if your code editor runs that package automatically when you save a file, that code would run without any sandbox limits.

Codex doesn't use virtual machines or containers for this — it uses each operating system's own built-in sandboxing (Seatbelt on macOS, bubblewrap and seccomp on Linux, and Microsoft's MXC on Windows), through one shared internal interface. This lets Codex still work with tools that containers struggle with, like Apple's iOS simulator.

Developers can define their own permission profiles in a `config.toml` file, marking specific folders as readable, writable, or denied, and can turn on a network proxy that only allows connections to specific domains you list. There's also a `codex sandbox` command that lets you run any command, or wrap something like an MCP (Model Context Protocol) server, under one of these restricted profiles yourself.

Administrators can also set organization-wide rules in a `requirements.toml` file to control which permission profiles are even allowed to be used.

## Why it matters

This matters for anyone using Codex on their own machine: it explains exactly what "safe by default" means in practice, and where the edges of that safety are — like the locally-installed-package gap. For teams, the ability to define custom permission profiles and restrict network access by domain means you can tighten or loosen what Codex is allowed to touch based on the sensitivity of the project, rather than trusting one fixed set of rules.

## How to use it

- To run any command under a specific profile, use `codex sandbox --permission-profile <name> -- <your command>`.
- To define custom rules, add a `[permissions]` section to your `config.toml`, listing folders as `read`, `write`, or `deny`, and set `default_permissions` to your profile's name.
- To restrict network access to specific domains instead of blocking it entirely, turn on `[features] network_proxy = true` and list allowed domains in your profile.
- To sandbox an MCP server (which isn't sandboxed by default), wrap its startup command with `codex sandbox` under a profile that limits its file and network access.

## Source

- [OpenAI: Inside the Codex sandbox](https://openai.com/index/inside-the-codex-sandbox/)
