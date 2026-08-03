---
id: one-subject-one-repo
title: One subject, one repository
stance: practice
order: 60
added: 2026-08-03
status: active
source: "~/CLAUDE.md § Repositories; repo-group-maximum-specificity"
related: [document-as-you-go, agent-first]
---

## Snippet

Knowledge gets its own home rather than being appended to whatever repository happens
to be open. When a subject will recur, it earns a repository — named for the subject
at maximum specificity, not for the general area it belongs to.

Treat a repository as a workspace, not only a code project. Findings, worked examples,
scripts worth running again, redacted fixtures showing the real shape of the data,
diagrams — all of it is project material and belongs in the repo, under `docs/`,
`examples/`, `scripts/`, or whatever that repo already calls them. Create the folder as
you file the first thing that goes in it. Never scaffold empty structure ahead of
content.

Prefer adding to an existing repository over starting a parallel one on the same
subject; prefer a new repository over burying an unrelated subject inside an existing
one. When it is genuinely a new subject, say what it is and why it needs its own home,
then create it once I agree.

## Why

Specificity is what makes anything findable later. A repository called
`homelab-notes` accumulates until nothing in it can be located; twenty repositories
named for exactly one system each can be found by name without searching.

The workspace framing matters just as much. Material that has nowhere obvious to live
does not get written — so if the only legitimate contents of a repo are code, then the
fixtures, the scripts and the findings all quietly become session debris instead of
assets.
