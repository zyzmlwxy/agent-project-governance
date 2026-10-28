# Task Rules

States: OPEN, ACTIVE, BLOCKED, REVIEW, DONE, CANCELLED, SUPERSEDED.
Use one `status:*` label at a time. Track `risk:low|medium|high|critical` and `type:*` labels.

Transitions: OPEN→ACTIVE; ACTIVE→BLOCKED/REVIEW; BLOCKED→ACTIVE; REVIEW→ACTIVE/DONE; OPEN/ACTIVE/BLOCKED→CANCELLED/SUPERSEDED with reason.

Each Issue must contain: task ID, objective, scope/non-goals, acceptance criteria, risk, owner, dependencies, related tasks, evidence, and deployment requirement.
Never equate merged PR with deployment. All terminal transitions require a reason and supporting links.

Detailed problem handling: `ISSUE_LIFECYCLE.md`. Unique instruction dispatches and Git-backed short handoffs: `DISPATCH_PROTOCOL.md`. Issue/task identity is distinct from each dispatch ID. Never recycle a dispatch ID for a new action.
