---
name: running-outreach-campaigns
description: The front door for running a cold email campaign through Columnline, from a one-line ask to a loaded, approved campaign. Use when someone says "run a campaign for X", "let's go run a campaign", "set up a campaign", "launch outreach to a group", "new push", "build a list and load it", "refill the campaigns", "we're out of leads", or "nothing is sending". Covers the one upfront approval, sample, full list, campaign, batch record and launch gate, and which Columnline tool does each step.
---

# Running Outreach Campaigns

## In plain English

This is the recipe an AI follows when someone says "let's go run a campaign for X". Start with one plan and spending ceiling, then prepare the sample, full list, draft campaign and batch record. Keep the actual sample, audience, load and batch decisions together where the supported tools allow it. Their required human confirmations remain separate from the final decision to send.

## The shape of a push

- **Push:** one offer, sent to one or more groups at the same time. Recorded as one Outreach **batch**.
- **Campaign:** one per group. Same copy, different list. Three groups (for example mechanical, electrical, architects) means three campaigns in one batch.
- **List:** the people in one group. Saved in Columnline Leads first, so nobody is paid for twice.
- **Goal:** replies that turn into calls and booked meetings. The offer is the easiest possible yes.

## Step 0: Start (no questions yet)

1. `columnline_whoami`. Confirm the person, the workspace (tenant) and that Outreach and Pursuits are enabled.
2. Read the workspace's own campaign rules from Knowledge before planning anything. Search its outbound knowledge base for "campaign rules", "who we target", "offer" and "copy rules". These rules (company size, titles, industries, offer, copy limits, sending limits) are the workspace's, not this skill's. If none exist, say so and ask for them once.
3. Read what is already running: `outreach_batches_read`, then `outreach_campaign_read` for each active campaign. Note leads left, daily sends and **runway** (days of first emails left = untouched leads ÷ daily first-email capacity). A campaign marked active with no untouched leads is the first thing to fix.
4. Check existing leads before buying any: `pursuits_leads` for the target group. Reuse what fits.

## Step 1: One upfront approval

Write one short plan and get one yes. Do not ask five separate questions later. The plan names:

- The groups (one campaign each) and the fit rule for each: company size, titles, industry, area.
- The offer in one sentence, and the copy for each step (see Step 4).
- How the leads will be found, the sample size (10), the full size per group, and the **spending ceiling** in dollars across all tools.
- How deep verification goes (verified email required for saving contact samples; phone optional), which audience checks apply to every included row, and which fit checks are sampled. Separate hard exclusions from useful but optional research.
- What needs a human decision: sample fit, the exact full audience and load confirmation, the batch record, and launch.

A yes to this plan covers sourcing, enrichment and saving up to the ceiling. It does not approve an unseen full audience, replace a tool's required load confirmation, or permit sending. Reuse approvals that actually cover the unchanged decision; do not ask for the same decision twice. If the plan changes (new group, higher spend, different offer), ask again.

## Step 2: Sample, then prove fit

1. Choose the cheapest source for the agreed audience. A mixed provider feed need not contain ten perfect leads. Preserve every raw row and source ID; distinguish obvious wrong fit from missing evidence. Exclude known non-target businesses, duplicates and contradicted identities. Do not broaden the audience merely because discovery was broad.
2. Default to ten raw rows. If the person chooses **broader sourcing followed by filtering**, agree the raw acquisition limit, cost policy, replacement scope and research time limit first. Freeze ten candidates from the filtered stream before detailed fit review; retain the raw count, rejects and reasons so selection is transparent. Do not replace failed members of that frozen sample to inflate its pass rate. A previously failed raw sample stays failed; changing to a filtered-stream test is a recorded method change, not a retroactive pass.
3. Research companies once, using supplied descriptions and estimates first. Use one supported estimate when that meets the brief; do not require independent corroboration of every provider field. Missing phone, LinkedIn, a fresh buying trigger or extra project research does not fail a lead unless the brief makes it required. Stop at the agreed research limit and retain unresolved cases separately. Known wrong fit stays excluded. Required numeric headcount and credible conflicting evidence remain governed by the brief.
4. Show the exact ten-person sample with a one-line fit reason per row, uncertainty, raw-to-filtered yield, actual cost and effort. The default threshold remains eight of ten; for an explicitly planned filter-first method it applies to the frozen filtered sample. If fewer than eight fit, refine once within actual authorization, then stop dependent scaling after a second failure. Do not require every lead to be perfect or call unchecked full-list contacts individually proven.
5. Find/verify work emails for the useful shortlist, then save with `pursuits_source_samples` (`begin → append → complete → get`, at most 25). Keep candidates missing required save fields in private preparation files; do not invent email addresses to satisfy storage. Cheap batch exclusions can run early; deeper sending-history checks may wait until audience preparation. This staging choice never grants send clearance.
6. Inspect the saved source and submit its exact revision with `pursuits_reviews`: `action: submit`, `tenantId`, `kind: sample`, `sourceId`, `expectedRevision`, a UUID `requestId`, and `context: {channel, sessionRef, skill?}`. **Omit `workspace` on submit**; it is a list filter. Preserve the same request UUID only for an identical request after uncertainty, and read the existing review before retrying. `get` uses `reviewId`; saving or automatic review creation is not explicit submission. Read back the review ID/state. Record an actual human approval against that revision without asking the person to repeat an unchanged approval. Submit and approval never send.

