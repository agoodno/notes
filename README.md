# notes

Personal org-roam store. **This repo is public** — no Sonos-internal content,
no credentials. Both rules are enforced by `~/bin/brain`, which is what writes
here; see the `2b` skill.

## After a fresh clone

Point git at the committed hooks:

    git config core.hooksPath .githooks

- `pre-commit` blocks a commit containing a credential. It shells out to
  `~/bin/brain secrets` (stowed from `sonos-stow`).
- `pre-push` rescans every blob the push would newly publish, including ones
  a later commit deleted -- `--no-verify`, an amend, or a rebase can get a
  credential past `pre-commit`, and a pushed blob is not retractable.
- `post-commit` pushes to origin in the background, so the notes survive
  losing the laptop. Failures land in `$TMPDIR/notes-autopush.log`, including
  a `pre-push` refusal; the next commit retries.

Audit on demand, including every blob ever committed:

    ~/bin/brain secrets --store personal --history
