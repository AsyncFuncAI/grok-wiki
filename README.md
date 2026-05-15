# Grok-Wiki

Grok-Wiki is a desktop app powered by Grok CLI that turns GitHub repositories and local codebases into source-cited technical wikis, architecture guides, and codebase maps.

## Alpha 0.0.1

This alpha release ships the macOS Apple Silicon desktop build.

Download:

- `releases/Grok-Wiki_0.0.1_aarch64.dmg`

Requirements:

- macOS on Apple Silicon
- Grok CLI installed and authenticated locally

## What It Does

- Generates repository wikis from GitHub repos and local paths
- Uses local CLI agent execution through Grok CLI
- Saves generated wiki artifacts locally
- Includes default generated wiki examples for first-run exploration

## Verify

```sh
shasum -a 256 releases/Grok-Wiki_0.0.1_aarch64.dmg
```

Expected SHA-256:

```text
f868976d40e549af0da0eefb4055e7490d6531b6254bda9a72bcfbfee91851a2
```
