# APG Agent Entry (v1.0)

## Mandatory startup
1. Read this file, `docs/AI_HANDOFF.md`, `docs/PROJECT_STATUS.md`, `.agent/WORKFLOW.md`, `.agent/SECURITY.md`.
2. Check Git status, main HEAD, open Issues, PRs and recent merged work; distinguish remote facts from local uncommitted changes.
3. Read `docs/LOCAL_PRIVATE.md` and check local private files without exposing their contents.
4. Before any implementation, search duplicate Issues/PRs and existing code.
5. Summarize confirmed state, uncertainty, current task, plan and permissions.

## Source of truth
- GitHub Issues: tasks and acceptance criteria.
- Git history/PRs: code changes and reviews.
- Actual tests/deployment evidence: verified behavior.
- `docs/PROJECT_STATUS.md`: concise project snapshot; `docs/AI_HANDOFF.md`: resumable work checkpoint.
- When sources conflict, verify and report; never silently overwrite.

## Safety
- No secrets in Git, PR, Issue, logs or reports.
- No destructive operation, production deployment or privilege change without applicable authorization.
- Single active execution owner per task; handoff explicitly releases ownership.
- Follow `.agent/` rules and project-specific `docs/PROJECT_RULES.md`.
