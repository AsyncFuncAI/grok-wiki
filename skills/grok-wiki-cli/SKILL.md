---
name: grok-wiki-cli
description: >-
  Use the `grok-wiki` CLI to generate local-agent repository wikis, ask
  evidence-backed questions about one or more repositories, inspect saved wikis,
  or run the local Grok-Wiki server/sidecar. Trigger when the user asks for
  Grok-Wiki CLI usage, wiki generation from GitHub or local repos, multi-repo
  workspace Ask, local CLI agent selection (Grok, Codex, Claude, Pi,
  Antigravity), or troubleshooting the local-cli-only wiki/ask flow. Keep the
  workflow BYOC/BYOK and vendor-agnostic: do not require API-provider keys or
  assume one model provider unless the user explicitly chooses one local agent.
---

# Grok-Wiki CLI

Use this skill when the task should go through the public `grok-wiki` command rather than desktop UI clicks, direct server API calls, or provider-specific scripts.

## When To Use

Use `grok-wiki` for:

- generating repository wikis from GitHub shorthands, GitHub URLs, or local folders
- asking codebase questions against one repo or a multi-repo workspace
- checking local CLI agent readiness
- listing locally saved wikis
- starting the local server, worker, or local-cli sidecar
- explaining or debugging the Grok-Wiki CLI command surface

Do not use `grok-wiki` when the task is to edit Grok-Wiki source code itself unless the user specifically asks to exercise the CLI.

## Preconditions

- Prefer the public `grok-wiki` command first.
- If `grok-wiki` is unavailable but the current repo is Grok-Wiki, use `bun run ./bin/grok-wiki.ts`.
- `rlm-wiki` is a legacy alias with the same CLI behavior; use it only as a fallback or when the user names it.
- Wiki generation and Ask are local-cli only. Do not add provider API-key checks or route through cloud model APIs for these commands.
- A local agent must be installed and authenticated: `grok`, `codex`, `claude`, `pi-codex`, `pi-claude`, or `antigravity`.

First check the CLI and local agent availability:

```bash
command -v grok-wiki || command -v rlm-wiki
grok-wiki agents --rescan
```

If the command is not installed but you are inside the Grok-Wiki repository:

```bash
bun run ./bin/grok-wiki.ts agents --rescan
```

If no local agent is ready, report the selected agent's setup hint from `grok-wiki agents --rescan` and stop before starting generation.

## Core Workflow

1. Identify sources:
   - GitHub shorthand: `owner/repo`
   - GitHub URL: `https://github.com/owner/repo`
   - Local path: `./repo`, `/abs/path/repo`, `~/repo`
   - Local path ref: `~/repo#main`

2. Check agent readiness:

```bash
grok-wiki agents --rescan
```

3. Choose agent behavior:
   - Omit `--agent` to use the first ready local CLI agent.
   - Pass `--agent <id>` when the user chose a specific local agent.
   - Pass `--model <model>` and `--reasoning <level>` only when the selected local agent supports them.

4. Run `generate`, `ask`, or another command.

5. For long-running generation, keep the user updated with concise progress. Do not claim success until the command exits successfully and reports a saved wiki.

## Command Surface

### Agents

```bash
grok-wiki agents --rescan
```

Why: verifies local sidecar availability and which local agents are installed, authenticated, and runnable.

Supported agent ids:

```text
grok
codex
claude
pi-codex
pi-claude
antigravity
```

### Generate Wiki

```bash
grok-wiki generate <source...> [--agent ID] [--model MODEL] [--reasoning LEVEL] [--pages N] [--page-count-mode auto|fixed] [--style STYLE] [--language LANG] [--concurrency N]
```

Use the CLI-facing `--reasoning` flag. Some local-agent process logs may mention provider-specific or downstream names such as `--reasoning-effort`; do not pass those log-only flag names to `grok-wiki`.

Examples:

```bash
grok-wiki generate expressjs/express
grok-wiki generate expressjs/express --agent codex --model <model-name> --pages 8 --style first-30
grok-wiki generate ./api ./web --agent claude --page-count-mode fixed --pages 6
grok-wiki generate ~/work/repo#main --style custom --style-prompt-file ./operator-runbook-prompt.md
```

Defaults:

- agent: first ready local CLI agent
- style: `first-30`
- pages: `auto` up to `6`
- language: `en`
- storage: `~/.rlm-wiki`, unless `GROK_WIKI_ROOT` or `RLM_WIKI_ROOT` is set. The legacy `~/.rlm-wiki` name is intentional for backward compatibility even when using the `grok-wiki` binary.

Use `--style custom` only with `--style-prompt` or `--style-prompt-file`.
Prefer `--style-prompt-file` for multi-sentence custom prompts so shell quoting and agent wrappers cannot alter the prompt.

### Ask

```bash
grok-wiki ask <source> "question" [--agent ID] [--model MODEL] [--reasoning LEVEL] [--mode fast|deep]
grok-wiki ask <source...> --question "question" [--workspace-goal compare|steal|understand|bridge|audit]
```

Examples:

```bash
grok-wiki ask expressjs/express "How does routing work?" --mode deep
grok-wiki ask ./api ./web --question "Compare auth flows" --workspace-goal compare
grok-wiki ask owner/repo-a owner/repo-b --question "What should we steal?" --workspace-goal steal
```

Ask modes:

- `fast`: focused inspection and concise answer
- `deep`: broader investigation with stronger evidence

Workspace goals:

- `compare`
- `steal`
- `understand`
- `bridge`
- `audit`

### List Saved Wikis

```bash
grok-wiki list
```

Use this to find existing local wiki records before regenerating.

### Server, Worker, Sidecar

```bash
grok-wiki serve --port 3141 --host 127.0.0.1
grok-wiki worker --once
grok-wiki sidecar --token TOKEN --port 0 --host 127.0.0.1 --stamp PATH
```

Use `serve` for a local web/API runtime. Use `worker` and `sidecar` only when the task explicitly involves the Grok-Wiki runtime process model or local CLI adapter debugging.

## Agent Guidance

- Treat `grok-wiki` as local-cli only for wiki generation and Ask. Do not require `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `GEMINI_API_KEY`, or other provider API keys.
- Keep BYOC/BYOK behavior intact: let the user's selected local CLI agent own provider/auth details.
- Prefer explicit `--agent` only when the user chose one. Otherwise use the CLI's first-ready-agent default.
- Validate enum-like flags instead of guessing: agent ids, ask modes, workspace goals, styles, page-count modes, and languages must be known values.
- Use local paths directly for local repos; do not force GitHub remotes.
- For multi-repo tasks, pass each source positionally and use `--question` for Ask.
- Do not use `--runtime rlm` or cloud-provider runtime flags. The CLI accepts only `--runtime local-cli` for these flows.
- If a run fails because the sidecar or selected agent is unavailable, run `grok-wiki agents --rescan` and report the setup hint.
- For source-code changes to the CLI itself, run at least:

```bash
bun test src/cli.test.ts
bunx tsc --noEmit
git diff --check
```

If changing generator, Ask, sidecar, or streaming behavior, also run focused tests for the touched surface and preserve scoped streaming render contracts.
