---
title: OpenAI adds admin controls for who can create API keys
date: 2026-09-21
description: OpenAI now lets organizations restrict how new API keys get created, so admins can block risky key types before they're issued.
---

## What changed

OpenAI added a new "API Key Governance" section to Platform settings in the OpenAI API dashboard. It lets organization and project administrators restrict what kinds of API keys people are allowed to create going forward. Admins can pick one of three modes:

- Allow only service-account keys (keys tied to an automated system, not a person)
- Allow only user-owned project keys (keys tied to an individual's account)
- Disable new API key creation entirely

Organization-level settings always win: a project can add stricter rules on top, but it can't loosen a restriction the organization has already set. The controls only affect keys created from now on — any API keys that already exist keep working as before.

## Why it matters

An API key is a password-like string that lets code call the OpenAI API. Loose or leaked keys are a common security problem, especially at companies where many people can generate their own. This gives admins a way to close that off before it becomes an incident, without having to police it key by key after the fact.

## How to use it

Organization or project admins can go to Platform settings in the OpenAI developer dashboard and open the API Key Governance section to choose a policy. The setting is enforced immediately for any new key creation attempts; it does not touch keys that already exist.

## Source

- [OpenAI API changelog](https://developers.openai.com/api/docs/changelog)
- [Production best practices — API keys](https://developers.openai.com/api/docs/guides/production-best-practices#api-keys)
