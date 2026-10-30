---
title: "Claude API roundup: bigger request limit, new usage and cost analytics API"
date: 2026-10-30
description: Anthropic raised the Claude API's maximum request size from 32 MB to 128 MB and launched a new Usage and Cost Analytics API in beta for Console and Enterprise organizations.
---

## What changed

Two small Claude API changes landed this week:

**Bigger request size limit (October 28, 2026).** Anthropic raised the maximum request size for the Messages API (the main endpoint for sending a conversation to Claude) and the Token Counting API (which estimates how many tokens a request will use) from 32 MB to 128 MB, on the first-party Claude API.

**Usage and Cost Analytics API, in beta (October 29, 2026).** Anthropic launched a new Usage and Cost Analytics API in beta, available with the `analytics-usage-cost-2026-08-24` beta header. It adds two endpoints, `/v1/organizations/analytics/usage` and `/v1/organizations/analytics/cost`, which report token usage and dollar cost for Claude Console and Claude Enterprise organizations. Results can be filtered and grouped by dimensions such as model, workspace, API key, and the specific user or service account that made each request. At the same time, the older Usage and Cost API — along with the `usage_report`, `cost_report`, `user_usage_report`, and `user_cost_report` endpoints of the Claude Enterprise Analytics API — became "legacy" APIs. Anthropic says all of them remain supported for now; it's just pointing new integrations at the new API.

## Why it matters

The request-size increase mainly helps anyone sending large payloads to Claude — for example, a request with several big file attachments or a long tool-use conversation — who was previously bumping into the 32 MB ceiling. Most everyday requests are far smaller than either limit, so this won't affect typical usage. The new analytics API matters more for teams managing Claude spend across many users, API keys, or workspaces: being able to filter and group usage and cost by those dimensions makes it easier to see which team, project, or key is driving cost, without building that breakdown yourself from raw request logs.

## How to use it

- The larger 32 MB → 128 MB request limit applies automatically; no code changes are needed.
- To try the new analytics API, send requests to `/v1/organizations/analytics/usage` or `/v1/organizations/analytics/cost` with the beta header `analytics-usage-cost-2026-08-24`. It's for Claude Console and Claude Enterprise organizations only.
- If you have an existing integration against the older Usage and Cost API or the Enterprise Analytics API's report endpoints, those still work, but Anthropic's migration guides (linked in the source) cover moving to the new API.

## Source

- [Claude Platform release notes — October 29, 2026](https://platform.claude.com/docs/en/release-notes/api#october-29-2026)
- [Claude Platform release notes — October 28, 2026](https://platform.claude.com/docs/en/release-notes/api#october-28-2026)
