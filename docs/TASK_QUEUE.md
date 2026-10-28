# Deterministic task selection (APG v1.1)

The GitHub Issue register is canonical. This file defines *selection policy*, not a duplicate task list.

## Required Issue metadata
- Exactly one status label: status:open, status:active, status:blocked, status:review, status:done, status:cancelled, status:superseded.
- Exactly one priority label: priority:p0, priority:p1, priority:p2, priority:p3 (p0 highest).
- Risk label: risk:low, risk:medium, risk:high or risk:critical.
- Task ID, acceptance criteria, dependencies, owner, related PR and evidence in Issue body.
- An optional `apg:next` label designates the explicit next task.

## Selection algorithm
1. Fetch *all* open Issues (paginate) and relevant open PRs; do not rely on only recent items.
2. First resume the unique `status:active` Issue owned by the current agent or explicitly released in the last handoff, if safe and unblocked. If multiple candidates conflict, stop and report.
3. Otherwise choose unique eligible Issue marked `apg:next`. If multiple, stop and request disambiguation.
4. Otherwise choose eligible `status:open` Issue ordered by priority p0→p3, then Issue creation time ascending, then Issue number ascending.
5. Eligible means no unresolved dependencies, no conflicting owner or active PR, not blocked, and scope/risk permitted.
6. If the selected Issue is missing acceptance criteria or required permission, report it as selected-but-blocked and do not skip silently to a lower-priority task.
7. If no eligible task exists, report idle with open blockers and ask for next task.
8. 'Latest task' means the *next authorized actionable task* under this policy, NOT the newest Issue or latest chat instruction.

## Ownership
Single execution owner per Issue. Before taking ownership, read latest Issue activity and handoff. Record agent identity and timestamp in Issue; release on handoff. If another owner is active and not explicitly released, do not race them. Ownership staleness requires user confirmation or a documented project lease policy.

## Integrity
When labels are missing/inconsistent, stop or propose metadata repair; never fabricate task state. GitHub Issue number is a collision-free fallback task identifier; custom PREFIX-NNNN must be allocated serially.
