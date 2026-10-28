# Newly discovered problem approval gate (APG v1.2.2)

## Purpose
After each execution, an Agent may discover new defects, risks or improvement opportunities outside the currently approved task. **Do not immediately create GitHub Issues, assign permanent task IDs, change the public issue register, or start fixing those new problems.** First give the user a concise numbered candidate list and wait for explicit confirmation.

## User-facing candidate format
Use simple sequential numbers **1, 2, 3, 4 ...** (reset for each report). These are **temporary display numbers**, not project IDs or dispatch IDs.

Example:
1. 群聊中部分消息未触发预期响应——可能影响正常使用；建议修复。
2. 错误提示不清晰——影响排查效率；建议改进。

For each candidate: short plain-language symptom, user impact, and a proposed next action. Avoid technical implementation details unless the user asks. Clearly distinguish VERIFIED observations, hypotheses, and unconfirmed risks. Avoid duplicating already registered Issues; if a candidate appears related to an existing Issue, mark it as such and suggest updating the existing record after approval.

## Approval and persistence
1. At the end of each execution, inspect outcomes and existing Issues/PRs for newly discovered problems. Report new candidates as a numbered list only; keep the normal execution result and evidence report for the *original authorized task*.
2. Await user confirmation of selected numbers (e.g. "记录 1、3", "全部记录", "暂不记录"). Silence or a general acknowledgment is not approval.
3. For **approved** candidates, recheck GitHub for duplicates and current status. Reuse an existing Issue when it already tracks the same problem; otherwise create a new Issue using the project's canonical unique task ID allocation (GitHub Issue number fallback). Assign permanent unique IDs **only after approval**.
4. Update the plain-language `docs/ISSUE_REGISTER.md` and the canonical Issue with approved facts, cause uncertainty, risk, priority, acceptance criteria and next action. Cross-link the originating execution/Issue/PR and record the user's approval. Preserve history.
5. Report a mapping from temporary numbers to permanent Issue URLs/IDs, and explicitly distinguish registered from pending/declined candidates.
6. User approval to **record** an issue is not permission to **implement**, merge, deploy or perform risky operations. Prioritize and execute only under existing task-selection and authorization rules.
7. If GitHub write access is unavailable, report `BLOCKED` and retain the proposed numbered list in the chat; do not claim synchronization or invent Issue numbers. Do not silently commit the candidate list elsewhere.

## Exceptions
- A newly discovered security vulnerability, active secret leak, imminent data loss or severe ongoing incident may require an immediate **minimal safety warning** and approved containment procedure. Do not publish sensitive details to a public repository or wait to warn the user. Creating a permanent public Issue still requires user confirmation unless the project's explicit incident policy says otherwise.
- Existing task failures, required acceptance evidence, and blockers must still be recorded in their **already authorized** Issue/PR as part of normal execution. The approval gate applies to **new out-of-scope problems**, not to suppress truthful reporting of current-task failure.
- A new user request to perform work is governed by the normal unique dispatch ID rules; temporary discovery numbers must never be used as dispatch IDs.
