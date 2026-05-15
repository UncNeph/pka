# PKA Clone Sanitization — 2026-05-15

## Verdict

GO.

`pka clone/` is now a standalone PKA product repo. The clone has its own git
boundary, clone-local configuration, scrubbed project memory, PKA-only delivery
history, clean side-project reference scan, passing PKA validation, and a clean
Why Engine dependency audit.

## What Changed

- Removed external environment entries from `.claude/settings.local.json`.
- Repointed the post-tool hook to the clone-local PKA hook with `python`.
- Removed all external launch configs from `.claude/launch.json`.
- Replaced conflicted CI with minimal PKA CI: ruff plus `pka_doctor`.
- Removed venture/project-specific rules from `CLAUDE.md` and `MEMORY.md`.
- Scrubbed agent cards for product-specific PKA language.
- Pruned `Owner's Inbox/` to PKA deliverables, reports, evidence, recovery,
  manifest, dashboard, and clone reports.
- Removed side-project task records and cleaned handoff/status state.
- Removed stale per-file ignore for removed script paths in `pyproject.toml`.
- Replaced hardcoded remote host defaults with environment-driven config.
- Regenerated machine-health and proof-dashboard reports from sanitized state.
- Initialized `pka clone/` as its own git repository.
- Remediated Why Engine root npm audit findings with `npm audit fix`.

## Validation

- `python -m ruff check scripts governance` — PASS
- `python scripts/pka_doctor.py` — PASS, overall healthy
- `python scripts/pka_process_audit.py` — PASS
- `python scripts/pka_e2e_test.py` — PASS
- `python scripts/pka_resilience_test.py` — PASS, 100/100
- `python scripts/pka_full_validation.py` — PASS, 100/100, 8/8
- Side-project reference scan across repo source, excluding generated dependency
  and build folders — PASS, zero hits
- `npm test` in `tools/why-engine` — PASS, 11/11
- `npm audit --audit-level=moderate` in `tools/why-engine` — PASS, 0 vulnerabilities

## Notes

- Generated dependency/build/runtime folders remain ignored by `.gitignore`.
- The repo has no remote configured yet; that should be intentional when chosen.
- All modifications were scoped to `pka clone/`.
