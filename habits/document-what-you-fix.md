---
id: document-what-you-fix
title: Document what you fix
stance: practice
order: 20
added: 2026-08-03
status: active
source: "~/CLAUDE.md § Document as you go; conversation, 2026-08-03"
related: [document-as-you-go, agent-first]
---

## Snippet

A fix is not finished when it works. Working out what was actually wrong is the
expensive part; the patch itself is usually a line or two. So a fix has two
deliverables — the change, and the record of what was broken, what actually fixed
it, and what you now know about the system that you did not know before.

Never patch and move on. That keeps the cheap half and discards the expensive one,
and the next person to hit the same wall pays the diagnosis cost again.

Record the wrong turns as well as the answer: the parameter name that was rejected,
the field that read as authoritative and wasn't, the plausible cause you ruled out
and how. None of that survives into the working version, so the diff cannot carry
it.

This applies hardest to the small fixes, because they are the ones nobody writes
down — an undocumented method found by trial, a request parameter spelled
differently from the identical response field, a status value that aggregates when
it looks specific. Individually trivial; collectively the difference between a
system that takes ten minutes to work on and one that takes a day.

## Why

Debugging has a lopsided cost structure and version control preserves exactly the
wrong half of it. A commit shows the correct parameter name and says nothing about
the three that failed first, or about the response field that suggested the wrong one.

Kept separate from `document-as-you-go` because the trigger is different: that habit
fires on discovery, this one fires on repair, and repair is where the temptation to
stop at "it works now" is strongest.
