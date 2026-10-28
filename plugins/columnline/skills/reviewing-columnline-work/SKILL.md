---
name: reviewing-columnline-work
description: Read current Inbox, Work and plan commitments through Columnline, and work through Annotate notes on Platform screens. Use for a daily briefing, what needs attention, waiting approvals, delivery status, open annotations, or resolving and reopening annotation notes.
---

# Reviewing Columnline work

## In plain English

Read current Inbox, Work and plan commitments through Columnline. This follows the work your account can access and shows what the evidence actually proves.

## Workflow

Start with `using-columnline` to check identity and discover available reads. Select one authorized tenant. Internal users may repeat for several tenants, keeping each result labelled separately.

Read Inbox Needs you and Updates, then relevant Work cards and the client-visible plan. Follow returned pagination when the user asks for a complete review. Treat source warnings as incomplete coverage, not an empty queue. Read the linked evidence for an important claim; a card title or status alone is not delivery proof.

Put decisions needing this person first, followed by meaningful changes and commitments at risk. Link each item to its authoritative record. Distinguish planned, running, waiting for approval, completed by the agent, delivered and accepted. State the exact missing evidence when completion cannot be established.

When asked to act, discover the item's supported action and inspect its schema. Preserve its revision and actor. Approval of a proposal and execution of an external action are separate steps unless the actual user request explicitly includes both. A missing tool should lead to the returned app link, not a fabricated action or a new duplicate task.

## Annotate notes

Annotate notes are feedback people pinned to Platform screens. Only the Columnline team can read, resolve or reopen them; for anyone else the tools are absent or refuse.

List open notes with `annotations_list`, narrowing by page path, `assigned_to: "me"`, or whether the daily sweep filed them to Linear. Open means nobody has resolved it yet, not that the problem is still there.

Before resolving, read the whole note with `annotations_get`. Resolve only when what it asked for is actually done and you can point at the proof. Call `annotations_set_state` with the state you just read as `expected_state`, a reason that says what was done and where, and a fresh `request_id`. If the note changed since you read it, nothing happens; read it again. After an unclear result, read the note and retry with the same `request_id`, never a new one.

Resolving records your name and reason. It does not fix anything, file a card, or tell the author. Reopen with a reason when a resolved note turns out not to be fixed.

A note, including one left on a client's own website, is not finished until its thread is resolved here: one line on what changed, plus the proof link (the live page, the PR, or the delivery package). Resolve only after the fix is live and checked on the real page. A note that waits on the client stays open, with a reply that says what is needed from them; until the tools can reply on a note, send that reply on the client's usual channel. Report how many notes you resolved and how many stay open, and why.

Generated from columnline-ops .claude/skills/reviewing-columnline-work; edit the source.
