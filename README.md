<div align="center">

# Twsta

**The second brain for your AI coding agent.**

Local agents are powerful — but they forget everything overnight. Twsta gives your
agent a permanent, Obsidian-native memory vault on your machine, so it actually
learns who you are, how you talk, what you're building, and what you decided.

`npx skills add ubeyidah/twsta`

</div>

---

## Table of contents

- [The problem](#the-problem)
- [The solution](#the-solution)
- [How it works](#how-it-works)
- [Install](#install)
- [How to work with it](#how-to-work-with-it)
- [Migrating from another AI agent](#migrating-from-another-ai-agent)
- [Vault structure](#vault-structure)
- [Why Obsidian](#why-obsidian)
- [Advantages](#advantages)
- [Security](#security)

---

## The problem

Every local coding agent (Claude Code, opencode, Cursor, and friends) starts every
session from zero. Ask it *"remember how I like my commit messages"* the day after you
told it, and it has no idea.

- No memory of **who you are** — your name, your role, your context.
- No memory of **your mission** — why you build what you build.
- No memory of **your priorities** — what matters right now.
- No memory of **your voice** — how you talk, write, and post.
- No memory of **your decisions** — and why you made them.
- No memory of **what you know** — so it re-explains things you've mastered.

You end up repeating yourself, re-arguing settled decisions, and fixing tone forever.
The agent is smart but *amnesiac* — all that intelligence, no continuity.

## The solution

**Twsta is a second brain.** A predictable, structured Markdown vault that lives on
your computer and persists between sessions. The agent:

1. **Reads** the vault at the start of every session to load context.
2. **Follows** it during work — your voice, your rules, your priorities.
3. **Writes** durable facts back — decisions, learnings, project state.
4. **Learns you** actively on first use, by asking one question at a time.

The result: an agent that gets better every session instead of resetting to zero.
It *remembers* you, the way a good collaborator does.

## How it works

Twsta is a skill — a set of instructions your agent follows automatically. It runs in
two modes:

| Mode | When | What happens |
|------|------|--------------|
| **Bootstrap** | Vault doesn't exist yet | Creates the full vault skeleton from bundled templates |
| **Learn** | Vault is thin/empty | Asks you questions, one at a time, and fills your profile |
| **Operate** | Every session | Loads context at start, follows your voice & rules, writes durable facts back |

The vault is written in **Obsidian-native Markdown** — `[[wikilinks]]`, YAML
frontmatter, tags, numbered folders. That means your agent and your note-taking app
share one source of truth: open the same folder in Obsidian and you can read, link,
graph, and query your agent's memory like your own notes.

## Install

```bash
npx skills add ubeyidah/twsta
```

That's it. No API keys, no accounts, no cloud. The vault is created automatically on
your machine at the first session that needs it.

## How to work with it

Nothing to configure — just talk to your agent normally. Twsta triggers on:

- **Session starts** — "let's get going", "picking up where we left off"
- **Memory requests** — "you remember", "as I said before", "what was I working on"
- **Personal context** — "my priorities", "my mission", "what am I building"
- **Voice & style** — "write this in my voice", "like I always do"
- **Any decision or fact worth keeping** — "we decided to use X because Y"

### First session

The agent will ask you a few short questions to learn who you are:

> "What should I call you, and what do you do?"
> "What's your top priority this week?"
> "How do you like your writing to sound? Paste an example."
> "Any hard rules I should never break?"

Answer naturally — each answer is recorded into the vault. Corrections are gold: when
you fix the agent's tone or give a rule, it writes that down immediately.

### Every session after

```text
You:   continue where we left off. what's my top priority?
Agent: finishing the sync engine this week. you decided to stay
       with sqlite for lumen because it keeps data local-first.
       and yes — lowercase, short lines, no emoji, as usual.
```

## Migrating from another AI agent

Already have memory elsewhere — a `CLAUDE.md`, `AGENTS.md`, Cursor rules, an old
Obsidian vault, or just a brain-dump doc? Copy the knowledge into Twsta by pasting
this prompt to your agent:

```text
You are setting up my Twsta second brain. My old agent knowledge is
in [PATH_OR_PASTE]. Read it and migrate everything durable into the
Twsta vault (set TWSTA_DIR if needed). Rules:

1. Map each fact to the right note: identity, mission, priorities,
   voice, rules, projects, decisions, knowledge.
2. Fill every 00_self note (identity, mission, priorities, voice,
   rules) with real content — ask me to fill anything missing.
3. Turn every past decision into a dated note in 20_decisions/
   (decision, why, alternatives considered).
4. Put reusable knowledge into 30_knowledge/, one topic per note.
5. Create one 10_projects/ note per project, with current state.
6. Update INDEX.md so every note is listed with a one-line summary.
7. Link related notes with [[wikilinks]].
8. Do NOT copy secrets, API keys, or ephemeral chat logs.
9. Show me what you migrated when done.
```

Run it once and your existing knowledge is a living second brain instead of a dead doc.

## Vault structure

```
twsta/                      # $TWSTA_DIR → /workspaces/twsta → ~/twsta
├── INDEX.md                # the map — every note, one line + link
├── 00_self/                # who you are
│   ├── identity.md         # name, role, tools, key facts
│   ├── mission.md          # why you exist / goals
│   ├── priorities.md       # what matters NOW (changes often)
│   ├── voice.md            # how you talk & post — style + examples
│   └── rules.md            # hard rules for the agent (non-negotiables)
├── 10_projects/            # one note per project
├── 20_decisions/           # decisions + why, dated (ADR-style)
└── 30_knowledge/           # durable facts, learnings, your expertise
```

Numbered prefixes keep the folders stable in Obsidian's file explorer. Every note is
atomic (one topic), linked via `[[wikilinks]]`, and carries YAML frontmatter with
`tags`, `created`, and `updated` dates.

## Why Obsidian

- **You can read it.** Your agent's memory is plain Markdown, not a database.
- **It's yours.** Local files on your machine — no lock-in, exportable forever.
- **It's a real brain.** Wikilinks and tags give you backlinks, a graph view, and
  fast navigation over everything the agent has learned.
- **It grows with you.** Edit notes yourself; the agent respects what you write.

## Advantages

- **Permanent memory.** Nothing is forgotten between sessions — ever.
- **Learns you, not just your tasks.** Identity, mission, priorities, voice, rules.
- **Speaks your voice.** Every tweet, post, and commit reads like you wrote it.
- **Structured recall.** A fast INDEX map + wikilinks mean the right fact is found
  quickly, not buried in a chat log.
- **Decisions with reasons.** Settled arguments stay settled — the "why" is saved.
- **Agent-agnostic.** Works with any agent that can read and write Markdown files.
- **Zero setup.** No accounts, no keys, no cloud, no subscription.
- **Durable only.** No session-log noise — just facts that matter next week.
- **Obsidian-native.** One source of truth shared with your own notes app.

## Security

- Twsta **never** stores secrets, API keys, tokens, or credentials.
- The vault is plaintext Markdown on your machine — treat it as non-secret.
- If you share a secret mid-task, the agent keeps it out of the vault.

---

<div align="center">

**Give your agent a memory. Start a session and just talk to it.**

`npx skills add ubeyidah/twsta`

</div>