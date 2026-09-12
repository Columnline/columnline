---
name: managing-pursuit-materials
description: "Generate and register purposeful sales and client deliverables in Materials, preserving categories, reusable formats, personalized copies, exact revisions, and evidence. Use for one-pagers, proposals, research reports, decks, scripts, plans, and assets supporting leads, pursuits, outreach, or client work, whether for Columnline or a client."
---

# Managing Pursuit Materials

## In plain English

Materials is the home for documents made to move a sales effort or client job forward. A format is a reusable approach. Each personalized document stays linked to that format, while corrections stay in its version history. Sales results come from the existing pipeline; client deliverables can record acceptance and the number of review rounds.

## Start here before generating

1. Resolve **who owns the work**: Columnline selling its own service uses `columnline-ai`; research or sales assets made on behalf of a client use that client's tenant. Identify the purpose, audience, lead/pursuit when known, or a source link to the project/meeting.
2. Discover the Materials read action, list the intended tenant, and find the category and approved format. Read its exact source revision and generation recipe. Do not use a personalized client copy as a general source.
3. Choose the identity once:
   - **Same approach, new recipient:** create a copy with `role=copy`, `formatId`, and the exact approved `sourceRevisionId`.
   - **Correction to that document:** register a new version using its exact `materialId`, preserving its role, format and source revision. Include short change notes.
   - **Different approach:** create a separate format in the same category.
   - **Purpose-built one-off:** standalone is valid. A format is not required.
4. Use the existing generating skill or the format's saved recipe. Preserve a requested layout, pictures and source copy. Research reports use `research_report`; proposals and quotes use `proposal_quote`; call scripts use `call_script`. Native Your Plan meeting agendas remain on the meeting occurrence; only substantive sales scripts or separate deliverables belong here.
5. Inspect the actual rendered asset. Register it as a draft before returning it. Save purpose, audience, relevant links and optional notes. Return the Materials link and exact material/revision IDs. Registration does not create email/calendar activity and does not approve an asset for agents.

Resolve the current approved format and its recipe from Materials.

For client pursuit preparation, discover the approved format and its current recipe in the selected tenant. Follow its audience, evidence, review and registration requirements. Do not assume another tenant uses the same document.

## The human workflow

Materials is the review library. Generate from the conversation, resolve the context,
and register the draft yourself; do not send the user through an upload form to finish
your generation task. The library's **Personalize with assistant** action copies a
request with the approved source; it does not dispatch a job. **Upload an existing copy**
is the manual fallback. Request changes to an existing copy as a new version of that
copy. Return the document and Materials link for review.

After authorized delivery, record the exact revision and confirmed sales identity.
Use existing sending receipts when available. For external email or offline review,
require the user's confirmation or source evidence; then record it through Materials.
Do not ask the user to re-enter tags, version labels or known context. Client acceptance
belongs to the delivered copy, not the reusable master. Manual history controls remain
available for missing evidence, not as the normal workflow.

## Register and record evidence

Discover the Materials write action and use its current schema. Register a reviewed draft with its tenant, source, purpose and audience. Preserve material and source revision identities when creating copies or revisions. Record a send only from confirmed delivery evidence; registration does not send. Record client acceptance only when supported. A new version does not inherit acceptance. Unknown history stays unknown.

## Authenticated MCP

`materials_read`: `action=list`, `get`, or `compare`, with `tenantSlug` and optional filters.
`materials_write`: `register`, `send`, `presented`, `accepted`, or `details`; same
camelCase fields and services as the CLI. Read the material immediately before a
revision or use receipt. Writes require connection write consent and live tenant
permissions; draft creation/format changes require the same approver role as the UI.
There is no MCP approval, win/loss, signing, payment, or sending operation.

## Generation recipes

Use the approved format’s saved generation recipe and tools available in this session. Preserve source links and editable inputs. This skill owns registration and evidence; it does not supply every document generator.

Generated from columnline-ops .claude/skills/managing-pursuit-materials; edit the source.
