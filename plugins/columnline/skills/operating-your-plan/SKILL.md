---
name: operating-your-plan
description: Operate and edit Columnline Your Plan across its Linear-backed project truth and Platform-backed plan content. Use when the teammate or another operator asks Codex to change a client plan, process map, outcomes, plan copy, owners, milestones, lane order, meetings, proof, acceptance, or lifecycle state; or asks what in Linear will appear in Your Plan.
---

# Operating Your Plan

## In plain English

Your Plan is one client view fed by two systems. Linear decides which Work appears, where it sits, and when its milestones are due. The Platform holds the client-facing promise, process maps, outcomes, acceptance, updates, and meetings. This skill helps Codex make the requested change in the right place, then check both systems so the teammate does not have to know the plumbing.

## Proposal development

For a new proposal, an unclear outcome, a material revision, or acceptance/closeout
planning, use [`developing-your-plan`](../developing-your-plan/SKILL.md) for the
conversation and decision quality. This skill remains the execution layer. Routine
field edits and status lookups do not require a full planning interview.

## Start here

Use the live connection and the same-role Platform or Linear controls. Repo-only implementation, provisioning, and publication steps belong to an internal operator with the approved repo workflow.

Do not make a write just because this skill loaded. First explain the current truth and the exact proposed change. A request to inspect, explain, or audit is read-only.

## Which system owns the change

| Change | Source of truth | Normal operating path |
|---|---|---|
| Linked Work project, Customer, team | Linear | Use the authorized Linear controls; never relink across Customers by guess |
| Main, Flex, Operating, or Queue position and order | Linear project labels and project order | the authorized Linear project position control, then read back the saved position |
| Project priority | Linear | Always `No priority`; issue priority is the service clock |
| Milestone name and target date | Linear | Use the Platform milestone control when available because it writes through and reads Linear back; otherwise use the guarded Linear workflow |
| Plan title, acceptor, displayed owners | Platform | Open **Manage plan**, save a private draft or publish a revision |
| Delivery destination | Platform | Set at creation (`your_plan_create`, optionally creating the external record in the same call). There is no editor for changing it on an existing plan yet; stop and report instead of silently preserving or directly changing it |
| Problem, target process, scope, responsibilities, assumptions, criteria, checkpoints | Platform revision | Open **Manage plan**; preserve unrelated fields |
| Process-map links and stage labels | Platform revision artifacts | Open **Manage plan → Structured packet fields → artifacts**; preserve every unrelated artifact |
| Outcomes, baseline, target, current, source, window, response when missed | Platform revision | Open **Manage plan**; publish a new revision if client-facing truth changes |
| Status, proof, next step | Platform update | Use the matching publish-update control |
| Meeting occurrence, series, agenda, recap, recording or transcript source, scratchpad | Platform Meetings | Edit the exact occurrence or series and re-open it after save |
| Acceptance, correction, pause, retire, restore, completion | Platform lifecycle record | Use the named governed action; never edit a receipt or accepted revision in place |

Linear is execution truth. The Platform is promise and evidence truth. Do not copy one system over the other when they disagree; stop, report the difference, and fix the authoritative source.

## the teammate workflow

### 1. Connect Codex once

Open https://columnline.com/mcp/connect while signed into the Platform. Follow the Codex setup steps, sign in with the same Platform account, and choose Allow saving when editing is intended.

No database key, Linear API key, or 1Password access belongs on the teammate's computer. Those credentials remain server-side.

Start every new Codex setup with:

> Check my Columnline access, then list Your Plan. Tell me the signed-in name, Platform role, and whether editing is on.

The expected result is the intended signed-in operator’s own identity and live role. Confirm the returned plan read/write capabilities match the task; never require another teammate’s name or credentials. If the identity or role is wrong, stop. If writing is off, reconnect and check **Allow saving**.

### 2. Read before editing

Use `your_plan_list` to find the exact tenant and plan. Then call `your_plan_get` immediately before every write. The returned revision ID and checksum are the safety seal: the save is refused if someone changed the plan after it was read.

The plan read includes Linear-backed lane, order, status, and milestone data. When mirror reads are enabled, this comes from the last verified saved copy. Inspect `linearSync`: `ready` means complete recent coverage; `stale` means saved information with delayed or incomplete verification; `waiting` means initialization is incomplete. Reading the plan does not force a Linear refresh. If the request is to change the Linear project itself—its lane, Customer, team, or order—use Linear's own UI or OAuth connection. The repo `plan-audit` command remains an internal privileged fallback; it is not the teammate's setup path.

A timeout is not proof that an edit failed. Keep the original operation key. For a pending milestone or roster change, use the app **Check change** control or `your_plan_operation_get`. Do not submit the same intent with a new key. Report an operator-required receipt instead of attempting a broad undo. Meetings remains available independently of plan-source freshness.

### 3. State the edit before making it

Name:

