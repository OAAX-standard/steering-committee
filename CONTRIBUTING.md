# Contributing

## Meeting notes

1. Copy [`meeting-notes/TEMPLATE.md`](meeting-notes/TEMPLATE.md) to `meeting-notes/YYYY/YYYYMMDD.md`.
2. Fill it in during/after the meeting and delete the template's leading comment.
3. The moderator opens a PR with just this file and merges it within 48 hours. Merged notes are
   corrected by a new PR, never rewritten.

## Roadmap changes

1. Propose the change as an issue labelled `tsc-agenda`, describing the change and its
   compatibility impact.
2. It's decided in a TSC meeting and recorded in that meeting's notes (see above).
3. Once the notes are merged, open a separate PR updating
   [`roadmap/README.md`](roadmap/README.md), linking the PR description to the meeting notes
   that decided it.

Keeping the roadmap PR separate from the notes PR keeps notes an immutable record and roadmap
diffs easy to review on their own.
