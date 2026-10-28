# Development and Testing

- Setup: TBD
- Build: TBD
- Unit tests: TBD
- Integration tests: TBD
- Lint / formatting: TBD
- CI checks: TBD
- Supported platforms: TBD

Use project-defined commands. Never guess commands with destructive side effects.

## Git-first development requirement
Read `.agent/GIT_SOURCE_OF_TRUTH.md` before editing. The verified authorized Git remote governs all project source and deliverable history. Pull/read current remote state, reconcile local changes, and use an approved task branch. Commit, push and independently verify all in-scope non-secret source, headers, tests, scripts, non-secret configs and necessary documentation before claiming delivery; record full commit SHA, branch and PR. Do not confuse an unmerged PR with integrated default branch. If sync is unavailable or unauthorized, report `SYNC_BLOCKED` rather than claiming completion. Keep credentials, machine-only configuration, caches and disposable build intermediates out of Git.
