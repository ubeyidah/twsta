# Twsta

A second brain for your coding agent. A simple skill that gives the agent permanent memory of who you are, your voice, your rules, and your decisions, stored as Obsidian-native markdown on your machine.

I kept finding myself using coding agents over web apps. They're powerful, they have real access, they can do everything. But there's one problem. Tell an agent something today, come back tomorrow, it's gone. It forgets who I am, what I'm building, how I write, what I decided. I lost whole sessions of context.

So I built twsta. It's a second brain for the agent, stored on your computer as plain markdown. The agent reads it at the start of every session, follows it while it works, and writes durable facts back. It remembers everything.

And because the vault is Obsidian-native, you open the same folder in Obsidian and browse the brain like your own notes. Everything links with [[wikilinks]], tags, and frontmatter, the Obsidian way.

## No setup, no dependencies

Twsta is just a skill that manages a folder of markdown files. No database, no server, no runtime, nothing to install beyond the skill itself. It reads and writes plain notes, that's the whole job. The agent already knows how to handle files, so there's nothing new to learn.

## Install

```bash
npx skills add ubeyidah/twsta
```

That's it. No keys, no accounts, no cloud.

## What it does

- learns you, not just your tasks. on first use it asks a few short questions, then remembers
- keeps your voice. tweets, posts, and commits read like you wrote them
- saves decisions with the reason, so settled arguments stay settled
- stores what you know deeply, so it never re-explains things twice

## How it works

First session, the agent bootstraps the vault and asks a few short questions. What should I call you? What are you building right now? How does your writing sound, show me an example? Any rules I should never break?

Every session after that, it loads the vault first, follows your voice and your rules, and writes durable facts back. No session logs, just facts that still matter next week.

## Vault structure

```
twsta/
├── INDEX.md                the map, every note one line and a link
├── 00_self/
│   ├── identity.md         who you are
│   ├── mission.md          why you build what you build
│   ├── priorities.md       what matters now
│   ├── voice.md            how you talk and post
│   └── rules.md            hard rules for the agent
├── 10_projects/            one note per project
├── 20_decisions/           decisions with the why, dated
└── 30_knowledge/           durable facts and learnings
```

The vault lives at `$TWSTA_DIR` if you set it, else `/workspaces/twsta`, else `~/twsta`.

## Migrate from another agent

Already have memory in a `CLAUDE.md`, `AGENTS.md`, Cursor rules, or an old vault? Paste this to your agent and it moves everything over.

```text
You are setting up my Twsta second brain. My old agent knowledge is
in [PATH_OR_PASTE]. Read it and migrate everything durable into the
Twsta vault. Rules:

1. Map each fact to the right note: identity, mission, priorities,
   voice, rules, projects, decisions, knowledge.
2. Fill every 00_self note with real content, ask me to fill gaps.
3. Turn each past decision into a dated note in 20_decisions/
   with the decision, why, and alternatives considered.
4. Put reusable knowledge in 30_knowledge/, one topic per note.
5. Create one 10_projects/ note per project, with current state.
6. Update INDEX.md so every note is listed with a one-line summary.
7. Link related notes with [[wikilinks]].
8. Do NOT copy secrets, API keys, or chat logs.
9. Show me what you migrated when done.
```

Run it once and your existing knowledge becomes a living second brain instead of a dead doc.

## Security

No secrets stored, ever. The vault is plaintext markdown on your machine, so treat it as non-secret. If you share a token mid-task, the agent keeps it out of the vault.