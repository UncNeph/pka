# Repository Alignment

## Current State — Standalone Clone Target

Local workspace path:
- this repository root

Git root (standalone):
- expected to equal this repository root after `git init`

Active remote:
- intentionally unset until the product remote is chosen

## What Changed in v0.7.0

Previously: the source workspace was nested inside a broader working area.
This created risks:
- `git status` was noisy with hundreds of untracked home-dir files
- Any `git add .` from home dir could commit NTUSER.DAT, `.ssh/`, `.aws/`
- PKA versioning was file-driven because git was unsafe to use

**Target**: `git init` is run inside this clone, creating a clean standalone
`.git` here.

## Repo Shape (clean)

```text
pka-workspace/
  README.md
  CLAUDE.md
  VERSION
  CHANGELOG.md
  RELEASE_PROCESS.md
  REPO_ALIGNMENT.md
  .gitignore
  Team/
  Team Inbox/
  Owner's Inbox/
  scripts/
  .claude/agents/
```

## Release Rule

The repo is aligned.  All future PKA releases should:
1. `cd` to the repo root
2. `git add` / `git commit`
3. `git push origin main` only after an intentional remote is configured

Do NOT reference any parent repo for PKA versioning.

## Doctor Check

`pka_doctor.py check_git_boundary` verifies that
`git rev-parse --show-toplevel` equals `ROOT` (derived from
`Path(__file__).resolve().parent.parent`).  This check passes post-v0.7.0.
