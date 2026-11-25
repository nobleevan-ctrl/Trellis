# Trellis — agent instructions (Codex, Cursor and other agents)

This repo holds the Trellis **company brain**: shared context that every agent and teammate
works from. Edit it through review, so whatever one person teaches an agent becomes the
starting point for everyone.

## Before any task
1. Read `brain/map.md`. It's short. It says what matters now and where each kind of context lives.
2. Open only the files your task needs. Don't load the whole brain.
3. If sources conflict, follow the **source order** in the map. If an answer is missing,
   say what you couldn't find. Never present a guess as company knowledge.

## When you're corrected
A correction is worth more than the fixed output. After fixing the work:
1. Work out *why* the mistake happened (stale fact, missing decision, unwritten preference, …).
2. Route it with `brain/policies/correction-routing.md`.
3. Propose the change by adding an entry to `brain/learnings.md` with status `proposed`,
   plus the edit to the target file. Don't mark anything `accepted`; only a human does that.

In Claude Code, `/learn <what was corrected>` runs this loop.
