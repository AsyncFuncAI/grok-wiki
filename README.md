<p align="center">
  <img src="https://grok-wiki.com/grok-wiki-preview-bottom-left.png" width="100%">
</p>

<div align="center">

# Grok-Wiki

**Bring your local agents. Keep the context yours.**

</div>

Grok-Wiki is a desktop app powered by local CLI agents that turns GitHub repositories and local codebases into source-cited technical wikis, architecture guides, and codebase maps.

## Download

**Latest release:** [Grok-Wiki 0.0.32](https://github.com/AsyncFuncAI/grok-wiki/releases/latest)

| Platform | Download |
|----------|----------|
| macOS Apple Silicon | [Grok-Wiki_0.0.32_aarch64.dmg](https://github.com/AsyncFuncAI/grok-wiki/releases/download/0.0.32/Grok-Wiki_0.0.32_aarch64.dmg) |

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

### 0.0.32
- Normalizes Ask current-workspace scopes across localized labels, mixed scope lists, badges, summaries, and interview prompts
- Adds the minimal current Tauri dialog permission needed by terminal and confirmation flows without broadening event or file-system grants
- Retries transient SQLite locks for lower-frequency run and artifact writes while keeping stream-event persistence on the historical timeout boundary
- Expands regression coverage for scope normalization, desktop capability alignment, and SQLite lock timeout restoration
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.30
- Fixes desktop Ask `FailedToOpenSocket` failures where Claude Code or another Local CLI agent worked in Terminal but could not reach provider APIs from the app
- Carries safe login-shell network config, including proxy, `NO_PROXY`, and CA bundle settings, into the bundled desktop server while continuing to filter provider API keys from agent processes
- Adds PostHog Ask failure classification and capture for request failures, terminal stream errors, and streamed agent error text
- Expands regression coverage for Local CLI environment filtering and Ask error classification without coupling runs to one model provider
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.29
- Adds desktop Ask sharing so completed Ask sessions can be published, copied, updated, or unpublished from the Ask view
- Creates public read-only Ask pages with sanitized session payloads and stable links managed by the local desktop server
- Adds public Ask website assets alongside the existing public wiki surface without changing the desktop app bundle boundary
- Fixes a Safari/WebKit boot-order crash that could prevent the desktop shell from rendering after persisted navigation state loaded
- Hardens run-event persistence so disk-full SQLite failures stop retry storms while live streams keep updating in memory
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.28
- Adds server-side PostHog error capture for the desktop local server and API flows
- Redacts exception messages and stack traces, stripping paths, URLs, emails, tokens, and long identifiers before anything leaves the process
- Rate-limits exception reporting so a failure loop cannot flood telemetry
- Syncs the desktop analytics opt-out state to the bundled server so privacy settings disable both client-side and server-side capture
- Adds hosted/server telemetry controls through `RLM_WIKI_SERVER_TELEMETRY` without coupling runs to one model provider or changing BYOK/BYOC execution paths
- Refactors Ask outline, Wiki stream, document tabs, and repo route controllers while preserving scoped rendering boundaries for high-frequency streams
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.27
- Adds a local-first Tasks board that turns Ask findings into backlog cards, epics, and sub-tasks
- Adds Ask-to-Tasks extraction so local CLI agents can distill engineering answers into actionable work without locking users to one provider
- Runs tasks from cards through detected local agents, with watchable terminal transcripts, completion reconciliation, and change summaries
- Adds screenshot attachments for Ask and Clarify flows on supported local CLI agents, with clear gating for runtimes that cannot read images
- Fixes clarified Ask turns so clarification answers reach the model and appear as a visible Clarified pill in the thread
- Keeps Docs and Wiki generation progress scoped to the owning surface so a Docs run does not stream into the Wiki panel
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.26
- Adds Knowledge Bases that distill Ask sessions into source-grounded study cards and merge new evidence with existing cards
- Adds Knowledge Base publishing and private read links, with a calmer record-shop workspace and card/list review modes
- Changes project Knowledge Base affordances to lightbulbs that light up when a project has a Knowledge Base
- Adds guided Wiki and Ask interview flows that ask short clarifying questions before generation, while preserving skip paths for fast runs
- Adds Episode 06, “Jealousy-Driven Development,” to promote Ask as a multi-repository study partner
- Expands regression coverage for Knowledge Base storage, merge, publish, project grouping, Ask clarify, Wiki interview, render scope, and desktop routing
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.25
- Adds a floating outline peek for multi-turn Ask sessions so long answers stay navigable without leaving the current turn
- Keeps Ask outline updates scoped to the active surface instead of repainting the broader desktop shell during streaming
- Improves project item rendering and repository grouping coverage so project lists stay stable as repository metadata changes
- Adds focused regression tests for Ask outline render scope and project grouping behavior
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.24
- Adds warmer 90s memory-style desktop entry surfaces for Projects, Wiki, Ask, Docs, and the launchpad
- Reworks Projects into an image-backed cover while keeping the dense project list and New Project action visible
- Gives Ask, Wiki, and Docs calmer top-of-page visual treatments; Ask keeps the composer separate from the image hero
- Refreshes the launchpad with a softer office coffee-kitchen banner, no logo mark, clearer explanatory copy, and a sharper placeholder for repo, folder, or question starts
- Removes the extra Wiki and Docs gallery refresh button for a calmer generation surface
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.23
- Fixes packaged macOS terminal-agent launches when the sidecar detects Claude, Codex, Grok, or another local CLI but the app's narrower GUI PATH cannot find the executable
- Launches local agents through the detected executable path, preserving BYOK/BYOC setups across shell managers, npm install roots, Volta, asdf, mise, nvm, and fnm
- Keeps very fast startup exits visible long enough to show diagnostics instead of flickering the pane closed after a failed launch
- Preserves Orca-style close-on-exit behavior for established terminal panes
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.22
- Adds desktop completion attention for long-running wiki and Ask work with native alerts, optional sound, dock badge counts, and deep links back to the finished item
- Upgrades the embedded terminal with xterm-backed PTYs, compact project/runtime controls, and calmer empty states
- Adds Orca-style `Cmd+D` split-right and `Cmd+Shift+D` split-down terminal shortcuts while keeping splits inside the same tab
- Makes natural `exit` close the shell pane, prevents duplicate split panes, and keeps surviving panes visible when another pane exits
- Tightens streaming render boundaries so Ask answers, wiki progress, and terminal updates patch their owning surfaces instead of repainting the desktop shell
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.21
- Adds Orca-style first-run onboarding for choosing a local CLI agent, appearance, and app UI language
- Adds English, Japanese, and Mandarin desktop language choices while keeping generated wiki output language separate
- Updates desktop branding with the Grok-Wiki favicon, app icon, and website-matched wordmark treatment
- Redesigns Ask thinking steps into human-readable progress states instead of raw command/path logs
- Smooths high-frequency stream updates by coalescing process events and patching only the active Ask timeline
- Fixes Grok CLI live-answer runs so a Research Agent indicator stays visible even when answer text streams before tool events
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.20
- Fixes the desktop Local CLI picker so selecting Grok CLI, Codex CLI, Claude Code, Pi, or Antigravity reliably switches the active local agent
- Keeps refreshed local-agent menu rows clickable during readiness rescans
- Opens setup instructions when the newly selected local CLI agent is missing or blocked
- Adds regression coverage for refreshed menu rows, rebinding safety, persisted local-runtime selection, and setup-popover visibility
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

### 0.0.19
- Improves desktop local CLI discovery for custom npm, pnpm, Bun, Volta, asdf, mise, nvm, and fnm install roots
- Retries Grok CLI startup in headless streaming mode when the ACP initialize/session path fails
- Adds regression coverage for local CLI path discovery, fake-machine test isolation, and Grok fallback behavior
- Signed and notarized macOS Apple Silicon DMG plus Tauri updater artifacts

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
