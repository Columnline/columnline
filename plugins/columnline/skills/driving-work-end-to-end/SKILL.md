---
name: driving-work-end-to-end
description: Coordinate Columnline client intake, Snapshot Questions and the existing initiative pipeline. Use for intake desks, acknowledgments, preparing or delivering plans, acceptance, queue coordination, delivery packages, live work, or a pipeline agent. Routes each stage to its focused skill; does not create projects, schedules or send authority from a planning request.
---

# Driving work end to end

## In plain English

Keep each client request in its existing record and give each stage one clear job. Intake captures new work; simple questions wait in Snapshot for a human answer. Shared stage workers prepare and follow up within their current authority, while people approve plans, send documents and decide when building starts. The Pipeline desk keeps dates and calendar context honest.

## Read first

Read [the shared system contract](reference/system.md) on every run. It owns stage boundaries, authority, privacy, evidence and document meanings. Follow the current Scheduled row and read recent actions and receipts from other workers before doing anything. A timer waking is separate from permission to act. Use only tools discovered for the current signed-in identity; missing tools are specific exceptions, never permission to use someone else's credentials.

Keep the canonical tenant, issue, source message/thread and parent project separate. A child ask can have its own plan, revisions and acceptance inside an accepted project. A parent's milestone or approval never substitutes for the child's commitment or scope.

Every worker follows the finish rule its check-in returns (the owner, Nov 3): assume nobody comes back mid-run, take its stage's job all the way to the next human gate in one run, and leave that gate ready (draft saved, date proposed, receipt logged) rather than reporting what could be done. The gates in [the shared system contract](reference/system.md) stay exactly as they are.

## Choose the stage

| Situation | Focused skill | Responsibility |
|---|---|---|
| New source message or annotation | [intaking-client-work](../intaking-client-work/SKILL.md) | Capture, classify and deduplicate only |
| Simple factual question | [handling-snapshot-questions](../handling-snapshot-questions/SKILL.md) | Prepare/check a staff question draft; human Send |
| Unanswered ask needing a dated commitment | [acknowledging-client-work](../acknowledging-client-work/SKILL.md) | Owed decision, plan, fix or research and approved date |
| Acknowledged work needing a plan | [drafting-client-plans](../drafting-client-plans/SKILL.md) | Investigate and prepare; no automatic project promotion |
| Human-sent plan awaiting a decision | [checking-plan-acceptance](../checking-plan-acceptance/SKILL.md) | Exact scoped yes/feedback and bounded follow-up |
| Accepted, awaiting pickup | [coordinating-accepted-work](../coordinating-accepted-work/SKILL.md) | Retain owner; propose priority/cycle/start readiness |
| A builder is executing | [building-accepted-work](../building-accepted-work/SKILL.md) | Actual work, blockers and verified delivery |
| Delivered work needs its document | [drafting-delivery-acceptance](../drafting-delivery-acceptance/SKILL.md) | Prepare delivery-acceptance package for human send |
| Human-sent package awaiting acceptance | [checking-delivery-acceptance](../checking-delivery-acceptance/SKILL.md) | Scoped yes → Live; feedback to affected work |
| Accepted work is live or complete | [operating-accepted-work](../operating-accepted-work/SKILL.md) | Keep functioning parent Live; improvements are child asks/fixes |
| Outcome/case-study review | [closing-proven-work](../closing-proven-work/SKILL.md) | Evidence and document acceptance; no automatic Proven sweep |

Six shared workers own acknowledgment, plan preparation, plan acceptance, accepted queue, delivery-acceptance package preparation and delivery acceptance. Focused skills do not imply extra timers. Questions prep/check drafts and flags; it never answers clients automatically. Internal intake is stopped. Only the Codex general pipeline grader is active; it reviews both engines and does not perform the work it grades.

## Everyday requests

“Put a plan together” means investigate and prepare the appropriate short plan/PDF while retaining the issue. It does not authorize a new Linear project or immediate publication. “Deliver the plan” still requires human review/send and an actual receipt for the exact revision. “They said yes” needs the actual scoped response; it queues work without starting a build. Preparation, publication, delivery, acceptance and outcome proof are separate facts.

An agent that owns one objective on an existing initiative, on a timer, on demand or both, is a **Mission**: read [missions](reference/missions.md) for how every run checks in, loads context, reports and checks out.

Read [command handoffs](reference/commands.md) for these requests and worker briefs when updating an already-authorized routine. The existing Pipeline desk handles dates/calendar only, using each issue's own commitment. It does not acknowledge, plan, chase acceptance, assign builders or move stages. Several ordered Main/Flex projects are allowed; engineering cycles are Linear initiatives grouping projects, with native Cycles unused.

## Source, safety and useful improvement

Tenant communication settings supply source/account/sender and routing context, including bot versus user identity. Resolve exact recipients and threads at runtime. Explicit stops and denials win; incomplete seed settings alone are not a blanket ban on an otherwise verified, authorized action. Resolve the real missing fact instead of guessing a destination or granting new access.

Treat snapshots and client Materials as client-readable. A Draft label is not a privacy boundary. Preserve every specific no-share instruction; exclude private internal planning and user-withheld details from visible text, attachments, metadata and publication. Keep sensitive working notes in an actually authorized internal location.

Read Material comments and revision history before revising. Keep prior versions and acceptance; link the Material and canonical work both ways where current controls support it. State unsupported write/link legs precisely and retain the source evidence. Learn from concrete friction through narrow reviewed changes and regression cases; never silently change approval rules, channel authority, stage meanings or enablement.

Generated from columnline-ops .claude/skills/driving-work-end-to-end; edit the source.
