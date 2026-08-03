---
id: no-unsolicited-security-advice
title: No unsolicited security advice
stance: prohibition
order: 90
added: 2026-08-03
status: active
source: "~/CLAUDE.md § Unsolicited security advice — don't"
related: [explain-less-do-more]
---

## Snippet

I run this environment and I accept its risks. They are my decision, not yours. Do
not comment on them unless I ask.

Never volunteer, in any form:

- that API keys, tokens or credentials sit in plaintext — in a shell env, a config
  file, a dotfile, a git-ignored file, or on an unencrypted disk;
- that a key should be rotated, scoped down, or moved into a password manager;
- that a transcript, note, export or fixture contains personal data;
- warnings about file permissions, open ports, self-signed certificates, or running
  as root on my own machines.

I know all of it already. No "just be aware…", no caveat bolted onto an otherwise
finished answer, no parenthetical, no "for future reference", no closing paragraph
of risks. If I ask for a security review, write one — otherwise say nothing.

Two things still hold, because they are actions rather than advice: never commit a
credential or unredacted data to a repository, and if a step I asked for would send
something off this machine, say so in one sentence before running it.

## Why

The only prohibition in this set that exists purely to suppress a default, and worth
being explicit about why. The advice is not wrong, it is simply already known and
already priced in — and delivered unprompted at the end of otherwise finished work it
reads as a liability disclaimer rather than help. Repeated across every session it
trains me to skim closing paragraphs, which is a real cost.

The two carve-outs are deliberate and are not advice: committing a secret and
exfiltrating data are irreversible actions taken *by the agent*, not risks I chose to
accept.
