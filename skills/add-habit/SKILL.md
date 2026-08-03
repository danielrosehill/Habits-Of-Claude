---
name: add-habit
description: Add a new habit to Habits-Of-Claude, or revise or retire an existing one — writes habits/<id>.md with correct frontmatter, snippet and rationale, then regenerates the assembled output. Use when the user states a standing principle they want to hold across all work, corrects the agent in a way that should persist, or asks to change or drop a habit.
---

# Add or revise a habit

## Qualify it first

A habit is a principle that should be in force before the task is known, in any
repository, on any machine. Three things it is not:

- **Environment configuration** — which server fronts a tool, what a hostname means,
  which package manager this machine uses. Belongs in `~/CLAUDE.md`.
- **A workflow** — an ordered procedure for a specific job. Belongs in a skill.
- **A one-off correction** — a preference about the task at hand, not about all work.

The test in the repo README: if it would still be true working on someone else's
machine, on an unfamiliar codebase, it is a habit.

If what the user said is close to an existing habit, revise that file rather than
adding a ninth near-duplicate. Two habits that overlap will eventually contradict.

## Write the file

`habits/<id>.md`, where `<id>` matches the filename exactly — `assemble.py` enforces
this. Imperative slug, no numbering in the name; order is a frontmatter field.

```markdown
---
id: <slug>
title: <short imperative title>
stance: practice | prohibition
order: <multiple of 10, leaving gaps>
added: <absolute date, YYYY-MM-DD>
status: active
source: "where this came from — a CLAUDE.md section, or a conversation with its date"
related: [<other habit ids>]
---

## Snippet

## Why
```

`## Snippet` is addressed to the agent in the second person and is what lands in a
system prompt — so it must stand alone, with no reference to this repo, to "the user's
preference", or to the conversation it came from. Write the rule and what it means in
practice, not the argument for it.

`## Why` is the argument, addressed to the user, and is excluded from the assembled
output. Put the reasoning and the cost of getting it wrong here. It is what makes the
habit revisable in a year instead of merely inherited — a habit whose rationale is
lost cannot be judged, only obeyed.

State the exception explicitly where one exists. A prohibition with no carve-out gets
over-applied: `ship-without-asking` had to say that deletion and outward-facing
actions are excluded, or it would read as licence to push anything anywhere.

`order`: practices before prohibitions, documentation habits first. Use multiples of
ten so a habit can be inserted later without renumbering.

## Then regenerate

```bash
python3 scripts/assemble.py
```

This validates frontmatter, that `id` matches the filename, that `stance` is one of
the two allowed values, and that every `related` id resolves. Fix what it reports —
it exits non-zero rather than emitting a broken build.

Commit the habit file and the regenerated `assembled/` together. Installing into
`~/CLAUDE.md` is a separate step: use `install-habits`.

## Retiring one

Set `status: retired` and leave the file in place rather than deleting it — the
rationale is the useful part and a retired habit records a position that was
considered and dropped. Note in `## Why` what changed. Retired habits are still
assembled today; if that becomes unwanted, filter on `status` in `assemble.py` rather
than deleting history.
