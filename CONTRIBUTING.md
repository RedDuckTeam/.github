# Contributing

Thanks for helping build RedDuck's work. This is the org-wide default and
applies to any RedDuckTeam repository without its own `CONTRIBUTING.md` — a
repo's own copy always wins over this one.

## Local setup

The package manager varies by repo (some use `pnpm`, some use `npm`) — check
the repo's `package.json` (`packageManager` field) or its README before
running anything. In general:

```bash
<pnpm|npm> install
cp .env.example .env   # if the repo has one
<pnpm|npm> run dev
```

## Before opening a PR

Run whichever of these scripts exist in the repo — most have all four, some
have a subset:

```bash
<pm> run lint
<pm> run typecheck
<pm> run build
<pm> run test
```

A PR shouldn't be opened with a failing check. If CI is configured for the
repo, it re-runs the same checks — don't rely on CI to catch what you could
catch locally first.

## Git, commits, and PRs

- **Commits are informative.** Not `feat: almost completed` or `fix: stuff`.
  A commit message should say what changed and, where it's not obvious, why.
- **Never commit broken code.** Each commit is a real, working snapshot. If
  you need to push work-in-progress to remote as a backup, push it to its own
  branch — don't land it on the branch others will build on.
- **Split commits reasonably.** Prefer several focused commits
  (`git add -p` is useful here) over one large commit that bundles unrelated
  changes.
- **No dead code, no `old/`, no `archive/`.** Git already keeps full history —
  commented-out code and "just in case" folders don't need to live in the
  tree. Delete it; it's recoverable from history if it's ever actually needed.
- **Merge only when the branch is actually done.** Don't merge early just to
  hand off a partial fix to someone else — use `git cherry-pick` (or just ask)
  instead of merging an unfinished branch into a shared one.
- **Before solving something from scratch, check if it's already been solved.**
  If the task is something the industry (or another RedDuck repo) has already
  built many times over — wallet connection, KYC integration, a common DeFi
  primitive — look at how it's usually done first. Re-deriving a well-trodden
  pattern from zero is rarely the best use of the time.

## Code review

Before requesting review, check your own change against the task/ticket it's
solving and give it a self-review pass — most review cycles that go back and
forth repeatedly are cases where this step got skipped. From there: automated
checks (lint/typecheck/build/test) run first, then a human review. Don't
merge your own PR unless the repo's process explicitly allows it.

## Security-sensitive changes

If your change touches wallet connections, signing, token approvals,
contract interaction, or anything else that could move funds or grant
approvals, see [SECURITY.md](SECURITY.md) before opening the PR.
