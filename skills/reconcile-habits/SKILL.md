---
name: reconcile-habits
description: Compare a system prompt file against the Habits-Of-Claude repo and resolve the drift in both directions — prose in ~/CLAUDE.md that should become a habit file, habit files whose installed copy is stale, and hand-written sections now duplicated by the managed block. Produces a reconciliation report and applies only the resolutions the user approves. Use when the habits and the system prompt have diverged, after editing CLAUDE.md by hand, or before trusting the repo as the source of truth.
---

# Reconcile a system prompt against the habits

The repo is meant to be the source of truth, but `~/CLAUDE.md` gets edited in place
mid-session — so the two drift. This resolves that. It is read-and-report first;
nothing is rewritten before the user picks.

## Establish the three buckets

Read the target (default `~/CLAUDE.md`) and `habits/*.md`, then sort every difference
into one of three kinds. Do not proceed to changes until all three are enumerated.

**1. Prose in the prompt with no habit file.** A directive the user wrote by hand that
meets the bar for a habit — a principle that holds across all work, not a fact about
this machine. This is the most valuable bucket, because it is where the user's real
intent is, expressed before anyone tried to systematise it. Propose an `add-habit`
for each, quoting the existing wording.

Apply the repo's own exclusion test: if it depends on this setup, it is environment
configuration and stays in `~/CLAUDE.md`. Which MCP server fronts which tool, what a
hostname refers to, that Python uses `uv` — none of those are habits. Do not drag
them in to make the repo look complete.

**2. Habit files whose installed copy is stale.** The managed block was generated from
an older revision. Mechanical: regenerate and reinstall.

**3. Hand-written prose duplicated by the managed block.** The same instruction now
appears twice, once in the user's words and once generated. Both copies being present
is worse than either alone, because they will diverge and the agent gets two subtly
different rules.

## Resolving bucket 3

Compare wording before deciding, and prefer the user's original where it is sharper.
Frequently the hand-written version has a specificity the generated one lost — a
concrete example, a blunter phrasing — in which case the fix is to update the habit
file to match, regenerate, then delete the hand-written section. Losing the user's
phrasing to a blander paraphrase is a real regression; check for it explicitly.

Never delete a hand-written section without showing the user the exact text being
removed and what replaces it.

## Report format

One table, one row per difference: bucket, subject, and the proposed resolution. Then
wait. Apply approved items in this order — edit habit files, `assemble.py`,
`install.py --write`, then remove superseded hand-written sections — so the target is
never briefly missing an instruction it had before.

## Verifying

After applying, re-run the comparison and confirm the three buckets are empty. Then
`git diff` in the repo and commit the habit changes; the installed block is a build
artefact of that commit, not a separate change to explain.

`~/CLAUDE.md` may itself be a checkout that syncs across machines — check before
assuming an edit there is local-only, and commit it if so.
