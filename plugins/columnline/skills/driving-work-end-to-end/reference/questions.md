# Snapshot Questions

Simple questions use the existing Tasks list `questions` on Columnline's own tenant, filtered by `fields.clientTenantId` for the client. They do not become Linear issues, project cards or acceptance tasks merely because they need research. Intake captures/deduplicates; the Questions prep/check worker prepares drafts and flags; the human decides and sends.

## Visibility and actor boundaries

Tenant users may see **their own questions and delivered answers/history** through a tenant-isolated projection. Unsent reply drafts, editing and Send-as-the owner are **platform-admin actions**. Platform-admin status alone does not expand the existing stricter Send actor restriction: retain that restriction until explicitly changed, and use the existing authorized workspace user identity.

Enforce these boundaries on the server, API and MCP—not only by hiding UI controls. Resolve tenant scope from current authenticated access; never return raw cross-tenant Tasks rows, unsent draft fields, internal planning or connection references to tenant users. Preserve exact source/receipt history without exposing staff-only delivery controls. This is distinct from permission for client-visible prepared plan Materials: that permission does not make Question reply drafts public. The Questions engineer owns release/verification of these surfaces; this instruction is not proof that a pending projection/transport is live.

## Canonical fields

Read the actual source thread and current list before creating a row. If a teammate already answered the question, do not create a duplicate open question or send another answer. For an existing stale row, retain the actual reply evidence and flag it for the supported human completion control. Use status `open`, a plain title naming who and the gist, and these exact fields:

| Field | Meaning |
|---|---|
| `clientTenantId` | Exact owning client tenant UUID; not legacy `tenantId` |
| `clientName` | Client name |
| `who` | Actual sender name |
| `message` | Verbatim question or contiguous excerpt; not legacy `question` |
| `draft` | Sourced proposed answer; not legacy `holdingLine` |
| `source` | Actual Quo, Gmail, Slack, Call or other source |
| `sourceHref` | Original message/thread link |
| `receivedAt` | Actual ISO source time |
| `related` | Relevant existing issue/project links |

Slack preserves verified workspace/team, channel, source-message and original-thread root identities separately in the current supported source fields. Read the actual schema/record rather than guessing field names or collapsing channel/message/thread IDs.

Quo requires actual `sourceMessageId` and `sourceConversationId`; Gmail requires actual `sourceMessageId` and `sourceThreadId`. Resolve the live account, line/contact and exact original message/thread through the existing authorized source tool. Never guess IDs from a search URL, substitute the newest message or use a phone/contact ID as consent. Preserve duplicates as one canonical row and retain source/edit history. Do not overwrite a human-edited draft with a sweep's first take. A saved `answer` takes precedence even when empty: an empty answer means it was cleared, never permission to resurrect `draft` or `holdingLine`.

## Native Questions tools and shared service

Native Questions register/read/update/send operations are being implemented separately over the **same UI Questions service**, not another store or send engine. Discover their actual released names and schemas; do not invent names or claim availability from this skill. Prefer those guarded operations when available. Capture/draft operations preserve canonical row/source identity; Send requires the human's exact reviewed answer and the same approval, concurrency, protected receipt and uncertain-outcome safeguards as the UI.

A human may approve/send through the supported UI or an explicitly authorized native Questions operation. Questions prep/check never sends automatically. Generic Tasks may capture/enrich open Questions; they cannot set/remove completion fields or answered state, or reopen/retarget a human-confirmed answer. Notes, ordering and archive/restore preserve recorded completion. General Tasks is a capture/compatibility route, not a substitute for guarded Send: changing task status or protected fields must never fake approval, answer delivery or completion. If a native operation is missing, state that exact capability gap and retain the existing safe UI/source workflow.

## Prepare, send and complete

Investigate enough to draft an honest answer and distinguish facts, assumptions and missing checks. Keep private planning and specifically withheld information out of the client-facing answer. Save only the draft/flags in the existing staff Questions workflow, not as internal notes in client-visible snapshot Markdown.

For supported app sources, the human edits and presses **Send**, or explicitly approves the exact answer through the released guarded native Questions operation. The app sends the exact approved reply and retains its protected provider result. Approval, attempted submission, sent and delivered are separate states. An unknown/pending send stays pending reconciliation; a worker never resets approval or repeats it with a new key.

For **Slack Send**, the contract is the owner existing authorized **user identity in that workspace**, not a bot fallback: one reply in the actual original thread, broadcast to the channel where supported. This transport is being implemented separately; verify the released app capability before claiming Send is live for Slack. Missing support uses the actual manual-source path, never a different sender/channel.

An optional eyes reaction is authorized while scanning a genuine Question. After the actual confirmed answer-send receipt, change only that actor's eyes to a check mark. Preserve all other actors' reactions. Reaction polish is optional: its failure must neither block core Send nor resend an already-sent answer. A reaction is not a text acknowledgment, answer, new commitment or acceptance.

For a source without supported app sending, the human replies in that actual source. Where **Mark answered** is available, record only the real source-qualified reply evidence through that human control. Manual completion requires the human to confirm they answered the actual question/decision, not merely acknowledged it. It records a human report; source-qualified links bind conversation, not provider-verified authorship, answer content or delivery. An existing app-send intent cannot be cleared manually. Calls have a recording for context, not a reply destination: choose the actual agreed answer conversation. A reported answer without valid source evidence remains unverified/flagged; never fabricate a link or silently substitute email, Slack or another line. Unsupported completion controls are a precise delivery-surface gap, not permission for a worker to mark success.

Questions prep/check may read and draft, detect a real reply, link evidence and flag stale/conflicting rows. It does not send client answers, mark answered on the human's behalf or alter provider state. Follow current app source rules for manual completion; do not assume an arbitrary HTTPS link establishes the right source/thread.

**Turn into ask** is a deliberate human decision through the existing UI/workflow. Preserve question/source identity and reuse the correct ask. A Question answer itself needs no PDF, project or fake acknowledgment/build cycle.
