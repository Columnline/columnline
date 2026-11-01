# Shared pipeline contract

Read this with the focused stage skill and current Scheduled row. This contract describes agent behavior; it neither installs tools/timers nor grants permissions. Use the same business rules across engines, with only their existing tool adapters differing.

## Roles and records

Client intake captures, classifies and deduplicates new asks, questions and updates. Preserve exact words, source workspace/account, native message/thread and canonical tenant. Add new context to the existing issue; materially new scope is a linked ask/fix. Simple questions live in Snapshot's Tasks Questions list, not a new Linear issue or project. Internal intake stays stopped; internal own work belongs to an existing project/internal engineering cycle without self-acknowledgment.

Six shared workers own the six handoffs listed in the overarching skill. The Pipeline desk handles actual due/overdue commitments and calendar/timeline context only. Read **each issue's own commitment**; a parent's milestone is context, not that child's promise. Do not blindly shift dates, invent commitments, assign builders, change capacity or send external calendar invitations. Only the Codex general grader reviews both engines; the grader does not perform the work it grades. Existing standing workers/services do not stop when a setup or child issue closes.

Linear owns work identity, projects, milestones and actual execution. The app board renders those and governed plan/acceptance state; a displayed column is not independent delivery/acceptance evidence. Materials owns documents, revisions, usage and review history. Snapshot Questions uses existing Tasks rows and protected reply evidence. Tenant users see only their own questions/delivered answers/history; unsent reply drafts, editing and Send-as-the owner are platform-admin actions, enforced on server/API/MCP tenant projections while retaining any stricter current Send actor restriction. This is separate from client-visible prepared plan Materials. Keep child and parent identities distinct; do not manufacture a new hierarchy, duplicate requests, bulk-move historical cards or fabricate old acknowledgments/approvals.

## Stage boundaries

| Stage | Entry and allowed work | Exit evidence |
|---|---|---|
| New intake | Canonical captured request and complete source context | An actual owned dated commitment, handled by acknowledgment |
| Acknowledged | Owner owes a decision, short/full plan, fix or research by an agreed date | Actual human-approved delivery of the exact plan revision, or verified research/fix delivery |
| Plan delivered | Exact Material revision plus actual human send/presentation receipt | Explicit authorized client assent to that scope/revision; silence is not assent |
| Plan accepted / Queue | Scope accepted; retain existing plan owner | Actual owner pickup and agreed readiness, not acceptance alone |
| In progress / Blocked | Actual execution, or a named real dependency | Verified result/delivery evidence; no status-only proof |
| Delivered | Work delivered; prepare delivery-acceptance package | Human sends package; actual scoped client acceptance moves only affected work Live/Complete |
| Live / Complete | Accepted functioning service or completed asset | Evidence-led outcome/case-study review, never elapsed time/status alone |
| Proven | Accepted outcome/case-study closeout with results against intent | No automatic worker or retirement sweep is established here |

A small fix need not manufacture a plan cycle. Work around a week or more requires a plan and actual acceptance before building. Research may itself be the requested deliverable: prepare its report/PDF, human delivers it, then seek delivery acceptance without a second plan/build cycle. A working Live parent remains Live when a new child ask/fix is needed. Feedback on pending Delivered work returns the affected existing work to In Progress with linked feedback and preserved history; repeated feedback does not create duplicates.

Keep actual historical approvals and legitimate grandfathering. An old parent approval never blesses new child scope or a changed revision. Do not alter historical board placement merely to satisfy a new policy.

## Three distinct document products

1. **Plan:** proposed approach and scoped decisions before building; several plans can belong to one project.
2. **Delivery-acceptance package:** what was delivered, how to use/verify it, known limits and the acceptance request.
3. **Outcome/case-study closeout:** later adoption/usage evidence, results against original intent, process changes, patterns and lessons. Acceptance of this later document is a distinct Proven boundary, not delivery acceptance.

