# APG durable instructions and unique dispatch IDs (v1.2)

Adapted from AI-Dev-Bridge-Lite AGENTS.md §§7.6–7.7. Applies to **any** sender/recipient Agent, including the same agent after a new session.

## Identity
Use `[PROJECT-I<issue_number>-H<NN>-<RECIPIENT>]` at the **start** of each short user-forwarded instruction. PROJECT comes from the project's manifest; recipient is a stable project-defined agent code (e.g. GPT, WB, CODEX). Same task and round may have recipient-specific variants sharing the base `PROJECT-I24-H01`.

Every *new independently actionable instruction*, including supplement, recheck, revised acceptance, handoff or intentional rerun, gets the next unused H number and is recorded on the existing Issue. A byte-for-byte reforward of the **same** dispatch keeps its original ID and must not rerun side effects. An authorized retry of the same dispatch may use `-R02` and must record attempt/result; new numbering never grants new permissions.

Use Issue comments or an existing task ledger as the authoritative dispatch registry. Only one authorized dispatcher allocates a round at a time; read back the new entry before giving the user a short prompt. On collision, stop and reconcile. Never claim a number is registered before verifying it remotely.

## Git-backed detailed instructions
Save complete, sanitized task instructions in the target project Issue/PR or `.agent/handoffs/` on an approved branch. Include sender, recipient, dispatch ID, Issue/PR, objective, exact scope/non-goals, trusted baseline and SHA verification method, permissions, forbidden actions, acceptance criteria, evidence format and next actor. Never rely on chat history or put another project's private details in this public APG repository.

Only after the destination is remotely verified and readable by the recipient, return one short message:
`[PROJECT-I24-H02-CODEX] Read <verified Issue/PR/file URL>, check trusted AGENTS.md and current SHA, perform only the authorized task, then report the same ID and evidence.`
Pending PR/branch links must be identified as unmerged. If GitHub write or readback is unavailable, report BLOCKED; do not fabricate a durable handoff.

## Dispatch lifecycle
ISSUED → ACKED → IN_PROGRESS → PASS/FAIL/BLOCKED (skip unobserved stages). Record timestamp, executor, dispatch ID, attempt, actual SHA, result, sanitized evidence and next action. Recipient replies beginning with the full dispatch ID and state. Completed dispatches must be checked before retrying any side effects.

## No automatic agent wake-up
GitHub comments and Actions are not an always-on AI scheduler. The user or a separately authorized integration must start the recipient. This protocol does not grant write, shell, merge or deployment rights.
