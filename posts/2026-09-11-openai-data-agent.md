---
title: "OpenAI's new Data agent lets ChatGPT users query company data by asking questions"
date: 2026-09-11
description: The Data agent in ChatGPT Work connects to company databases and BI tools, and turns plain-language questions into analysis, dashboards, and shareable charts.
---

## What changed

On September 10, 2026, OpenAI introduced the **Data agent** in ChatGPT Work. It connects to a company's data sources and lets employees ask questions in plain language — like "why did sales slow down?" — instead of writing database queries or waiting for someone else to build a report. The agent investigates the question and builds interactive dashboards that can be shared and refined through further conversation.

Key details:
- **Data source connections.** The Data agent connects to sources including Amazon Redshift, Google BigQuery, ClickHouse, Databricks, MongoDB, Snowflake, and Datadog, and can pull in files from Google Drive and SharePoint.
- **Uses a company's own definitions.** Rather than guessing what a metric means, the agent uses an organization's existing business terms, metric definitions, and data relationships — sourced from tools like Databricks Genie Ontology, dbt, GitHub, and Snowflake Horizon — so its answers should match how the company already defines things internally, rather than a generic interpretation.
- **Partner quotes.** Data platform partners including AWS, Databricks, Snowflake, MongoDB, Redis, and ClickHouse provided quotes describing early integrations, generally emphasizing that customers can query live data without writing code.

## Why it matters

In many companies, answering a data question means either learning a query language and analytics tool, or waiting on a data or analytics team to run the report — both of which slow decisions down. A tool that connects directly to a company's actual databases and BI (business intelligence) context, rather than requiring data to be exported or re-explained, could meaningfully cut that wait for non-technical staff. The emphasis on using a company's existing metric definitions (rather than a generic interpretation) matters because a common failure mode for AI-assisted analytics is producing a plausible-looking but wrong answer because it doesn't understand what a specific internal term actually means.

## How to use it

- The Data agent is available now in ChatGPT Work; it can be installed as a plugin from within ChatGPT.
- It requires connecting to your organization's data sources (Redshift, BigQuery, Snowflake, Databricks, MongoDB, ClickHouse, Datadog, or files from Google Drive/SharePoint) — an admin will typically need to set up these connections first.
- Once connected, ask questions directly in conversation, and refine the resulting dashboard by continuing the conversation rather than rebuilding a query from scratch.

## Source

- [Now everyone can put data to work](https://openai.com/index/put-data-to-work/)