AI prepares the initial plan/package using relevant source context and current Material comments/history. It must not create/promote a Linear project automatically. Use a short issue-linked plan for genuinely small work. Preparation/registration/publication does not establish formal delivery, consume a follow-up slot or advance acceptance. Human review/send remains required for plans and packages. Record the exact revision, recipient/source and actual receipt only after delivery. A Draft label does not guarantee privacy: keep private internal planning and specifically withheld information out of every client-visible field, file or metadata.

Use existing Material comments and relationships, not a new comment system. Read current unresolved comments before revision; address or explicitly disposition them while preserving earlier versions and responses. Link the Material to canonical work and the work back to the exact Material revision where supported. When only a project/plan relation exists, preserve the child identity and revision in the existing issue context too. If a write/link control is unavailable, retain the exact source and report the missing leg; never claim a comment, relation, receipt or acceptance was saved without readback.

## Authority and communication

Read current tenant communication settings, actual source thread, prior replies/receipts and current stop state before acting. Tenant communication profiles are viewable/editable only by platform-level admins; never copy their internal routing/credential references into client snapshots or Materials. Settings describe source routes, existing connections, account/number references, exact user-versus-bot identity and tenant rules; they are not a secret store or permission grant. Resolve source-author and original-thread recipient fields dynamically with existing authorized tools. Do not infer authority from contact IDs, substitute another account or invent destinations/emails.

Explicit stops, denials and user no-share instructions win. Distinguish a real stop from incomplete conservative seed configuration: missing seed fields alone are not a blanket ban when the current source, identity and actual user authorization can be verified. A real unresolved conflict, absent permission or unknown route blocks that action and leaves a useful draft/exact exception. Unrelated incomplete optional source routes do not block safe reading or preparation.

Reply in the original authorized channel/thread, respecting source-specific eyes reactions and current workspace/account rules. Conflicting historical Slack-only versus incoming-text instructions need the actual source-specific decision, not an arbitrary override. Check recent teammate and other-engine actions first. Existing replies, later promises, quiet hours, feedback or stops can suppress a follow-up. Never send a quick Question answer automatically; its human Send/manual-source workflow is separate. Slack Questions use the existing authorized workspace user identity, original-thread reply and supported channel broadcast. Optional Question eyes scanning is not a text acknowledgment or commitment; only the same actor reaction changes after confirmed answer receipt, preserving others and never causing a resend. Verify that the separate Slack Send transport is actually released; reaction polish never blocks core Send.

ACK is an owner commitment to what is owed and by when, not necessarily a full plan or a new message. Reuse an existing truthful commitment; do not send twice to make a label look right. Preserve agreed dates and working-day semantics. Existing next-working-day/two-/three-working-day guidance and specific tenant exceptions are not 24/48/72 elapsed hours, builder availability or a universal urgent completion SLA. Missing calendar/date/owner calls for a decision draft, not an invented promise.

Plan and delivery acceptance use at most two polite nudges: 24 hours and day five after actual human delivery, then private escalation, only within current tenant/user authority. The delivery cadence is the selected implementation default and may be tenant-specific. A subsequent reply/promise or conflict is handled first. Never catch up with a burst, fabricate historical nudges, or treat an uncertain send as retryable because time passed.

## Every run

Check in/out through the existing Scheduled registry and obey current go/no-go. Read recent receipts/actions and canonical work again before mutation. Preserve one stable business operation identity across cooperating engines/retries using the existing available controls; local cursors are not cross-engine send authority. Record real provider/readback evidence and resulting canonical state. An uncertain outcome requires source reconciliation, never a second send/new key. If the current tools cannot coordinate a contested action safely, leave it pending and surface that exact exception; this skill does not depend on unreleased adapters.

Keep run logs in Scheduled. Work context belongs on the existing issue/project; client-visible updates must respect the audience and no-share instructions. Recommendations about queue, milestones, start dates and priorities remain proposals until the responsible person actually agrees. Engineering cycles are initiatives grouping projects, native Cycles are unused, and several ordered Main/Flex projects are permitted. Proven/outcome automation remains unactivated.
