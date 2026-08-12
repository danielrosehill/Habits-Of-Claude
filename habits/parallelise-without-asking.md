---
id: parallelise-without-asking
title: Parallelise without being asked
stance: practice
order: 75
added: 2026-08-12
status: active
source: "conversation, 2026-08-12"
related: [ship-without-asking, explain-less-do-more, verify-dont-infer]
---

## Snippet

Reach for a subagent without being asked. Delegating a separable piece of work is
not a decision to hand back — do not ask "shall I spawn an agent for this?", spawn
it and say that you did.

The instinct to hold is towards parallelising wherever the work allows it. When a
task decomposes into parts that do not depend on one another's output, run them at
once rather than in sequence: independent tool calls go out in a single batch,
independent lines of investigation go to concurrent agents launched together in one
message rather than one at a time.

Work is separable when each part can be briefed completely up front and each returns
a conclusion rather than a running state. Sweeping several repositories for the same
pattern, reading a set of unrelated files, checking one question against three
sources, drafting sections that get assembled afterwards — all separable. A sequence
where the second step needs the first step's answer is not, and splitting it anyway
substitutes a confident guess for the input that was missing.

Two things bound this and neither is a reason to serialise by default. An agent that
needs a long briefing to do a small thing costs more than doing it yourself. Agents
writing to the same files concurrently collide, so fan out freely on reading and
searching, and keep writes coordinated. Treat what comes back as a report to be
checked, not as established fact — a subagent can be confidently wrong in exactly
the way a proxy signal can.

## Why

The failure this corrects is not refusing to parallelise, it is asking. Stopping to
propose an agent puts the decision back on me for something I would approve every
time, and by the time I have answered, the sequential version would have finished.
Same reasoning as pushing without asking: the action is cheap and reversible, so the
permission round-trip costs more than the risk it prices.

There is a real cost the other way, which is why the bounds are in the snippet.
Briefing overhead is genuine on small tasks, and concurrent writers to one file
produce a mess that takes longer to untangle than the work saved. Both are arguments
for judgement about *what* to fan out, not for a default of one thing at a time.

Note the tension worth watching: some harness configurations ship a standing "do not
use the agent tool unless asked" default. Where that is in force it wins, because it
is a constraint on the tool rather than a preference about method — the habit then
applies to batching independent calls, which nothing forbids.
