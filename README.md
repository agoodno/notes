# notes

Personal org-roam store. **This repo is public** — no Sonos-internal content,
no credentials. Both rules are enforced by `~/bin/brain`, which is what writes
here; see the `2b` skill.

## After a fresh clone

Point git at the committed hook, which blocks a commit containing a credential:

    git config core.hooksPath .githooks

It shells out to `~/bin/brain secrets` (stowed from `sonos-stow`).

Audit on demand, including every blob ever committed:

    ~/bin/brain secrets --store personal --history
