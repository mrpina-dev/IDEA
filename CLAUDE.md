# Claude Code Instructions

## Behavior
- Make all requested changes without asking for clarification unless the request is genuinely ambiguous.
- After every change, immediately stage, commit, and push without waiting to be told.
- Never ask permission to commit or push. Just do it.
- Use "Yes, allow all edits during this session" (option 2) behavior by default.

## Commit Messages
- Keep them short and descriptive. One line.
- Format: `update: what changed` or `add: what was added` or `fix: what was fixed`
- No co-author lines, no verbose descriptions.

## Git Workflow
After every file change:
```bash
git add -A
git commit -m "descriptive message here"
git push
```

## Repo Context
- This is a GitHub Pages site at mrpina-dev.github.io/IDEA
- Main file is index.html in the repo root
- All changes go to the main branch
- No build step required - changes are live after push

## DESIGN_DIRECTION.md maintenance

DESIGN_DIRECTION.md at the repo root is the design north star. When a prompt
includes edits to it, apply them as routine surgical changes (no confirmation
needed, same as code edits). Never rewrite the file wholesale. Never delete
entries from "Standing Rejections" unless the prompt explicitly says to.

## Update log (CHANGELOG) maintenance

The CHANGELOG array in vanguard/index.html powers the in-game UPDATE LOG and must
stay current. When a prompt ships a change players will notice (new weapon, mechanic,
mode, a balance pass players will feel, or a visible UX change), it will normally
include a CHANGELOG edit. If such a change ships without one, prepend or extend the
top CHANGELOG entry for the current VERSION yourself in the same commit, one concise
player-facing bullet per change. Pure internals (dev tools, telemetry plumbing,
refactors, version-string changes) need no entry. Never rewrite the whole array;
only prepend a new top entry or amend the existing top one.
