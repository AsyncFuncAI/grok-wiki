# Grok-Wiki

Grok-Wiki is a closed-source desktop app powered by Grok CLI that turns GitHub repositories and local codebases into source-cited technical wikis, architecture guides, and codebase maps.

This repo is the public distribution hub — releases, issue tracking, and auto-updater metadata. Source code is maintained privately.

## Download

**Latest release:** [Grok-Wiki 0.0.3](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)

| Platform | Download |
|----------|----------|
| macOS Apple Silicon | [Grok-Wiki_0.0.3_aarch64.dmg](https://github.com/AsyncFuncAI/grok-wiki/releases/download/0.0.3/Grok-Wiki_0.0.3_aarch64.dmg) |

## Requirements

- macOS on Apple Silicon (M1/M2/M3/M4)
- [Grok CLI](https://x.ai/grok) installed and authenticated locally

## Install

1. Download the `.dmg` from the [latest release](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)
2. Open the `.dmg` and drag **Grok-Wiki.app** to `/Applications`
3. Launch **Grok-Wiki.app**
4. Sign in with your Grok CLI credentials when prompted

## What It Does

- Generates repository wikis from GitHub repos and local paths
- Uses local CLI agent execution through Grok CLI
- Saves generated wiki artifacts locally
- Includes default generated wiki examples for first-run exploration
- Offers outcome-led wiki formats for mental models, hidden quirks, feature scouting, repo comparison, debugging maps, and tech-reader briefs
- Turns generated wikis into in-app slide previews for lightweight sharing

## Changelog

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
