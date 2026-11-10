---
title: "OpenAI's Codex plugin can build and flash Game Boy-style games"
date: 2026-11-10
description: A new Codex plugin lets you design a Game Boy Color game by chatting with ChatGPT, then install it on a ModRetro Chromatic handheld.
---

## What changed

OpenAI released a Codex plugin for the ModRetro Chromatic, a handheld game console that plays Game Boy Color cartridges. Codex is OpenAI's coding agent, built into the ChatGPT desktop app. With the plugin installed, you can describe a game in chat and have Codex generate the game's code and art, then preview it in a built-in browser emulator, and finally copy the finished game onto a real Chromatic handheld.

The underlying games target the Game Boy Color format (`.gbc` ROM files). Codex builds them mainly with GB Studio, a visual game-creation tool, though it can also write lower-level code directly using GBDK-2020 (a C compiler for these consoles) or assembly language with a toolchain called RGBDS.

## Why it matters

This is a narrow, hobbyist-facing feature rather than a core API or model change — it doesn't affect anyone using OpenAI's models for regular work. It's notable mainly as an example of what a coding agent can do when paired with real hardware: instead of just producing source code, Codex here handles the whole loop — generating assets, letting you preview and tweak the game interactively by pausing a frame and pointing at what to change, and then writing the finished build to a physical cartridge over USB.

Anyone trying this should know the install step overwrites whatever game is already on the connected cartridge, and can erase its saved data — the plugin doesn't back up the cartridge first.

## How to use it

1. In the ChatGPT desktop app, choose **Codex** from the ChatGPT dropdown.
2. Open **Plugins**, search for **ModRetro Chromatic**, and install it.
3. Open a local project folder, start a chat, type `@`, and select the plugin.
4. Ask Codex to set up the plugin and check for any missing build tools.
5. Describe the game you want, then ask Codex to build it and open the preview — you can pause the preview and annotate a frame to point Codex at what to change.
6. To put the game on real hardware: update your Chromatic's firmware and turn on Developer Mode (ModRetro's own quickstart guide covers this), connect it with a USB data cable along with a rewritable homebrew cartridge, then choose **Install on Chromatic** in the preview and confirm.

Back up anything on your cartridge first — installing a new game erases the old one, including its save data.

## Source

- [OpenAI Developer Community: Build your own games on the Codex edition ModRetro Chromatic](https://community.openai.com/t/build-your-own-games-on-the-codex-edition-modretro-chromatic/1414530)
- [OpenAI Developers blog: Build a game with ModRetro Chromatic](https://developers.openai.com/blog/build-a-game-with-modretro-chromatic)
