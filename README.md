# Agent Project Governance (APG) · v1.1

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

Version: 1.2.0. Project copies are updated through reviewed changes, not automatic overwrites.

## One-link adoption and agent switching

**Initialize:** Give an agent your new repository URL and say: "Initialize using [APG BOOTSTRAP.md](BOOTSTRAP.md); verify default-branch readiness."

**Resume:** Give any agent the initialized repository URL and say: "Read AGENTS.md, recover live context and execute the next authorized task."

See [Adoption guide](docs/ADOPTION.md), [Manifest template](docs/APG_MANIFEST.yml), and [Task selection policy](docs/TASK_QUEUE.md). Initialization is complete only after merge into the target default branch. Agents without write access can prepare a patch but cannot complete setup.

## Issue handling and short cross-agent handoffs (v1.2)

- [Problem registration, triage, repair and evidence](.agent/ISSUE_LIFECYCLE.md)
- [Unique numbered dispatches and Git-backed instructions](.agent/DISPATCH_PROTOCOL.md)
- [Execution report template](.agent/templates/EXECUTION_REPORT.md)
- [Problem record template](.agent/templates/PROBLEM.md)

Adapted from [AI-Dev-Bridge-Lite](https://github.com/zyzmlwxy/AI-Dev-Bridge-Lite) with a single-agent default; optional cross-agent handoff is sequential, not a mandatory multi-agent pipeline.
