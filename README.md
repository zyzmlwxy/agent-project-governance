# Agent Project Governance (APG) · v1.0

A reusable, GitHub Issue-first governance template for local projects and AI agents.

## Principles
- GitHub Issues are the canonical task register; commits and PRs document implementation.
- One active execution agent per task; sequential handoffs must be explicit.
- New agents recover context from repository evidence, not chat memory.
- Verification and deployment approvals are risk-based.
- Secrets remain local; Git tracks only paths and contracts.
- Keep historical decisions and project-specific overrides; never overwrite them silently.

## Quick start
1. Copy this template into a project.
2. Set the project prefix, permissions and environment in `docs/PROJECT_RULES.md`.
3. Fill `docs/PROJECT_STATUS.md`, `docs/AI_HANDOFF.md`, and private-path contract.
4. Read `AGENTS.md` before any agent work.
5. Create tasks in GitHub Issues, search for duplicates, link branches/PRs and evidence.

## Documentation
- [Agent entry](AGENTS.md)
- [Workflow](.agent/WORKFLOW.md)
- [Task rules](.agent/TASK_RULES.md)
- [Security](.agent/SECURITY.md)
- [Project rules](docs/PROJECT_RULES.md)
- [Handoff](docs/AI_HANDOFF.md)
- [Status](docs/PROJECT_STATUS.md)
- [Private files](docs/LOCAL_PRIVATE.md)
- [Deployment](docs/DEPLOYMENT.md)

## Scope
This is a starter template, not a complete automation system. Protected task-ID allocation, duplicate detection and full secret scanning are roadmap items. The bundled CI performs only basic checks.

Version: 1.0.0. Project copies are updated through reviewed changes, not automatic overwrites.
