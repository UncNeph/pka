# PKA Clone Manifest

Created: 2026-05-15

## Purpose

This folder is a clean core copy of the PKA workspace. It is intended to keep
the operating system for the agent team without the unrelated projects,
prototype app folders, local caches, generated dependencies, screenshots, or
zip archives that accumulated in the original workspace.

## Included

- Workspace bootstrap and release memory:
  `AGENTS.md`, `MEMORY.md`, `VERSION`, `CHANGELOG.md`, `CLAUDE.md`, `README.md`,
  `RELEASE_PROCESS.md`, `REPO_ALIGNMENT.md`
- Local repo/process config:
  `.gitignore`, `.pre-commit-config.yaml`, `.github/`, `.snapshots/`,
  `pyproject.toml`
- Agent definitions:
  `.claude/agents/`, `.claude/launch.json`, `.claude/settings.local.json`
- Team operating memory:
  `Team/`
- Owner delivery history and evidence:
  `Owner's Inbox/`
- Intake folder structure:
  `Team Inbox/README.md`
- Governance and verification tools:
  `governance/`
- PKA operational scripts:
  `scripts/pka_*.py`, `scripts/gmags_doctor.py`, `scripts/agent_brain/`
- Why Engine source:
  `tools/why-engine/` without `.git`, `node_modules`, or `dist`

## Excluded

- Side projects and prototypes unrelated to the PKA product repo
- Review clones and extracted/generated folders:
  `_reviews/`, `__design_extract__/`, `tmp_extract/`,
  `design_handoff_red_team_console/`, `Red Team (1)/`
- Runtime/generated noise:
  `.git/`, logs, Playwright folders, pytest/ruff caches, temp screenshots,
  zip/tar archives, `node_modules`, `dist`
- Root-level one-off helper scripts tied to side projects or terminal injection
  experiments

## Original Folder

No existing files in the original workspace were edited or moved during this
clone operation. The original workspace only gained this new `pka clone/`
folder.
