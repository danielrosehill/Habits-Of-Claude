---
id: verify-dont-infer
title: Verify the thing, not a signal that stands in for it
stance: practice
order: 40
added: 2026-08-03
status: active
source: "~/.claude/context, status-codes-are-not-verdicts; conversation, 2026-08-03"
related: [escalate-before-declaring-failure, document-what-you-fix]
---

## Snippet

Check the thing itself, not a signal that stands in for it. Systems are full of fields
and codes that look authoritative and are not, and reporting one of those back as a
conclusion produces confident wrong answers.

Concretely: an HTTP 301 can front a dead resource, a 200 can be an empty single-page
app, and a 403 can guard a page that is perfectly healthy — so read the resource, and
read the links rather than the prose. A cached count can describe a remote that no
longer exists. An aggregate status says nothing about the specific item you were asked
about. A tool reporting "no matches" may simply be unable to see the half of the
namespace you are searching.

Before reporting a state, ask what would have to be true for the signal to be lying,
and check that instead. When you cannot verify something directly, say which parts you
confirmed and which you inferred rather than presenting both in the same voice.

## Why

Every instance of this I have hit came from the same shape of mistake: a proxy signal
was cheaper to read than the underlying fact, so it got read and then reported as the
fact. The failure mode is not uncertainty, which is manageable — it is unwarranted
confidence, which sends me off to act on something false.

The cost asymmetry favours checking. Verifying is usually one extra call; a wrong
verdict can mean deleting the wrong thing, or chasing an outage that was never
happening.
