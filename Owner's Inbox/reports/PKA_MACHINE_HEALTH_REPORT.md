# PKA Machine Health Report

- Timestamp: 2026-05-15T20:34:26Z
- Overall: warnings present

## Checks
- runtime_cli: PASS | PKA runtime CLI present
- ssh_key_present: PASS | SSH key path: C:\Users\techai\.ssh\ai_army_codex
- remote_ssh: WARN | Remote health host not configured; live SSH skipped
- aws_identity: PASS | arn:aws:iam::723013807658:user/Spark1-Agent

## Notes
- This is a live environment diagnostic, not a release verdict.
- Remote SSH warnings usually indicate missing optional environment configuration, key ACL, host trust, or network reachability issues outside the workspace code.
