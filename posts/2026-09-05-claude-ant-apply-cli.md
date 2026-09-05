---
title: "ant apply: manage Claude API resources as files in your repo"
date: 2026-09-05
description: A new ant CLI command, ant apply, lets you define agents, environments, skills, memory stores, and deployments as files and keep them in sync with the Claude API.
---

## What changed

Anthropic's `ant` command-line tool (the CLI for the Claude API) added a new command, `ant apply`, in version 1.30.0, released September 3, 2026.

`ant apply` reads files in your repository that describe Claude API resources — agents, environments, skills, memory stores, and scheduled deployments — and creates or updates the matching resources through the API. Each resource is a Markdown, YAML, or JSON file (an agent, for example, is a Markdown file with configuration in its front-matter and the system prompt as the body). You run `ant apply`, it prints a plan of what will be created or changed, and you approve it before anything happens.

The first run writes a lockfile, `claude-lock.json`, that records the ID of every resource it created. You commit this file alongside your resource files. On the next run — on your machine or in CI — `ant apply` reads the lockfile and updates those same resources instead of creating duplicates.

Files can also reference each other by relative path instead of by ID. For example, an agent file can list another agent file as a sub-agent, or a deployment file can point to an environment file — `ant apply` resolves the paths and fills in the real IDs when it creates them, in the right order.

`ant apply` requires CLI version 1.30.0 or later.

## Why it matters

Before this, creating an agent, environment, or scheduled deployment on the Claude API meant calling the API directly or using the Claude Console. Nothing tracked those resources as code, so there was no natural way to review a change to an agent's configuration the same way you'd review a code change, or to keep a team's agents in sync with what's checked into a repository.

With `ant apply`, these resources become files that go through the same pull request and code review process as everything else. Running it in CI means a merge to your main branch automatically updates the live resources to match, and a pull request can show a preview of what would change before it merges.

## How to use it

- Requires `ant` CLI version 1.30.0 or later (see the CLI quickstart to install and authenticate).
- Write a resource as a file: an agent goes in `agents/` as Markdown with its config in the front-matter; an environment or memory store is YAML in `environments/` or `memory_stores/`; a deployment is Markdown in `deployments/`; a skill is a directory with a `SKILL.md` at its root.
- Apply one file with `ant apply agents/summarizer.md`, or a whole directory with `ant apply .`.
- Approve the printed plan interactively, or pass `--yes` to apply without asking (required when there's no terminal, such as in CI).
- Use `--dry-run` to print the plan without applying anything — useful for showing reviewers what a pull request would change.
- Commit the `claude-lock.json` file it writes so later runs update the same resources.
- Other flags: `--force` to override a resource that was changed outside these files, `--prune` to remove resources no longer declared in a file, and `--upgrade` to re-resolve a skill referenced by a GitHub URL.

## Source

- [Claude API release notes, September 3, 2026](https://platform.claude.com/docs/en/release-notes/api#september-3-2026)
- [Manage resources as code with ant apply](https://platform.claude.com/docs/en/cli-sdks-libraries/cli/apply)
