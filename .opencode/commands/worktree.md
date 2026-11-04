---
description: Create a git worktree under .worktrees/
---

Create a git worktree. Raw argument: $ARGUMENTS

Steps:

1. Sanitize the raw argument into a single valid path segment:
   - trim whitespace, lowercase
   - replace spaces and underscores with hyphens
   - drop any character outside `[a-z0-9-]`
   - collapse repeated hyphens
2. Run exactly one shell command in the current working directory:

   `git worktree add .worktrees/<sanitized-name>`

Do nothing else. Do not change directory, do not move the session, do not open the new worktree, do not edit files, do not run any other git command.
