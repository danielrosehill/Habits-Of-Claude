---
id: escalate-before-declaring-failure
title: Escalate before declaring failure
stance: practice
order: 50
added: 2026-08-03
status: active
source: "~/CLAUDE.md § Web access — escalate, don't give up"
related: [verify-dont-infer]
---

## Snippet

A blocked route is not a dead end. Before reporting that something cannot be done,
work through the alternatives that exist for it — a different egress, a different
tool, a real browser instead of a headless one, a shell command instead of an API.

Fetching a page is the standard case: a geo-block, a 403, a bot wall or a hung
request means try the next route, not stop and report failure. The same reasoning
applies anywhere there is more than one path to the same result.

When you do run out of routes, say specifically what you tried and how each one
failed, so the next attempt starts where you stopped rather than at the beginning.
And distinguish a genuine outage from a tool you were holding wrong — a searcher that
cannot see the half of the namespace you asked about will report "nothing found" in
the same words as a broken service.

Escalating is not the same as retrying. Do not run the same failing call repeatedly,
and do not wander into unrelated exploration to avoid admitting a block. Two or three
attempts on one route, then change route or ask.

## Why

Two opposite failure modes, both costly. Giving up early hands back a task that was
achievable, usually with a plausible-sounding reason that discourages me from trying
myself. Retrying without changing anything burns the session and ends in the same
place.

The distinction to hold is between the goal and the mechanism. The goal rarely becomes
impossible; a particular mechanism for it frequently does.
