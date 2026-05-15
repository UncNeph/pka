# Delivery Manifest

This file is the index of completed PKA product deliverables.
Newest entries go at the top.

| Date | Task | Route | Verdict | Deliverable | Next Action |
|------|------|------|------|------|------|
| 2026-05-15 | PKA clone sanitization | Codex/FORGE | GO — standalone product repo, tests green, dependency audit clean | Owner's Inbox/PKA-clone-sanitization-2026-05-15.md | Configure remote only when ready |
| 2026-05-15 | PKA clone acceptance test | Codex,worker agents | PARTIAL GO — core workspace validates; standalone repo/settings/dependency issues remain | Owner's Inbox/PKA-clone-acceptance-test-2026-05-15.md | Initialize clone git boundary; localize settings; remediate dependency audit findings |
| 2026-05-14 | PKA v0.9.0 pipeline test | FORGE,WRAITH,CRUCIBLE,SENTINEL,DEBUGGER | GO | Owner's Inbox/evidence/whycase-display-data-divergence-v090-2026-05-14.json | Keep WRAITH and Why Engine in the Build route |
| 2026-04-02 | PKA v0.6.0 gap close | AXIOM,FORGE,CRUCIBLE,SENTINEL | GO | Owner's Inbox/reports/PKA_LATEST_VALIDATION_REPORT.md | Continue using validation as the release gate |
| 2026-04-02 | TASK-20260402-012 CRUCIBLE reopen test | CRUCIBLE | GO | Owner's Inbox/reports/PKA_LATEST_VALIDATION_REPORT.md | Keep reopen tests in the validation path |
| 2026-04-02 | TASK-20260402-007 SENTINEL: PKA v0.5.0 GO/NO-GO Verdict | SENTINEL | HOLD to GO | Owner's Inbox/reports/PKA_LATEST_VALIDATION_REPORT.md | Keep scorecard evidence populated |
| 2026-04-02 | TASK-20260402-006 RADAR: PKA v0.5.0 Opportunity Scan | RADAR | GO | Team/tasks/20260402-radar-pka-v0-5-0-opportunity-scan-20260402-006.md | Keep product opportunities tied to PKA only |
| 2026-04-02 | TASK-20260402-004 CRUCIBLE: PKA v0.5.0 Full Script Test Sweep | CRUCIBLE | PARTIAL PASS | Owner's Inbox/reports/PKA_LATEST_VALIDATION_REPORT.md | Preserve as historical validation baseline |
| 2026-04-02 | PKA resilience self-cleanup fix | AXIOM,FORGE,SENTINEL | GO | scripts/pka_resilience_test.py | None |
| 2026-04-02 | TASK-20260402-008 FORGE: Fix pka_resilience_test.py stub self-cleanup | AXIOM,FORGE,SENTINEL | GO | scripts/pka_resilience_test.py | None |
| 2026-04-01 | TASK-20260401-006 Rebuild PKA scorecard with real task history metrics | AXIOM,FORGE,SENTINEL | GO | scripts/pka_scorecard.py | Use real task history and evidence coverage metrics |
| 2026-04-01 | TASK-20260401-001 E2E Process Validation Task | AXIOM,FORGE,CRUCIBLE,SENTINEL | delivered | Team/tasks/20260401-e2e-process-validation-task.md | Keep this path as the baseline for consequential tasks |
| 2026-03-31 | TASK-20260331-001 Process hardening control layer | AXIOM,FORGE | delivered | Team/OPERATING_MODEL.md, Team/TASK_BRIEF_TEMPLATE.md, Team/tasks/, scripts/pka_process_audit.py | Use the task ledger and run the process audit at session end |
