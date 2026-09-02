---
title: "ChatGPT roundup: personalized temporary chats, DALL·E GPT retires"
date: 2026-08-30
description: Temporary chats can now optionally use your saved memory and settings, and the standalone DALL·E GPT tool is retired in favor of ChatGPT Images.
---

## What changed

Two smaller ChatGPT updates landed in late August 2026:

**Personalized temporary chats (rolled out starting August 27):**
Temporary Chat is ChatGPT's mode for a conversation that isn't saved to your chat history. Previously, a temporary chat never used your saved memory, custom instructions, or connected plugins. Now, when you start a temporary chat, you can choose between two modes:
- **Non-personalized (the default)**: works as before — no access to your memory, custom instructions, or plugins, and nothing from it is saved.
- **Personalized**: the chat can use your existing saved memories, custom instructions, and plugins to tailor its answers. It still doesn't create *new* memories while the chat stays temporary, and it's still left out of your regular chat history unless you choose to save it.

You pick the mode when you start the temporary chat; it can't be changed partway through. If a temporary chat turns out to be worth keeping, you can save it into your regular chat history, at which point it starts following your normal account settings (including data-use preferences for model training).

**DALL·E GPT retired (effective August 30):**
OpenAI shut down the standalone "DALL·E" GPT tool inside ChatGPT. Image generation in ChatGPT is not going away — this only removes the separate, older DALL·E-branded tool. It's replaced by **ChatGPT Images**, which runs on OpenAI's newer `gpt-image-1` and `gpt-image-1-mini` models. Custom GPTs that you or others built with image generation turned on are not affected and keep working. Images you generate through ChatGPT Images are saved automatically to a gallery at chatgpt.com/images.

## Why it matters

The temporary-chat change gives you a middle option between a fully anonymous, throwaway chat and a fully saved one: you can get personalized answers without the conversation itself being kept, unless you decide afterward that it's worth saving. The DALL·E retirement mainly affects anyone who had images saved only inside that specific tool's interface — those images needed to be downloaded before the August 30 cutoff, since the tool no longer exists to retrieve them from.

## How to use it

- To use a personalized temporary chat, start a new temporary chat and choose "Personalized" from the menu before sending your first message.
- If a temporary chat becomes worth keeping, use the option to save it to your chat history.
- For image generation, use ChatGPT Images (the default image tool in ChatGPT) instead of the old DALL·E GPT; check chatgpt.com/images for previously generated images.

## Source

- [OpenAI Help Center: ChatGPT release notes](https://help.openai.com/en/articles/6825453-chatgpt-release-notes)
- [OpenAI Help Center: Temporary Chat FAQ](https://help.openai.com/en/articles/8914046-temporary-chat-faq)
