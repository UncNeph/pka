# PKA Clone Acceptance Test — 2026-05-15

## Verdict

PARTIAL GO.

The clone is operational as a PKA core workspace: Python scripts compile,
core PKA audits pass, runtime integrity passes, E2E passes, resilience passes,
full validation passes, governance tools pass, Agent Brain imports and runtime
path checks pass, and Why Engine builds/tests after dependency installation.

It is not yet a clean standalone production-grade clone because it lacks its
own `.git` boundary, clone-local Claude settings still reference original
workspace paths, and Why Engine root dependencies report npm audit
vulnerabilities.

## Major Passes

- `python -m compileall scripts governance` — PASS
- `python scripts/pka_doctor.py` — PASS with warnings
- `python scripts/pka_process_audit.py` — PASS
- `python scripts/pka_runtime_check.py` — PASS
- `python scripts/pka_e2e_test.py` — PASS
- `python scripts/pka_resilience_test.py` — PASS, 100/100
- `python scripts/pka_full_validation.py` — PASS, 100/100, 8/8
- `python -m ruff check scripts governance` — PASS
- `python scripts/pka_session_gate.py start` — PASS
- Governance smoke tests — PASS
- Agent Brain import/help/runtime-path checks — PASS
- Why Engine root `npm test` after `npm ci` — PASS, 11/11
- Why Engine web backend `npm run build` — PASS
- Why Engine web frontend `npm run build` — PASS
- Why Engine web `npm audit --audit-level=moderate` — PASS, 0 vulnerabilities

## Findings

### Critical

1. The clone is not a standalone git repo.
   - `pka clone` has no `.git`.
   - `git rev-parse --show-toplevel` resolves to the parent original workspace:
     `C:\Users\techai\PKA testing`.
   - Impact: repo-boundary checks warn, git status is inherited from the
     original folder, and the clone is not yet a safe independent working copy.

### High

2. Clone-local Claude settings still referenced original/excluded paths.
   - File: `.claude/settings.local.json`
   - Examples included references to side-project paths and a post-tool hook
     path under the original workspace instead of the clone.
   - Impact: a future Claude/Codex session launched inside the clone may call
     tools or hooks outside the clone.

3. Why Engine root dependency audit reports vulnerabilities.
   - Command: `npm audit --audit-level=moderate`
   - Result: FAIL, 7 vulnerabilities: 2 moderate, 5 high.
   - Main packages implicated: `@hono/node-server`, `hono`,
     `express-rate-limit`, `fast-uri`, `path-to-regexp`, `ajv`, `ip-address`.
   - Impact: Why Engine source builds and tests, but root dependency posture
     needs remediation before production/service exposure.

4. A historical task expects a script not included in the clean clone.
   - File: `Team/tasks/20260401-build-ai-army-group-chat-client-script-20260401-005.md`
   - Missing artifact: `scripts/ai_army_chat.py`
   - Impact: readiness and machine-health checks can show degraded coverage if
     the AI Army chat client is considered core.

### Medium

5. Readiness is degraded by clone infrastructure gaps.
   - `python scripts/pka_agent_readiness.py` returned 87/100.
   - Reported gaps: missing validation history, missing pre-commit git gate,
     and no standalone repo boundary.

6. Scorecard is not release-ready in the fresh clone context.
   - `python scripts/pka_scorecard.py` returned 68/100.
   - Main driver: no recent delivered-task throughput in the cloned history.
   - This is a historical/metrics issue, not a functional script failure.

7. Machine health has environment warnings.
   - Spark SSH failed due key permission/remote auth.
   - AWS identity passed.
   - Impact: live remote machine reachability is not fully green from this
     machine/session.

8. Agent Brain local model status can hang when local Ollama is unavailable.
   - `python -m scripts.agent_brain status --model local` timed out in the
     delegated check after about 34 seconds.
   - Cloud status returned promptly but reported backend offline.

9. Testing created generated artifacts inside the clone.
   - Python checks created `__pycache__` folders.
   - Governance smoke tests created `logs/policy_check.jsonl`.
   - Why Engine tests/builds created `node_modules` and `dist` folders.
   - Impact: the clone is now tested and bootstrapped, but not as minimal as the
     original clean copy.

## Notes

- The first `pka_full_validation.py` run timed out because the local command
  timeout was too short. A later run with a longer timeout passed completely.
- No original workspace source files were moved or edited by this test pass.
  All test execution happened under `pka clone`.

## Recommended Fix Order

1. Initialize `pka clone` as its own git repo or move it outside the parent git
   workspace and then initialize git.
2. Rewrite `.claude/settings.local.json` so hooks and allowed paths are
   clone-local or intentionally external.
3. Decide whether `scripts/ai_army_chat.py` is core. If yes, add it; if no,
   update readiness/machine-health expectations and historical task references.
4. Remediate Why Engine root npm audit findings with dependency upgrades.
5. Add a bootstrap script documenting required installs:
   Python lint/test prerequisites, Why Engine root `npm ci`, and Why Engine web
   `npm ci`.
6. Optionally clean generated artifacts if the clone should return to a minimal
   source-only state.
