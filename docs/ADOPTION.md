# APG adoption and migration

## New empty repository
Give any agent the repository URL and this bootstrap instruction:
"Initialize this repository using https://github.com/zyzmlwxy/agent-project-governance/blob/main/BOOTSTRAP.md, then verify the result."

## Existing repository
Same instruction. Agent inventories existing conventions, preserves code and history, reconciles instructions, and uses a PR by default. Never replace an existing AGENTS.md blindly.

## Subsequent agent handoff
Give only the initialized repository URL and ask:
"Resume this repository according to its AGENTS.md, verify live GitHub state and continue the next authorized task."

## Readiness checks
- APG marker in root AGENTS.md.
- docs/APG_MANIFEST.yml points to an actual pinned source revision.
- docs/TASK_QUEUE.md defines selection and precedence.
- docs/PROJECT_STATUS.md and docs/AI_HANDOFF.md reflect verified repository state.
- .agent/SECURITY.md and docs/PROJECT_RULES.md define permissions.
- .gitignore excludes local secrets.
- Initialization is merged into default branch (not merely proposed).

## Limitations
A URL alone cannot grant repository access, secrets, local environment or deployment permission. An agent with read-only GitHub access can recover context and propose work, but cannot push. Without an existing task or deterministic selection metadata, the agent should request clarification.
