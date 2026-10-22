---
title: "OpenAI API: admins can now restrict which service tiers a project uses"
date: 2026-10-22
description: OpenAI's API platform now lets organizations and individual projects restrict which service tiers (like default, flex, or priority) are allowed, to control cost and processing behavior.
---

## What changed

OpenAI added service tier controls to its API platform. In a project's Platform settings, you can now choose which service tiers that project is allowed to use. Organization-level settings can also restrict which service tiers are allowed across every project in the organization, and a project cannot enable a tier the organization has blocked.

A service tier is the processing option a request uses — OpenAI's documentation names tiers including `default`, `flex`, and `priority` (the `fast` tier is treated the same as `priority` for this feature). If a request sets `service_tier` to a tier that isn't allowed for its project — or uses `auto` and that resolves to a disallowed tier — the API now returns a 400 error with `error.param` set to `service_tier`.

## Why it matters

Before this, any project could use any service tier, which made it easy to accidentally use a more expensive tier (like priority processing) in a project that was only supposed to use the standard, cheaper option. This gives organizations a way to enforce that at the platform level instead of relying on every developer remembering to set the right parameter.

## How to use it

- As a project admin: go to the project's Platform settings and choose the allowed service tiers for that project.
- As an organization admin: set organization-wide allowed service tiers; these act as a ceiling that no project can exceed.
- If a request fails with a 400 error naming `service_tier`, either change the request's `service_tier` value to one the project allows, or update the project's (or organization's) allowed tiers.

## Source

- [OpenAI API changelog — October 21, 2026](https://developers.openai.com/api/docs/changelog)
- [OpenAI API error codes — service tier errors](https://developers.openai.com/api/docs/guides/error-codes)
