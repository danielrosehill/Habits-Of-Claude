[![Claude Code Repos Index](https://img.shields.io/badge/Claude%20Code%20Repos-Index-blue?style=flat-square&logo=github)](https://github.com/danielrosehill/Claude-Code-Repos-Index)

# Habits Of Claude

Standing habits for an AI coding agent, one file per habit, kept as paste-ready
snippets for a user-level system prompt (`~/CLAUDE.md`, `AGENTS.md`).

The unit here is the **habit**: a principle that should hold across every piece of
work, in every repository, public or private, regardless of the task in front of it.
Not a workflow, not a skill, not a tool preference — a disposition that ought to be
in force before the task is known.

## Why one file per habit

A system prompt written as one continuous document gets edited by accretion and is
hard to reason about. Split into habits it becomes maintainable: each has a single
subject, its own history, and can be revised, retired or lifted into another
project's instructions without disturbing the rest. New habits are added as files
rather than as paragraphs wedged into an existing section.

The assembled system-prompt block is generated, never hand-edited:

```bash
python3 scripts/assemble.py      # writes assembled/habits.md and assembled/habits.json
```

`assembled/habits.md` is the block to paste. `assembled/habits.json` is the same content
structured for an agent reading this repository programmatically — see the
`agent-first` habit for why that exists.

## Installing

`~/CLAUDE.md` is a build target, not a place to hand-edit habits. The installer
maintains a marker-delimited region and leaves everything around it alone:

```bash
python3 scripts/install.py                     # dry run — prints the diff
python3 scripts/install.py --write             # backs the target up first
python3 scripts/install.py --only agent-first,verify-dont-infer --target ./CLAUDE.md --write
```

Three skills drive this, in `skills/`:

| Skill | For |
|---|---|
| `install-habits` | Install or update the block — all habits or a named subset |
| `reconcile-habits` | Resolve drift when the prompt and the repo disagree |
| `add-habit` | Add, revise or retire a habit with valid frontmatter |

## The habits

| Habit | Stance | In one line |
|---|---|---|
| [`document-as-you-go`](habits/document-as-you-go.md) | practice | What you learned is an output of the work; capture it unasked |
| [`document-what-you-fix`](habits/document-what-you-fix.md) | practice | A fix is not finished when it works |
| [`agent-first`](habits/agent-first.md) | practice | The next reader is an agent with no memory of this session |
| [`verify-dont-infer`](habits/verify-dont-infer.md) | practice | Check the thing itself, not a signal that stands in for it |
| [`escalate-before-declaring-failure`](habits/escalate-before-declaring-failure.md) | practice | One blocked route is not a dead end |
| [`one-subject-one-repo`](habits/one-subject-one-repo.md) | practice | Knowledge gets its own home, at maximum specificity |
| [`ship-without-asking`](habits/ship-without-asking.md) | practice | Finished means deployed, not committed |
| [`parallelise-without-asking`](habits/parallelise-without-asking.md) | practice | Spawn the agent, don't propose it |
| [`explain-less-do-more`](habits/explain-less-do-more.md) | prohibition | Do the work; instruct only when asked to |
| [`no-unsolicited-security-advice`](habits/no-unsolicited-security-advice.md) | prohibition | My environment, my risk calculus, not yours |

## What does not belong here

Facts about a particular machine or account — which MCP server fronts which tool,
which VM a hostname refers to, that Python environments use `uv` — are environment
configuration, not habits. They change when the environment changes and they mean
nothing in another context. They stay in `~/CLAUDE.md` and `~/.claude/context/`.

The test: if it would still be true working on someone else's machine, on an
unfamiliar codebase, it is a habit. If it depends on this setup, it isn't.

## Relation to Document-As-You-Go

[`Document-As-You-Go`](https://github.com/danielrosehill/Document-As-You-Go) was the
first pass at this idea — the documentation habit developed on its own, with a
slash command for retroactive sweeps. It remains the long-form treatment of the two
documentation habits here, which are deliberately kept short in this repo and defer
to it.

This repo generalises the pattern: the insight was never one instruction, it was
that standing dispositions are the useful unit.

## Layout

```
habits/         One markdown file per habit — frontmatter + snippet + rationale
skills/         Claude Code skills — install, reconcile, add
scripts/        assemble.py builds the output; install.py splices it into a prompt
assembled/      Generated output, committed so it is usable without running anything
```

Each habit file carries `id`, `title`, `stance`, `order`, `added`, `status` and
`source` in frontmatter. `## Snippet` is the text that goes into a system prompt;
`## Why` is context for me and is excluded from the assembled output.

---

For more Claude Code projects, visit my [Claude Code Repos Index](https://github.com/danielrosehill/Claude-Code-Repos-Index).
