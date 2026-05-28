---
name: grok-wiki-custom
description: >-
  Use when the user wants a higher-quality custom Grok-Wiki generated from a
  repository, GitHub URL, or local path by first clarifying the intended
  audience/outcome, then using `grok-wiki ask` with a local agent to discover
  what the repo is about, crafting a custom style prompt, and generating the
  wiki with `grok-wiki generate --style custom`. This composes the
  grok-wiki-cli workflow and keeps BYOC/BYOK local-agent behavior intact.
---

# Grok-Wiki Custom

Use this skill for intention-driven wiki generation: Ask first, prompt second, generate last.

## Preconditions

- Follow the `grok-wiki-cli` skill for CLI availability, local agent readiness, command syntax, and fallback to `bun run ./bin/grok-wiki.ts` when needed.
- Wiki generation and Ask must stay local-cli/BYOC/BYOK. Do not require provider API keys or switch cloud providers.
- If the user chooses an agent, pass `--agent <id>`. If not, use the CLI default after checking readiness.

## Workflow

1. Confirm generation intent.
   - If the user already supplied a clear intention, audience, page count, source, and agent, proceed.
   - If the intention is missing, ask one concise question before running generation: "Who is this wiki for, and what should it help them do?"
   - If page count is missing, choose a small focused default: 3 pages for custom contributor/operator/product wikis, unless the user asks otherwise.

2. Discover the repository.
   - Run `grok-wiki ask <source> "<discovery question>" --mode deep`.
   - Include `--agent <id>` if selected.
   - Ask for product purpose, architecture, key workflows, important implementation areas, contribution risks, and the highest-value page plan for the stated intention.

3. Craft a custom style prompt.
   - Write the prompt to a local file in the current shell working directory, for example `.grok-wiki-<repo>-custom-prompt.md`.
   - If the source is remote and there is no local repo workspace, write the prompt to a temp path such as `$TMPDIR/grok-wiki-<repo>-custom-prompt.md`. `--style-prompt-file` accepts absolute paths.
   - The prompt should name the exact audience, outcome, page titles, and quality bar.
   - Keep it vendor-agnostic unless the repo itself is provider-specific.
   - Include instructions to use codebase evidence, paths, contributor checklists, and tests where useful.

4. Generate the wiki.
   - Run:

```bash
grok-wiki generate <source> --agent <id> --page-count-mode fixed --pages <N> --style custom --style-prompt-file <prompt-file>
```

   - Omit `--agent` only when the user did not choose one.
   - Use the CLI-facing `--reasoning` flag if the selected agent supports a reasoning setting. Some local-agent process logs may mention downstream names such as `--reasoning-effort`; do not pass those log-only flag names to `grok-wiki`.
   - Use `--page-count-mode fixed` when the user asked for an exact page count or you chose a focused page plan.

5. Verify.
   - Wait for the command to exit successfully.
   - Run `grok-wiki list` and inspect the saved JSON path reported by generation.
   - If working in the desktop app, verify the wiki appears in the desktop library/recent list when possible.

## Discovery Question Template

Use this shape, adapted to the user's intention:

```text
What is this repository about? For the goal "<intention>", identify the product purpose, main runtime architecture, key user workflows, important implementation areas, likely contributor/operator risks, and the highest-value <N> wiki pages to generate. Use evidence from the codebase and be concise but specific.
```

## Custom Prompt Template

```markdown
Generate a focused <N>-page technical wiki for <source>.

Audience:
- <audience>

Outcome:
- <what the reader should be able to do after reading>

Core framing:
- <repo-specific purpose discovered via ask>
- Keep the architecture BYOC/BYOK and vendor-agnostic unless the code requires otherwise.
- Emphasize ownership boundaries, runtime flow, extension points, persistence, and tests relevant to the intention.

Create exactly these <N> pages:

1. "<page title>"
   <page purpose, specific topics, and key files to anchor on>

2. "<page title>"
   <page purpose, specific topics, and key files to anchor on>

3. "<page title>"
   <page purpose, specific topics, and key files to anchor on>

Quality bar:
- Prefer codebase evidence over broad summaries.
- Include important paths and line-aware references where available.
- Explain why each subsystem exists, not just what files exist.
- Note the most important tests or test categories a contributor should run.
- Avoid marketing copy unless it clarifies architecture.
- Keep each page compact, structured, and actionable.
```

Adjust the page list length to match `<N>`.

## Failure Handling

- If the selected local agent is not ready, run `grok-wiki agents --rescan` and report the setup hint. Do not silently switch agents.
- If Ask succeeds but generation fails, preserve the prompt file and report the exact failed command.
- If the generated wiki is saved but not visible in a UI, verify `grok-wiki list`, the saved JSON path, and whether the UI reads the same product root or desktop SQLite store.