## Step 3: Full list

1. Pull the full list for each group, staying under the approved ceiling.
2. Save it with `pursuits_source_runs` (`begin → append → complete → get`, `alreadyAcquired: true`). One run holds **1 to 1,000 people**. For a larger group, save several runs of up to 1,000 each. Use the `partIdempotencyKey` the `begin` call returns; never invent one.
3. If enrichment is part of the plan (for example a casual company name), run it on 10 to 20 first, show the result, fix the prompt, then run the rest. Keep the research that backs each value.
4. Read the saved full audience and its review state. **ready means storage complete, not fit or audience approval.** Preserve individual fit evidence, unchecked records, suppression, prior outreach and active-client/open-Pursuit holds. A sample approval does not clear the full list. Pending, unchecked or unresolved people stay out of a load until the governing review clears them; never count an observed email as fit or clearance.
5. Present the exact eligible audience and exclusions for the full-audience decision required by the discovered action. Record the actual human decision against that revision or hash and read it back. If the supported load preview combines audience approval with loading, its human confirmation may record both; the sourcing-plan yes cannot substitute for it.

## Step 4: Campaign

Copy rules unless the workspace's Knowledge says otherwise:

- Two steps. Day 0 first email; day 2 follow-up with a different angle on the same offer.
- The follow-up has its own subject line.
- One variation only (subject or offer), so the test is clean.
- Short, plain, no em dashes. The ask is a one-word reply.
- Every variable used in the copy exists on every lead, with the exact same key.

Use a discovered, described action or the matching same-role Platform control to create one **draft** or **paused** campaign per group within the agreed plan. Use its supported audience/load path only for the cleared, approved audience. For a batch loader, preserve its exact current approved hash and required review. For `leads_outside_actions`, preview without `confirm`, show the actual audience, exclusions and effect, then wait for the person's explicit yes before calling with the returned confirm word and unchanged arguments. Never answer that confirmation for the person. Read the load receipt and campaign membership back, including counts, variables on three random leads and the next sending window. A saved source batch is not proof of loading.

If no governed create/load action or same-role app control is available, report that exact gap and retain the prepared draft and audience receipts. Do not replace the missing action, a refusal, or a required confirmation with a direct sending-provider API call or internal credential. After an uncertain load, inspect the saved receipt and provider membership through the supported read path. Follow the described action's bounded recovery: `leads_outside_actions` permits at most one further call with the same confirm word and unchanged arguments after that read-back. Never preview again or generate a new retry identity to resolve an uncertain load. If it remains uncertain, stop and report that some people may already have been loaded.

## Step 5: Batch record

Make the batch with `outreach_batch_create`: name, the approach in one line, and every campaign's `platformCampaignId`. **A batch can never be changed or deleted.** Read the name, approach and campaigns back and get a clear yes first. Keep the `request_id` you generated.

## Step 6: Launch gate

Launching sends real email. Before it, show: each campaign, its lead count, the copy, the mailboxes and the first sending time. Launch only on an explicit "launch it" from the person, then read the campaign state back. A review approval, a draft, or a batch is not a launch.

## Step 7: Watch it

- First check after the first sending window: sends happened, bounce rate under 3%, no mailbox paused.
- Keep runway above 7 days. When it drops to 7 or less, start the next push's sample.
- A reply that says yes goes to the reply recipe the workspace uses, fast. Calls are what book the meeting.

## Working efficiently

- Read each unchanged evidence revision once and keep it. Re-read consequential state before a write or after uncertainty; do not repeat research to fill optional fields. Batch company classification and deduplication before paid email enrichment.
- Check a vendor's credit balance once before a paid run and once after, not per contact. Per-contact checks hit hourly limits.
- Run independent groups in parallel.
- Save files and receipts in one working folder per push, named for the push.

## Stop and ask only when

- A step would spend past the approved ceiling.
- The sample fails twice.
- The exact sample/full-audience decision, load preview confirmation or immutable batch needs the person's yes.
- Anything would send email or load leads into a live campaign.
- A tool refuses with a permission error. Report the exact message to the workspace admin; do not work around it.

## Never

- Send, launch, or add people to a live campaign without the explicit go in this conversation.
- Store leads only in the sending tool. Save them in Columnline first.
- Repeat an uncertain write with a new key. Read the saved state, then retry with the same key.

Generated from columnline-ops .claude/skills/running-outreach-campaigns; edit the source.
