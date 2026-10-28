# Workflow v1.0

## Task intake
1. Search open and closed Issues, PRs, relevant commits and existing implementation before creating new work.
2. Use a unique per-project task ID `PREFIX-NNNN`; do not reuse IDs even for supplementary instructions. Link `parent_task` for follow-ups.
3. Issue is canonical: purpose, scope, acceptance criteria, risk, dependencies, owner, evidence links.
4. Allocate IDs with a single serialized allocator or a protected counter/issue-creation workflow; never compute `max + 1` concurrently. GitHub Issue numbers are intrinsically unique and may be used as the canonical fallback (`PREFIX-GH-<issue_number>`).

## Execution
1. One active execution owner per task; confirm ownership in Issue and check existing branch/PR.
2. Create a focused branch; protect uncommitted user changes and never force-reset without approval.
3. Make minimal changes; test according to risk; link commit and PR to Issue.
4. On interruption, checkpoint in `docs/AI_HANDOFF.md` and/or Issue, with SHA, dirty paths, tests, blockers and next action.
5. For handoff, outgoing owner releases task; incoming owner verifies current remote/local state before taking ownership.

## Closeout
- Record acceptance evidence and limitations.
- Distinguish implementation, review, merge, deployment, and online validation.
- Update project status/handoff on material changes; do not duplicate full Issue content.
- Close only when Issue's approved Definition of Done is satisfied. Reopen or create linked follow-up for regression.

## Communication
- Instruction header: `[PREFIX-NNNN][TO:AGENT]`.
- Each newly delegated actionable instruction receives a new ID, including revisions; connect to parent Issue.
- Never silently broaden scope; record changes to acceptance criteria before applying them.

## Problem handling and dispatch
Follow `ISSUE_LIFECYCLE.md` for issue deduplication, failure classification, retry, tested SHA and acceptance. Follow `DISPATCH_PROTOCOL.md` for per-instruction H numbers, recipient identity, Git-backed detailed prompts and idempotent reforwarding. A new instruction can share an Issue but must not reuse an old dispatch ID.

## Delivery priority
Apply `.agent/GOAL_FIRST.md` while implementing: finish the currently approved objective before pursuing unrelated low-impact issues, unless a safety or acceptance gate requires escalation. Report all deferred issues after execution using `.agent/ISSUE_DISCOVERY.md`.
