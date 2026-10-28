---
name: finishing-a-development-branch
description: Use when implementation is complete and tests pass, to wrap up the branch. Never merges or deploys. Pushes or opens a PR only when the user picks that option. If the project has its own PR or shipping skill, use that one instead.
---

# Finishing a Development Branch

**Project skill first:** if the current project has its own skill for this, use that one instead of this skill.

**Git rules:** commit only to the branch you're on. Never push unless the user asks in this conversation. Never merge, rebase or commit into any other branch (including main/master), and never deploy.

## Overview

Verify tests, then let the user decide what happens to the branch.

**Announce at start:** "I'm using the finishing-a-development-branch skill to complete this work."

## The Process

### Step 1: Verify Tests

Run the project's test suite, using the command the project documents (CLAUDE.md, README, bin/ scripts). Common defaults:

```bash
bundle exec rspec       # RSpec
bin/rails test          # Rails with Minitest
# npm test / cargo test / pytest / go test ./...  (other project types)
```

**If tests fail:** show the failures and stop. Don't offer to push or open a PR.

### Step 2: Commit Remaining Work

If there are uncommitted changes from this work, commit them to the current branch. Never switch branches to do it.

### Step 3: Present Options

```
Implementation complete and committed on <branch>. What would you like to do?

1. Keep the branch as-is (I'll handle it)
2. Push and open a pull request

Which option?
```

Don't add explanation. Don't offer to merge.

### Step 4: Execute Choice

#### Option 1: Keep As-Is

Report: "Keeping branch <name>." If it's in a worktree, report the path and leave the worktree in place.

#### Option 2: Push and Open a PR

Choosing this option is the user asking to push. Push only the current branch.

```bash
git push -u origin <current-branch>
gh pr create --title "<title>" --body "<summary and test plan>"
```

Follow the project's PR template and title conventions if it has them. Leave the worktree in place, since review may need more changes.

## Red Flags

**Never:**
- Merge into main/master or any other branch
- Push without the user choosing it
- Force-push
- Deploy, or apply deploy labels
- Delete a branch or worktree without the user asking

## Integration

**Called by:**
- **subagent-driven-development** - After all tasks complete
- **executing-plans** - After all tasks complete

**Pairs with:**
- **using-git-worktrees** - The user removes the worktree when they're done with it
