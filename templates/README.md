# Templates

Reference copies of `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`,
`PULL_REQUEST_TEMPLATE.md`, and `ISSUE_TEMPLATE/` for RedDuck repos.

**These are not applied automatically.** GitHub's org-wide default community
health files only activate from specific locations in this repo — its root,
a `.github/` folder, or a `docs/` folder. Deliberately keeping these files
under `templates/` instead means they never auto-apply to any repo, public
or private.

That's on purpose: GitHub's fallback mechanism doesn't distinguish public
from private repos — it's all-or-nothing across the whole org. Since we
want these on public repos only, they're copy-paste reference files, same
model as
[error-handling-best-practices](https://github.com/RedDuckTeam/error-handling-best-practices):
copy what you need into a public repo's root (and `ISSUE_TEMPLATE/` into
that repo's own `.github/ISSUE_TEMPLATE/`), don't rely on inheritance.

## When a repo goes public

Copy in whichever of these it doesn't already have its own version of:

```
templates/CONTRIBUTING.md              → <repo>/CONTRIBUTING.md
templates/SECURITY.md                  → <repo>/SECURITY.md
templates/CODE_OF_CONDUCT.md           → <repo>/CODE_OF_CONDUCT.md
templates/PULL_REQUEST_TEMPLATE.md     → <repo>/PULL_REQUEST_TEMPLATE.md
templates/ISSUE_TEMPLATE/*             → <repo>/.github/ISSUE_TEMPLATE/*
```

Or run `./sync.sh` from this directory — it copies these into the public
repos listed at the top of the script (edit that list to add/remove repos)
and opens a PR in each. It uses your already-authenticated `gh` CLI, so it
needs no separate token or repo secret; it just needs those repos cloned as
sibling folders next to this one.
