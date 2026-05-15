# Release Process

This repo uses `VERSION` and `CHANGELOG.md` as the canonical release line.

## Repo Constraint
The clone must be initialized as its own git root before release tags or pushes.
Until a remote is configured intentionally, local git history plus
`VERSION`/`CHANGELOG.md` are the source of truth.

## Release Rules

1. Update `VERSION`
2. Add a new entry to `CHANGELOG.md`
3. Run:
   - `python scripts/pka_process_audit.py`
   - `python scripts/pka_e2e_test.py`
   - `python scripts/pka_resilience_test.py`
   - `python scripts/pka_full_validation.py`
4. Confirm `Team/handoff.md` and `Team/status.md` reflect reality
5. Confirm `Owner's Inbox/DELIVERY_MANIFEST.md` is current
6. Generate updated observability output with `python scripts/pka_observability.py`
7. Only call a version "green" if the validation suite passed on the real workspace

## Versioning Scheme

Use semantic-style versions:
- `MAJOR`: operating model or compatibility break
- `MINOR`: meaningful capability expansion
- `PATCH`: fixes, clarifications, hardening with no workflow break

## Recommended Git Future State

Best path:
- initialize this folder as its own repository
- configure an explicit product remote
- tag releases from that dedicated repo
