## What it does

`implement` turns a decided [Issue](https://www.aihero.dev/ai-coding-dictionary/ticket), spec, or conversation plan into a verified pull request. It establishes the delivery line first: base, branch, dedicated worktree, and PR target. Then it builds the change, drives [tdd](https://aihero.dev/skills-tdd) at agreed seams, verifies the real runtime surface, and reviews the working tree on separate Standards and Spec axes.

The skill prepares the commit, push, evidence upload, and pull request, then stops for explicit approval. It performs only the operations the user approves. It never merges the pull request.

## When to reach for it

Invoke `/implement` yourself after the work has been decided. The agent cannot invoke it implicitly.

| The work is | Reach for |
| --- | --- |
| One tracked Issue | `/implement <Issue URL>` |
| A small spec | `/implement <spec path>` |
| A small plan settled in the current conversation | `/implement`, stating that the thread is the source |
| A larger spec spanning several Issues | [to-tickets](https://aihero.dev/skills-to-tickets), then one fresh `/implement` session per Issue |
| Still unclear or disputed | [grill-with-docs](https://aihero.dev/skills-grill-with-docs) |
| Already built and only needs review | [code-review](https://aihero.dev/skills-code-review) |

One invocation owns one Issue, one branch, and one dedicated worktree. It follows the repository's documented branch workflow. When the repository has no workflow, it uses the user's global Git workflow when available.

The worktree is chosen from repository evidence. A dirty worktree is never reused or switched; the skill creates a separate worktree so user changes remain untouched.

## Common questions

**Does it commit or push automatically?**

No. After implementation and review, it shows the proposed commit messages, push target, PR base, title, body, and evidence plan. Commit, push, evidence upload, and PR creation require explicit user approval.

**Does invoking `/implement` count as approval for Git operations?**

No. Invoking the skill approves local implementation and verification. Remote or history-changing operations still require a separate, explicit approval naming those operations.

**Does it merge the pull request?**

No. The user owns merging.

**What happens when `/code-review` cannot see uncommitted work?**

The skill reviews the working tree directly against the planned base using the same separate Standards and Spec axes, including untracked files. It resolves every valid finding before requesting commit approval.

**Can several Issues run in parallel?**

Each Issue needs a separate branch and worktree. Parallel sessions must not share a working directory, index, or HEAD. The skill itself completes one Issue at a time.

**What if the repository uses a different Git flow?**

Repository instructions win. The global workflow is only a fallback.

## It's working if

- The first status line names the worktree, branch, base, and PR target.
- The worktree contains only the selected Issue and preserves unrelated user changes.
- Tests observe agreed seams and the real runtime surface.
- Typecheck, focused tests, the full suite, and the final two-axis review have fresh evidence.
- The agent presents exact commit, push, evidence, and PR operations before asking for approval.
- No commit, push, PR, merge, tag, release, or deletion occurs outside the approved scope.