- the client and Work project;
- what will change;
- whether Linear or the Platform owns it;
- whether it is a private draft, a published client revision, or a lifecycle action;
- what read-back will prove success.

If the request changes the client promise, priority order, final acceptance, or irreversible lifecycle state and the user has not clearly approved that exact change, ask first.

### 4. Make the narrow change

For lane/order changes, use the authorized Linear controls and a human position. Repo-only fallback commands belong to an internal operator.

For Platform content, call `your_plan_save_draft` first. Use `editor.settings` and `editor.revision` from `your_plan_get`, or continue the complete saved `operatorDraft.payload` after checking its baseline. Never copy raw `plan.revision` server metadata into a write. Resolve `editor.issues` with real answers; schema readiness is not acceptance readiness. Change only the requested fields and preserve everything else. Use `your_plan_publish_revision` only after the draft is reviewed and the user explicitly asks to publish. Use `your_plan_publish_update` for a status, proof, or next-step update. Always report the returned saved read-back.

**Creating a plan.** There is no create screen in the app, by design. A Linear project inside the Your Plan lanes that has no plan record is created through the shared MCP in two calls: `your_plan_setup_options` with the tenant id returns the tenant's lane projects (each with `hasPlan`), its cards, its configured external delivery records, and its seats; then `your_plan_create` takes the chosen `linearProjectId`, one tenant-owned destination, an acceptor seat, and the complete first revision in the same shape `your_plan_save_draft` accepts. When the Work has no card yet, pass `external_destination` (an `https://` link such as the Linear project or a shared folder) with `destinationKind: "other"` and the record is created in the same call. The tool reads the new plan back; creation is neither publication nor acceptance. The Linear project itself, its Customer, team, milestone, and lane label are still set in Linear first, or the create is refused with the reason.

The shared MCP does not yet expose lane, meeting, or lifecycle actions. Discover the live catalog; use the matching Platform control as the same authorized operator or their Linear OAuth connection when an action is absent. Never require repo credentials or borrow the owner identity. Report an unavailable action honestly.

The browser at `https://columnline.com/app?workspace=your-plan` remains the visual review surface. It is not required to get credentials or make the structured edit.

When Codex has browser control, it may operate the existing controls for the teammate. If browser control is unavailable, give the teammate the exact field and value to paste; do not replace the governed action with a direct database write.

### 5. Process maps

New Your Plan maps use clear, expanded, stage-level SVGs by default. Make as many current or future maps as the process needs. Do not squeeze the entire process into one unreadable strip.

Prepare a readable process map, then have an authorized internal operator publish its reviewed file through the repo workflow. Use the verified durable URL in the artifact record. This package carries no media-bucket credential or publishing script.

If the authorized publisher rejects the file type, report the exact failure to the internal operator responsible for publication. Do not change storage policy from this package or disguise the file as another type.

Each Platform artifact uses this shape:

```json
{
  "kind": "process_map",
  "provider": "configured_external",
  "stage": "current",
  "label": "Stage 2 — Operate",
  "href": "https://PUBLIC-HTTPS-SOURCE/stage-2-operate.svg"
}
```

Use `stage: "future"` for future-state maps. The source must be a durable HTTPS `.svg`, `.png`, `.jpg`, `.jpeg`, or `.webp` URL that the intended client can open. Preserve all existing artifacts that were not part of the request. Preview the published revision in Your Plan; a working source link alone is not proof.

### 6. Read both systems back

Call `your_plan_get` again and confirm the changed field, revision number or draft checksum. Its Linear-backed fields must still show the expected lane, order, status, and milestones. If the change was made directly in Linear, read that project back there too. Re-open the exact Your Plan page for a visual preview. For a publish, verify the new revision and confirm the prior accepted revision still exists unchanged.

Report these as separate facts: edited, draft saved, published, Linear reconciled, deployed, the teammate-tested, client-enabled, client-accepted, and Operating. One does not imply another.

## Copy-paste prompt for the teammate

> Use `$operating-your-plan` to update Your Plan for **[client] / [Work project]**. First use the `columnline` connection to check my identity and editing access. Then read the complete current plan, including its live Linear-backed lane and milestones. I want to **[describe the change]**. Tell me which system owns it. Save a private draft first, preserve every unrelated field and every accepted revision, and show me the read-back. Publish only if I explicitly approve it. Do not merge or deploy code.

## Stop conditions

Stop and explain the mismatch instead of guessing when:

- the Work project has zero or multiple Your Plan labels;
- the Customer, team, tenant, or linked project does not match;
- more than one active Platform plan points to the same project;
- a delivery destination change is requested before a governed destination picker exists;
- a map source is private to the operator or does not preview for the intended client;
- the requested edit would alter an accepted revision in place;
- the Platform reports a stale revision or partial Linear failure.

Report a real failure with its source evidence so the source skill can be corrected.

Generated from columnline-ops .claude/skills/operating-your-plan; edit the source.
