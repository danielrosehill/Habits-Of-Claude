---
id: document-as-you-go
title: Document as you go
stance: practice
order: 10
added: 2026-08-03
status: active
source: "~/CLAUDE.md § Document as you go"
related: [document-what-you-fix, agent-first, one-subject-one-repo]
---

## Snippet

While doing a task you will learn things the task did not ask you to learn — how a
platform's undocumented API is really shaped, what an auth flow actually requires,
the sequence of steps that worked after several that did not. Treat that knowledge
as an output of the work, not a byproduct, and capture it **without being asked**.

Something is worth keeping if you had to reverse-engineer it, if the official docs
are absent or wrong, or if next time you would have to rediscover it the same way.

Place it by reach. Useful beyond this task, about a system that will recur: a
dedicated repo for that subject — add to it if one exists, propose creating one if
not. Useful only within this project: `docs/` in the current repo, written without
asking. Useful only right now: say it in your reply and put nothing on disk.

Write it so it is usable cold: concrete endpoints, field names and response shapes,
identifiers redacted and credentials referenced rather than pasted, what you tried
that failed, the absolute date you verified it, and which parts you confirmed versus
inferred.

Separately from discovered knowledge, documentation of a code change ships in the
same commit as the change: the decision and the constraint that settled it,
non-obvious constraints, workarounds with a removal condition, new config and
commands. Fix any statement your change made untrue.

Capture never substitutes for the task and is never a reason to leave it unfinished
— but do it before reporting completion. Do not restate the diff, and do not create
session artifacts: no `SUMMARY.md`, no `IMPLEMENTATION_NOTES.md`, no dated work
logs. Update the existing document rather than starting a parallel one. Writing
nothing is the right outcome more often than not.

Long-form treatment, with a slash command for sweeping a session that got away:
<https://github.com/danielrosehill/Document-As-You-Go>

## Why

The expensive part of most work is not the change, it is establishing the facts that
made the change possible — and those evaporate at the end of a session unless
someone writes them down. Left uncaptured, the same platform gets reverse-engineered
from scratch every few months.

The same-commit clause is here rather than in its own habit because the trigger is
identical — knowledge that exists only in your head at the moment the work lands.
Only the destination differs: a discovered fact goes to a repo that owns the subject,
a decision about the code goes next to the code.
