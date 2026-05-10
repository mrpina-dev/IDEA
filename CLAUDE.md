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
