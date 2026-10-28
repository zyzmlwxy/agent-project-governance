# Environment incident capture and prior-fix-first recovery (APG v1.2.4)

## Before troubleshooting
Whenever a tool, SSH/NAS connection, repository access, build environment, credentials reference or deployment step fails, first search `docs/ENVIRONMENT_INCIDENTS.md`, `docs/LOCAL_PRIVATE.md`, relevant Issues/PRs and recent reports for similar symptoms and matching execution environment. Match by agent identity, environment alias, tool/version, service, error class and known-good procedure. Do not ask the user to recreate previously documented setup before checking it.

## Evidence and scope
Record **which Agent actually experienced the failure**, environment alias and OS/tool versions, observed error/exit code, timestamps, attempted steps, cause (confirmed vs suspected), last known-good method, current outcome and next safe action. Distinguish historical, user-reported and freshly verified evidence. If an environment changed, explicitly record the difference.

For a key-backed SSH connection, Git may contain a **path reference** to the private key and the need for it, but never the key bytes, passphrase, token, secret-bearing config or sensitive log. A path is not permission to read, print or use a key; respect existing authorization. Prefer project-relative `.agent-local/...` paths or named variables for public repos. Real absolute paths are permitted only when disclosure is explicitly acceptable under the target repository's visibility and policy, and when they do not expose sensitive identity, topology or credentials. Store sensitive absolute paths locally and reference their contract from Git.

## Writeback rule
A troubleshooting event **within an already authorized task** is operational evidence: update the original Issue/PR and `docs/ENVIRONMENT_INCIDENTS.md` using an approved documentation-write route, without waiting for a new out-of-scope Issue approval. Do not create a permanent new product-defect Issue automatically. If Git writes are not authorized or possible, prepare a sanitized draft and report BLOCKED; do not bypass permissions.

Before repeating potentially harmful or state-changing diagnostics, check prior attempts and require applicable authorization. Use bounded, read-only probes first; do not regenerate SSH keys, loosen host-key checks, change firewall, install tools or modify credential configuration merely because a past connection failed.

## Resolution
After repair or a successful reconnect, append verified method, exact environment scope, validation time and result. Mark RESOLVED only with evidence; preserve earlier failures. At the next incident, re-check current environment and re-verify rather than assuming historical success still holds.

## Relationship to discovery approval gate
Operational incident evidence belongs to the existing authorized task and environment knowledge base. Newly discovered independent repair work remains a numbered candidate requiring user confirmation before GitHub Issue creation and permanent task ID allocation.
