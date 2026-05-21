# Grok-Wiki

Grok-Wiki is a closed-source desktop app powered by local CLI agents that turns GitHub repositories and local codebases into source-cited technical wikis, architecture guides, and codebase maps.

This repo is the public distribution hub — releases, issue tracking, and auto-updater metadata. Source code is maintained privately.

## Download

**Latest release:** [Grok-Wiki 0.0.7](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)

| Platform | Download |
|----------|----------|
| macOS Apple Silicon | [Grok-Wiki_0.0.7_aarch64.dmg](https://github.com/AsyncFuncAI/grok-wiki/releases/download/0.0.7/Grok-Wiki_0.0.7_aarch64.dmg) |

## Requirements

- macOS on Apple Silicon (M1/M2/M3/M4)
- One local agent CLI installed and authenticated: Grok CLI, Codex CLI, Claude Code, or Antigravity CLI

## Install

1. Download the `.dmg` from the [latest release](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)
2. Open the `.dmg` and drag **Grok-Wiki.app** to `/Applications`
3. Launch **Grok-Wiki.app**
4. Choose a local agent in the app and follow the setup copy if it is not installed yet

## What It Does

- Generates repository wikis from GitHub repos and local paths
- Uses local CLI agent execution through Grok CLI, Codex CLI, Claude Code, and Antigravity CLI
- Saves generated wiki artifacts locally
- Includes default generated wiki examples for first-run exploration
- Offers outcome-led wiki formats for mental models, hidden quirks, feature scouting, repo comparison, debugging maps, and tech-reader briefs
- Turns generated wikis into in-app slide previews for lightweight sharing

## Local Agent Setup

Grok-Wiki can run with any supported local CLI agent:

- Grok CLI: after install, authenticate with `grok login`
- Codex CLI: install with `npm i -g @openai/codex` or `brew install codex`, then authenticate with `codex login`
- Claude Code: install with `curl -fsSL https://claude.ai/install.sh | bash`, then authenticate locally
- Antigravity CLI: install with `curl -fsSL https://antigravity.google/cli/install.sh | bash`, then run `agy` once and complete Google Sign-In if prompted

## Changelog

### 0.0.7
- Adds configurable global wiki hotkeys with confirmation mode and power-user auto-run mode
- Adds subtle desktop feedback for hotkey triggers, including the floating status pill and optional haptic tick
- Improves hotkey wiki defaults for runtime, page count, and format selection
- Adds continuous-scroll wiki reading as the default with a Pages mode toggle for paged navigation
- Refines wiki reader layout so continuous markdown keeps the same readable width behavior as paged markdown
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.6
- Adds Google Antigravity CLI as a local agent alongside Grok CLI, Codex CLI, and Claude Code
- Improves local-agent Ask runs with clearer idle/loading states, better progress signals, and cancellable wiki generation
- Fixes follow-up composer submission/clearing, slash picker bounds, source citation linking, and local/remote source previews
- Adds safer page repair flows, including concurrent page regeneration without clobbering saved wiki pages
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.5
- Adds a titlebar Update button driven by the Tauri updater when a newer release is available
- Fixes follow-up submit behavior so Enter/click sends reliably and clears the follow-up input immediately
- Fixes follow-up slash-command picker positioning and keeps picker updates scoped to the active composer
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.4
- Bundles the desktop server, web assets, and Bun runtime inside the macOS app for reliable first-run startup
- Fixes local CLI readiness and run execution drift after installing Grok CLI, Codex CLI, or Claude Code while the app is open
- Adds sidecar recovery so Ask and Wiki runs can restart a stale local CLI sidecar instead of staying stuck
- Updates first-time setup copy for Grok CLI, Codex CLI, and Claude Code
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.3
- New outcome-led wiki formats for first-pass orientation, mental models, hidden quirks, feature scouting, worth-stealing analysis, debugging atlases, repo comparison, and tech-reader briefs
- Cleaner Compound Engineering lens support in Ask with slash commands, pro tips, and quieter UI copy
- Multiple concurrent wiki generations with higher page limits for larger codebase digests
- Slide generation and in-app Open Slide preview from generated wikis
- Desktop polish for sidebars, wiki controls, stream panels, feedback links, and reduced repaint/flicker during agent streaming
- Signed and notarized macOS Apple Silicon DMG and updater artifacts

### 0.0.2
- Signed updater artifacts for automatic future updates
- Grok CLI readiness fixes
- Pinned sidebar polish
- Ask source-panel hide/show toggle
- Landing download cleanup

### 0.0.1 (alpha)
- Initial macOS Apple Silicon desktop build

## Issues & Support

Found a bug or have a feature request? [Open an issue](https://github.com/AsyncFuncAI/grok-wiki/issues).
