---
name: implement
description: "Implement an Issue end to end in an isolated worktree, verify it, review it, and prepare an approved pull request."
disable-model-invocation: true
---

Implement all work described by the user's spec, Issue, or agreed conversation plan.

## Establish the delivery line

Before editing:

1. Read repository instructions, `~/.omp/agent/GIT-WORKFLOW.md` when it exists, the implementation Issue or spec, its prerequisites, and relevant open pull requests.
2. Inspect the remote default branch, current branch, all worktrees, uncommitted changes, and branch ancestry.
3. Follow the repository's documented workflow when present. Otherwise:
   - Feature work starts from an updated `develop` and targets `develop`.
   - Release work starts from `develop` and targets `main`.
   - Hotfix work starts from the affected release tag and targets `main`.
4. Use one Issue = one branch = one dedicated worktree. The worktree folder and branch must name the same Issue.
5. Preserve user changes. If a worktree is dirty, create a separate worktree instead of switching it.
6. Print exactly one status line before edits:

```text
Worktree: <path> | Branch: <branch> | Base: <commit/branch> | PR target: <branch>
```

Proceed without asking when repository evidence determines the local branch, worktree, base, and PR target. Ask only when materially different valid targets remain.

Completion criterion: the dedicated worktree, branch, base, and PR target are correct and contain no unrelated work.

## Implement and verify

Use /tdd where possible, at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite once at the end. Verify the changed behavior on its real runtime surface. Capture final evidence from the production/runtime path, never from mocks or placeholders.

Once implementation verification passes, review the working tree against the planned base on separate Standards and Spec axes. Use /code-review when it can inspect the diff. If it only sees committed changes, run the same two axes directly over `git diff <base>` plus untracked files. Resolve every valid finding and re-verify affected behavior.

Completion criterion: every acceptance criterion has fresh evidence; final review has no unresolved finding.

## Prepare the commit and pull request

1. Verify the head, base, merge-base, proposed commits, and diff contain only this Issue.
2. Read `~/.omp/agent/PR-STANDARD.md` when it exists before drafting or updating the pull request.
3. Prepare the proposed commit messages, push target, pull-request base, title, body, and evidence plan.
4. Request explicit user approval for the commit, push, evidence uploads, and pull-request creation.
5. After approval, perform only the approved commit, push, evidence upload, and pull-request operations.
6. Create a ready-for-review pull request to the approved target unless the user explicitly requests a draft.
7. Never merge the pull request; the user owns merging.

Completion criterion: the pushed commit and pull request reference the Issue, follow the applicable PR standard, include visible evidence, and contain no prerequisite or unrelated changes. Without approval, stop after preparing the proposed commit and pull request and report the approval blocker.

Report only: outcome, verification, commit, PR URL, and blockers.
