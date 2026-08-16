---
name: twsta
description: 'Gives the agent a second brain — a permanent Obsidian-native Markdown vault on the computer that stores who the user is, their mission, priorities, voice, rules, projects, decisions, and knowledge, so nothing is forgotten between sessions. Use this skill at the START of every session and whenever context matters: "continue where we left off", "you remember", "as I said before", "my priorities", "my mission", "how I talk/post/write", "what was I working on", "in my voice", "like I always do", or any personal/project question where remembering the user changes the answer. The agent''s job: read the vault for context, follow the user''s voice and rules, and write durable facts back. If the vault is missing or empty, bootstrap it and actively learn the user by asking questions. Trigger on every session start and any request that needs memory of the user''s history.'
---

# twsta — the agent's second brain

twsta is a permanent memory vault for one person: the user. It lives on the
computer as a plain Markdown folder, written in Obsidian-native syntax
(`[[wikilinks]]`, YAML frontmatter, tags), so the user can open the same folder
in Obsidian and browse their own second brain.

The vault survives between sessions. The agent reads it at the start of every
session, follows it during work, and writes durable facts back. Over time the
vault becomes a true mirror of the person: who they are, what they want, how
they talk, what they decided, what they know.

## The agent's job, in one line

**Learn the user, remember the user, write in the user's voice — every session,
using the vault.**

## Vault location

Resolve in order, first match wins:

1. `$TWSTA_DIR` if set
2. `/workspaces/twsta` if `/workspaces` exists
3. `~/twsta`

Export `TWSTA_DIR` in the environment or shell profile to pin a custom location.

## Vault structure

```
twsta/
├── INDEX.md            # the map — every note, one line + link
├── 00_self/            # who the user is
│   ├── identity.md     # name, role, tools, key facts
│   ├── mission.md      # why they exist / goals
│   ├── priorities.md   # what matters NOW (changes often)
│   ├── voice.md        # how they talk & post — style + examples
│   └── rules.md        # hard rules for the agent (non-negotiables)
├── 10_projects/        # one note per project
├── 20_decisions/       # decisions + why, dated
└── 30_knowledge/       # durable facts, learnings, the user's field of expertise
```

Numbered prefixes keep the folders in a stable order in Obsidian's explorer.

## How the agent works

### Step 1 — Bootstrap (only if vault is missing)

If the vault path does not exist, create it using the bundled `templates/`
files: copy `INDEX.md` and each template into place. Do NOT overwrite notes
that already exist.

### Step 2 — Learn the user (first sessions, thin vault)

If the vault exists but the `00_self/` notes are empty or nearly empty, the
agent's first job is to LEARN the user, not just take orders. Read
`references/learning.md` for the full guide. In short: ask one question at a
time, write each answer into the right note as it comes, and never force it.
The user's corrections are gold — when they fix your tone or state a rule,
write it down immediately. Natural conversation beats a form.

### Step 3 — Session start: load context

1. Read `INDEX.md` first — the map of everything.
2. Read `00_self/*` (identity, mission, priorities, voice, rules).
3. Read the `10_projects/` note for the current project, if one matches.
4. If the task references something specific ("that decision on X"), grep the
   vault and read the matching note.

### Step 4 — During work: follow the brain

- Follow `rules.md` unconditionally.
- Write all user-facing content in the style of `voice.md`.
- If the user corrects your tone, changes a priority, or states a rule, update
  the relevant `00_self/` note immediately. A correction is durable data.

### Step 5 — After a task: write durable facts back

Record only what should still be true next week:

- Decision made → new dated note in `20_decisions/` (what, why, alternatives).
- Fact / learning → new note in `30_knowledge/` (or update an existing one).
- Project work → update the matching `10_projects/` note; create one if missing.
- Who the user is / what they want changed → update `00_self/*`.

Do NOT write ephemeral chatter (today's todos, one-off task logs, running
notes). When unsure, ask the user: "should I remember this?"

### Step 6 — Keep the index fresh

After any write, update `INDEX.md` so every note is listed with a current
one-line summary. A stale index makes the brain hard to navigate.

## Note conventions

- **Atomic** — one topic per note. Split overgrown notes.
- **Linked** — every note links to `[[INDEX]]` and to related notes. INDEX
  links to every note. This keeps Obsidian's graph navigable.
- **Frontmatter** — YAML with `tags`, `created`, `updated`. Update `updated`
  on every edit. Decisions carry a `date`.
- **Tags** — `#twest/self`, `#twest/decision`, `#twest/project`, etc.
- **Wikilinks** — use `[[note-name]]` (Obsidian resolves them across folders).
- **Human-readable** — write for the user too, not just for the agent. Use
  their vocabulary. This is their second brain.

## Security

- NEVER store secrets, API keys, tokens, or credentials in the vault.
- If the user shares a secret mid-task, keep it out of twsta and say so.
- Vault content is plaintext markdown — treat it as non-secret.