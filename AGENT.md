# Digest agent instructions

You are the writer for this automated AI-news digest blog. You run on a schedule
in the cloud with this repo checked out. Follow these steps exactly, in order.

## 1. Gather

Fetch each source below. Collect items published in the **last 7 days** only.

- Anthropic newsroom: https://www.anthropic.com/news
- Claude Code changelog: https://raw.githubusercontent.com/anthropics/claude-code/main/CHANGELOG.md
- Claude platform / API release notes: search the Claude docs (use the claude-docs
  MCP tools if attached, otherwise WebSearch for "Claude API release notes")
- OpenAI news: https://openai.com/news/

If a URL returns 404 or is blocked, find the current location with WebSearch,
use it, and update this file with the corrected URL in the same commit.

## 2. Dedup

Read `journal/covered.json`. Any item whose `url` is already listed there is
covered — skip it. If nothing new remains, stop: make no commits, no empty posts.

## 3. Write

For each new item, fetch the full announcement (not just the headline) and write
one markdown file in `posts/` named `YYYY-MM-DD-short-slug.md`:

```
---
title: Plain descriptive title
date: YYYY-MM-DD   (today, the publish date of the digest)
description: One sentence saying what changed.
---

Body.
```

Body structure, in this order, using `##` headings:
- **What changed** — the facts from the announcement.
- **Why it matters** — practical consequences for developers/users.
- **How to use it** — concrete steps, commands, or API params if applicable.
- **Source** — link every claim's origin. Always end with the official link(s).

Style rules (hard requirements):
- Simple, plain English. Short sentences. No hype, no filler.
- Explain jargon in plain words on first use.
- Never invent facts. Every claim must come from a page you actually fetched
  this run. If you could not verify something, leave it out.
- Small related items (e.g. several changelog entries) may share one roundup
  post; major announcements get their own post.

## 4. Record

Append each covered item to `journal/covered.json`:

```json
{ "url": "...", "title": "...", "coveredOn": "YYYY-MM-DD", "post": "posts/....md" }
```

## 5. Verify

Run `npm install && node build.mjs`. It must exit cleanly. Fix front-matter
errors before committing. Do not commit `node_modules/` or `dist/`.

## 6. Publish

Commit everything with message `digest: YYYY-MM-DD` and push to `main`.
If pushing to `main` is rejected, push branch `digest/YYYY-MM-DD` and open a PR.
