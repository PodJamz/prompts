---
name: git-workflow
description: Git branch management, PR workflow, and the verification discipline that makes autonomous merging safe. USE WHEN creating branches, opening PRs, merging, cleaning up worktrees, or coordinating parallel agents on one repo.
---

# Git Workflow

Branching and PR mechanics are table stakes; the real value is the verification discipline at the bottom. That is what lets an agent merge autonomously without ever lying about what landed where.

## Branching

- Always branch FROM main, and open PRs with `--base main` explicitly. "MERGED" can mean merged into another feature branch; being explicit prevents the whole class.
- Naming: `feat/description`, `fix/description`, `docs/description`, `refactor/area`, `hotfix/critical-issue`.
- Short-lived (1-7 days), single-focus, deleted after merge.
- Commit format: `type(scope): brief description`. Types: feat, fix, docs, style, refactor, test, chore.
- Never push directly to main without a PR; never push untested code (build and test locally first).

## Pull requests

- Every PR references the issue it closes (`Closes #N`).
- Description: summary, changes made, testing done, breaking changes. Screenshots for UI.
- Keep PRs focused and reviewable (roughly under 500 lines); if a change is bigger, it is probably several PRs.
- Squash-merge feature branches for clean history.
- Close issues with evidence: commit hash, PR number, validation URL.

## Worktrees (parallel work)

- Worktrees are for WRITING, never for shipping: build and test in the worktree, but the PR merges to main and the canonical checkout is what runs in production. In-repo guards cannot protect a worktree that ships directly.
- Remove each worktree after its branch merges. A worktree with no purpose is sprawl (see the wayfinding skill: bind worktrees to tickets).
- Never auto-delete a worktree that might hold uncommitted unique work. Visibility first; deletion is a human decision.
- Never `git stash drop` or `git stash clear` autonomously.

## Parallel agents on one repo

- **One writer per shared file per wave.** Name the owned files in each agent's brief ("you are the ONLY server.py writer this wave"). Additive agents expose a public seam (initializer, closure) and one integrator wires the seams afterward. This is the difference between merge hell and zero collisions across six parallel PRs.
- If two agents both need one file, resequence (one lands first) or split the file's regions explicitly. Never hope git merges it.

## The verification discipline (non-negotiable)

1. **Ancestry-verify every merge.** MERGED status is not proof of destination:

   ```bash
   git merge-base --is-ancestor <mergeCommit> origin/main && echo "actually on main"
   ```

2. **Built is not merged, merged is not deployed, deployed is not reachable.** Claim each stage only with its own evidence: test output for built, the ancestry check for merged, a live health check or HTTP 200 for deployed and reachable.
3. **After hand-resolving any merge conflict, grep the whole file (better: the whole repo) for stray conflict markers** (`<<<<<<<`, `>>>>>>>`) before continuing. Then run the full suite on the merged result, not on the branches.
4. **Run tests on the merged HEAD** before calling work done; green on the branch tip proves nothing about the union.
5. **Check the PR's current state before any follow-up push** to it; the world may have moved.

## Checklist for an autonomous merge train

- [ ] Each PR mergeable and its base explicitly main
- [ ] Merge order respects stacked branches and shared-file conflicts (conflicting PRs: merge one, update-branch the other, hand-resolve, re-test)
- [ ] Every merge ancestry-verified
- [ ] Full test suite green on the final merged main
- [ ] Canonical checkouts pulled, services restarted only with evidence they need it
- [ ] Worktrees for the wave removed, branches deleted
