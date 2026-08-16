# twsta

Persistent memory for coding agents. A skill that gives the agent a second brain — an
Obsidian-native Markdown vault it reads for context and writes durable facts back to,
so nothing is forgotten between sessions.

## Why

Local coding agents are powerful but amnesiac. Every session starts cold: no memory of
who you are, your mission, your priorities, how you talk, or what you decided. twsta
fixes that with a predictable vault the agent treats as a real second brain.

## How it works

Two jobs, one skill:

- **Bootstrap** — creates the vault skeleton (`INDEX.md` + `00_self/` + projects,
  decisions, knowledge) the first time it runs.
- **Operate** — reads `INDEX.md` for context at session start, follows your voice and
  rules, and writes durable facts (decisions, preferences, learnings) back. No session
  logs — durable facts only.

The vault is written with Obsidian-native syntax (`[[wikilinks]]`, YAML frontmatter,
tags), so you open the same folder in Obsidian and share one source of truth.

## Vault location

`$TWSTA_DIR` → `/workspaces/twsta` → `~/twsta` (first match wins).

## Install

```bash
npx skills add <owner>/twsta
```

## Usage

Just talk to your agent normally. The skill triggers on session starts, "continue where
we left off", "you remember", personal/project context questions, and style/voice
requests.

## Security

Never stores secrets. Vault content is plaintext markdown — treat it as non-secret.