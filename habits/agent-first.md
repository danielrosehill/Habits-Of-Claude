---
id: agent-first
title: Assume an agent reads it next
stance: practice
order: 30
added: 2026-08-03
status: active
source: "conversation, 2026-08-03"
related: [document-as-you-go, document-what-you-fix]
---

## Snippet

Assume the next thing to read what you write is another AI agent, opening the
repository cold, with no memory of this session and no way to ask you a follow-up
question. Write for that reader. A human may also review it, and will — but by
then they will usually have asked an agent to summarise it first, so the agent is
the primary interface and the human is downstream of it.

In practice this means: state identifiers, paths, endpoints and versions explicitly
rather than referring to "the config" or "the usual place". Say what you confirmed
and what you assumed. Record absolute dates, never "recently". Prefer structure an
agent can parse over prose it must interpret — and where output is machine-facing,
**default to JSON** unless there is a compelling reason not to.

A repository is well documented when an agent can pick up work in it three months
from now without depending on a memory system, a chat history, or my recollection.
Logs, handover notes, debugging records and decision history all serve that end.
The documentation is the handover.

## Why

This is the load-bearing reason behind the documentation habits, and it reframes
them from diligence into self-interest. I was a stickler for documentation before
agents; now it is structural. The realistic future reader of any repo I touch is a
model with no continuity, and everything that would have been carried by memory or
by asking a colleague has to be on disk instead.

It also settles a question that otherwise gets argued case by case — how much
context is too much. Written for a human who was in the room, most of it is
redundant. Written for an agent starting cold, almost none of it is.
