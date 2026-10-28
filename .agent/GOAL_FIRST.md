# Goal-first execution and proportionate issue handling (APG v1.2.3)

## Principle
Prioritize delivering the **currently authorized objective** and its agreed acceptance criteria. Do not indefinitely delay useful functionality to chase every newly discovered low-impact edge case. This is a prioritization rule, **not** permission to misstate acceptance, ignore safety, broaden scope, merge or deploy without authorization.

## Decision during execution
For each newly observed issue, determine:
- Does it prevent the current goal or an explicitly required acceptance check?
- What is the likely impact, affected users and likelihood of triggering? What evidence supports that estimate?
- Is there risk of security/privacy compromise, data loss/corruption, irreversible action, material regression or compliance failure?
- Is the issue easily reversible or safely isolated, with a workaround or monitoring option?

**Must address or escalate before claiming success:** blocking acceptance failures, significant user impact, security/privacy issues, data integrity or irreversible harm, unknown/high risk, or issues likely to worsen with deployment. Do not relabel them 'rare' without evidence.

**May defer:** a demonstrably minor-impact issue, or a rare issue with bounded consequences, when it does not block an agreed acceptance criterion or safety guardrail. If probability is unknown, say UNKNOWN; do not invent a percentage. A rare event with severe consequences is not deferrable solely because it is rare.

When deferring, preserve the current goal, keep the change minimal and reversible, and continue work within existing authorization. If the acceptance scope must change, ask the user and record their decision; do not silently weaken criteria.

## Reporting after each execution
Report the current goal outcome first (completed / partially completed / blocked, with actual evidence). Then give **one consolidated temporary numbered list** of newly discovered issues, including minor/rare deferred items, using the existing `ISSUE_DISCOVERY.md` approval gate. For each item give a plain-language description, impact, likelihood (observed / estimated / UNKNOWN), whether it was deferred and why, and recommended next action. Example:

1. [暂缓] 极少数消息未按预期显示；影响较小，触发频率尚未测量；不阻碍本次目标。建议后续评估。
2. [需确认] 特定情况下保存可能失败；影响和发生概率未确认；建议先核实。

Do **not** register new out-of-scope issues in GitHub or allocate permanent IDs until the user confirms which temporary numbers to record. Keep failures and deviations of the already authorized task in its existing Issue/PR, regardless of this gate.

## End-state clarity
- "Goal completed" means the explicitly approved acceptance criteria passed; separately disclose deferred limitations.
- "Partially completed" means useful work exists but one or more required criteria remain unmet.
- "Blocked" means execution cannot safely proceed.
- Any decision to accept a known limitation that changes acceptance criteria must be made by the user and linked to the original task.
- Approval to record a newly discovered issue is not approval to fix or deploy it.
