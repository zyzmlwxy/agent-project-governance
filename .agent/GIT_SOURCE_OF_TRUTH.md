# APG Git-first development and mandatory deliverable synchronization (v1.2.5)

## Non-negotiable rule
**The authorized project's Git remote is the durable source of truth for development and all shareable project deliverables.** No agent's chat memory, private workspace, local branch, unpushed commit or exported ZIP may silently supersede verified remote repository history. GitHub Issues/PRs and linked reports remain canonical for task decisions, reviews, progress and acceptance; running tests and deployment probes are canonical for actual observed behavior. Do not equate a written claim in Git with an executed test.

**Every non-secret, in-scope deliverable must be committed AND pushed to the corresponding authorized project repository**, on an authorized task branch or approved default branch, with a real remote read-back. This includes source and header files, scripts, tests, dependency manifests and lockfiles, non-secret configurations, database migrations, interface definitions, assets needed to reproduce the project, design/architecture/usage documentation, task-relevant handoffs, issue logs and sanitized validation reports. Do not use the central APG template repository as a dumping ground for another project's deliverables.

## Required operating sequence
1. **Before development:** identify the canonical repository, verified remote URL, default branch and current HEAD. Fetch or otherwise read the remote branch, Issues, PRs, reviews/checks and last handoff. Inspect local branch, untracked and uncommitted changes and compare local/remote commit ancestry. A worktree snapshot is provisional until reconciled with remote. Never overwrite dirty user work or force-reset to resolve a mismatch.
2. **Choose an authorized work location:** usually a task branch and PR linked to an existing Issue. Do not use direct default-branch pushes unless the project's policy and current authorization explicitly permit them. Respect the single execution owner and existing PR to avoid competing commits.
3. **Develop and check:** modify only the approved scope; validate as required. Local intermediate edits may remain uncommitted while actively editing but are **not delivered**. Do not claim that chat output or a local ZIP is a sufficient substitute for Git.
4. **Synchronize deliverables:** prior to claiming a stage or task finished, review changed/untracked files and ensure every relevant non-secret deliverable has been staged, committed and pushed to the correct remote branch. Scan for credential, personal or environment secrets; exclude only genuine local-only files. Persist sanitized decisions, instructions and verification results as Issue/PR records or repository files.
5. **Verify remote read-back:** independently query the remote branch ref/commit SHA and verify expected files/changes exist at the intended path; compare with the local commit. Provide the repository/branch, full commit SHA, PR or commit link, and whether the changes are **PUSHED_UNMERGED**, **MERGED_DEFAULT_BRANCH** or **SYNC_BLOCKED**. An open PR, a local commit and a merged default branch are distinct states.
6. **Before switching agents or resuming:** always re-read latest Git evidence and reconcile it against local files and handoff records. If local work differs from Git, identify the cause and owner, preserve the local changes, and get any required approval before reconciling. Never assume the local folder is newer or more authoritative just because its files have recent timestamps.

## Completion and failure semantics
- `WORKING_LOCAL`: changes still only in workspace; not a delivered artifact.
- `COMMITTED_LOCAL`: committed but not remotely verified; not delivered.
- `PUSHED_UNMERGED`: committed and remote-verified on authorized branch; deliverable preserved but not yet integrated.
- `MERGED_DEFAULT_BRANCH`: remote default branch verified to contain the approved changes.
- `SYNC_BLOCKED`: remote access, write authorization, permissions, secret scanning or conflicts prevent push/read-back. Record the actual reason and a non-secret pending-change inventory; do not report full delivery or invent a remote SHA.
- Do not imply a Git push, PR merge, successful CI, deployment or user-facing acceptance proves any of the others. Completion must meet the task's approved criteria, including whichever merge/validation steps are required.

## Allowed exclusions and private material
- NEVER sync SSH/private keys, passwords, tokens, private environment configs, sensitive logs or unapproved identity/topology details. The secret stays under an ignored local path such as `.agent-local/`; Git may retain only an approved safe path/variable and setup contract as specified in `docs/LOCAL_PRIVATE.md`.
- Ephemeral caches, IDE state, temporary experiments and reproducible build intermediates need not be tracked unless the user expressly requires them as deliverables. Update `.gitignore` carefully; never use broad ignore rules to conceal relevant source changes.
- Large or generated **required deliverables** still need an approved Git-compatible storage plan (e.g. Git LFS or referenced approved artifact repository with checksums and persistent links, when the project policy permits). Do not silently omit them. If the destination cannot support a required deliverable, report `SYNC_BLOCKED` and seek approval for an alternative.
- Before pushing in a public repository, verify content classification and disclosure permissions. Never satisfy this rule by publishing private content.

## Relationship to newly discovered problems
Follow `.agent/ISSUE_DISCOVERY.md`: unapproved new out-of-scope defects are presented only as 1/2/3/4 candidates and **must not** be silently registered in Git or assigned permanent IDs. Approved problem records, current-task evidence and authorized environment incident logs are durable Git deliverables. The Git-sync mandate does not override user approval, access controls or security.

## Unavailable Git connection
If a tool lacks repository access or push rights, report `SYNC_BLOCKED` with a sanitized inventory of the remaining outputs and what authorization is missing. Do not claim a local-only patch, chat response or unverifiable branch URL has been synchronized. Preserve authorized local work without overwriting it and provide a minimal follow-up path for an authorized agent.
