# Security and Authorization

Default: read-only discovery is permitted; write/build/test only in authorized workspaces; no production deployment, destructive changes, secret disclosure, privilege changes or force pushes without explicit applicable permission.

Risk levels:
- LOW: docs, isolated nonfunctional change. Local verification; review optional if authorized.
- MEDIUM: normal feature/bug fix. Tests + PR review; deployment only if approved policy permits.
- HIGH: data migration, auth, production behavior, critical integration. Explicit review and deployment approval, backup and rollback.
- CRITICAL: destructive operations, credential rotation, irreversible changes. Explicit operation-specific approval and recovery plan.

Risk is determined by impact, reversibility, exposure and uncertainty. Highest applicable risk wins. Agent cannot downgrade risk to bypass approval.

Never place secrets in GitHub, logs or AI handoffs. Stop and escalate when a secret leak is suspected. Prefer least privilege and redact all evidence.

## Credential file locations versus contents
Documenting a credential file's location is distinct from publishing its contents. Safe project-relative paths or variable names may be recorded for troubleshooting; identity-bearing or sensitive absolute paths require repository visibility review and should remain in ignored local files. Never commit credential bytes, passphrases, tokens or secret-bearing configuration. A recorded path never grants authorization to access or use a credential.
