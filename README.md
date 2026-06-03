# Grok-Wiki

Grok‑Wiki is a desktop app powered by local CLI agents that turns GitHub repositories and local codebases into source‑cited technical wikis, architecture guides, and codebase maps.

## Download

**Latest release:** [Grok-Wiki 0.0.18](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)

| Platform | Download |
|----------|----------|
| macOS Apple Silicon | [Grok-Wiki_0.0.18_aarch64.dmg](https://github.com/AsyncFuncAI/grok-wiki/releases/download/0.0.18/Grok-Wiki_0.0.18_aarch64.dmg) |

## Requirements

- macOS on Apple Silicon (M1/M2/M3/M4)
- One local agent CLI installed and authenticated: Grok CLI, Codex CLI, Claude Code, Pi, or Antigravity CLI

## Install

1. Download the `.dmg` from the [latest release](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)
2. Open the `.dmg` and drag **Grok-Wiki.app** to `/Applications`
3. Launch **Grok-Wiki.app**
4. Choose a local agent in the app and follow the setup copy if it is not installed yet

## What It Does

- Generates repository wikis from GitHub repos and local paths
- Uses local CLI agent execution through Grok CLI, Codex CLI, Claude Code, Pi.Codex, Pi.Claude, and Antigravity CLI
- Saves generated wiki artifacts locally
- Publishes read-only wiki snapshots to grok-wiki.com for lightweight sharing
- Includes default generated wiki examples for first-run exploration
- Offers outcome-led wiki formats for mental models, hidden quirks, feature scouting, repo comparison, debugging maps, and tech-reader briefs
- Turns generated wikis into in-app slide previews for lightweight sharing

## Local Agent Setup

Grok-Wiki can run with any supported local CLI agent:

- Grok CLI: after install, authenticate with `grok login`
- Codex CLI: install with `npm i -g @openai/codex` or `brew install codex`, then authenticate with `codex login`
- Claude Code: install with `curl -fsSL https://claude.ai/install.sh | bash`, then authenticate locally
- Pi.Codex: install Pi with `npm install -g --ignore-scripts @earendil-works/pi-coding-agent`, start `pi`, enter `/login`, and select ChatGPT Plus/Pro (Codex)
- Pi.Claude: install Pi with `npm install -g --ignore-scripts @earendil-works/pi-coding-agent`, start `pi`, enter `/login`, and select Claude Pro / Max
- Antigravity CLI: install with `curl -fsSL https://antigravity.google/cli/install.sh | bash`, then run `agy` once and complete Google Sign-In if prompted

## Changelog

### 0.0.18
- Fixes a desktop React dependency mismatch that could trigger invalid hook call errors at startup
- Restores Pi local-agent logo assets in public web builds
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.17
- Adds in-place Docs Chat for documentation pages, with follow-up and new-question support without routing users to Ask
- Prioritizes current generated documentation MDX before repository inspection for documentation questions
- Preserves selected local CLI agent and model for Docs Chat runs
- Improves Docs Chat typing and streaming responsiveness with scoped panel updates
- Fixes desktop and public docs rendering for tabs, light-mode highlights, Python syntax highlighting, Mermaid diagrams, and code copy controls
- Adds public docs video thumbnail metadata for Google video indexing
- Strengthens the release runbook so public main and release tags stay limited to README.md and skills/
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.16
- Adds public wiki publishing and gallery surfaces for read-only wiki sharing
- Adds public agent handoff copy for provider-neutral follow-up work
- Improves desktop wiki reading, markdown rendering, diagram handling, and publishing controls
- Adds bundled Grok-Wiki agent skills for CLI and ask-first custom wiki workflows
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.15
- Allows local folders without a `.git` directory to be used for read-only Ask and Wiki generation
- Keeps branch and ref selection Git-only while adding clearer desktop confirmation for local folder mode
- Adds richer local CLI failure diagnostics, Anthropic SDK stderr capture, and a configurable Antigravity quiet-output timeout
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.14
- Adds Pi.Codex and Pi.Claude as local CLI agent runtime options for desktop Ask workflows
- Adds Pi agent readiness, install, and auth guidance while preserving the local, user-owned credential model
- Improves local CLI streaming and markdown rendering so Pi/Codex/Claude-style agent output stays scoped and readable
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.13
- Compacts noisy wiki source citations into a subtle sources disclosure in desktop and public wiki readers
- Fixes a desktop-only renderer override that could still show raw Sources lines after Mermaid setup
- Keeps the desktop app bundle scoped to local app assets while shipping signed, notarized macOS artifacts
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.12
- Adds format previews so users can peek at each wiki style before spending a run
- Adds a floating wiki ask composer that opens directly into Ask with the wiki attached as context
- Adds quota-aware page guidance for larger wiki runs
- Improves public wiki markdown access for agentic readers and generation status handling for partial failures
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.11
- Adds privacy-first desktop product analytics with a local Settings > Privacy opt-out
- Keeps analytics explicit: no session replay, autocapture, pageviews, prompts, code, repo names, local paths, API keys, or run logs
- Allows Ask to select local folders that are not Git repositories
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.10
- Adds private link sharing for wikis while keeping private snapshots out of the public gallery
- Adds Obsidian-ready Markdown ZIP export for local/team knowledge workflows
- Adds print-to-PDF export from the desktop Share flow
- Improves public wiki sharing route clarity and gallery visibility handling
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.9
- Adds Markdown ZIP export from the desktop Share flow
- Adds Explain Like I'm 5 wiki format
- Improves Antigravity CLI wiki generation reliability
- Refines wiki reader and gallery polish, including scroll/pages controls, theme support, and search behavior
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.8
- Adds public wiki publishing and sharing to grok-wiki.com
- Adds dynamic social preview images for public wiki links
- Adds public wiki diagram zoom for Mermaid and detected ASCII diagrams
- Improves desktop wiki reader controls, continuous scroll, hotkey feedback, and configurable wiki defaults
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

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
