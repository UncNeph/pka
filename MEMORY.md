# Workspace Memory Index

This is the canonical startup index for the standalone PKA product repo.

## What This Workspace Is

- Standalone PKA agent-operations workspace
- AXIOM-centered multi-agent operating model
- `Team Inbox/` is intake
- `Owner's Inbox/` is delivery
- PKA scripts and governance tools are the testable product surface

## Canonical Memory Stack

### Identity And Rules

- `VERSION` — current workspace release number
- `CHANGELOG.md` — latest implemented changes by version
- `CLAUDE.md` — workspace identity, agent roster, startup and shutdown rules
- `README.md` — repo overview and operator commands
- `Team/CORE_RULES.md` — team-wide non-negotiables
- `Team/OPERATING_MODEL.md` — canonical lifecycle and process rules
- `Team/roster.md` — active agent roster and responsibilities

### Current Session State

- `Team/handoff.md` — latest session summary and next attention items
- `Team/status.md` — active work and session-start checklist
- `Team Inbox/` — unprocessed user input for the team

### Completed Work History

- `Owner's Inbox/DELIVERY_MANIFEST.md` — indexed history of consequential PKA deliverables
- `Owner's Inbox/reports/` — generated PKA validation and observability reports
- `Owner's Inbox/evidence/` — evidence bundles and WhyCases
- `Owner's Inbox/recovery/` — recovery playbooks
- `Team/tasks/` — task records, definitions of done, operational history

### Agent Memory

- `Team/AXIOM/journal.md`
- `Team/CRUCIBLE/journal.md`
- `Team/DEBUGGER/journal.md`
- `Team/FORGE/journal.md`
- `Team/GRID/journal.md`
- `Team/HELM/journal.md`
- `Team/LEGAL/journal.md`
- `Team/NOVA/journal.md`
- `Team/RADAR/journal.md`
- `Team/SCRIBE/journal.md`
- `Team/SENTINEL/journal.md`
- `Team/SPARK/journal.md`
- `Team/VENTURE/journal.md`

## Retrieval Protocol

- For version questions, start with `VERSION`, then `CHANGELOG.md`.
- For latest session state, start with `Team/handoff.md`, then `Team/status.md`.
- For completed PKA work, inspect `Owner's Inbox/DELIVERY_MANIFEST.md`.
- For task-specific history, inspect the relevant `Team/tasks/` record.
- For agent-specific history, read that agent's journal before answering.
- For ambiguous prior-work questions, search the repo instead of guessing.

## Current High-Signal State

- Current workspace version is `0.9.0`.
- `0.9.0` added the WRAITH adversarial red-team layer, confidence vocabulary,
  trust ledger, and Why Engine root-cause documentation pipeline.
- `0.8.0` added the durable runtime layer.
- `0.7.0` established repo-boundary correction, production telemetry, and
  stronger session continuity.

## Guardrail

New chats in this repo should treat these files as persistent product memory
and should not answer prior-work questions from model memory alone.
