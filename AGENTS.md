<!-- APG-MANAGED: schema=1 version=1.2.1 -->
# APG bootstrap and resume

For a target project URL, follow [BOOTSTRAP.md](BOOTSTRAP.md). For an initialized project, follow its own root AGENTS.md, manifest, security and task-selection rules. Do not assume central repository permissions apply to target repositories.

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

## Issue and instruction continuity (v1.2)
Read `.agent/ISSUE_LIFECYCLE.md` before recording, fixing or closing problems; read `.agent/DISPATCH_PROTOCOL.md` before issuing any new agent instruction or handoff. Keep unique dispatch IDs, preserve attempt history and verify real test evidence.

## Nontechnical issue register
Maintain `docs/ISSUE_REGISTER.md` alongside canonical GitHub Issues. Every problem needs a plain-language description, impact, confirmed or uncertain cause, handling progress, outcome and next step. Read `.agent/templates/ISSUE_PUBLIC.md` for the format. No code, commands, SHA or technical stack traces in the public-facing description.
