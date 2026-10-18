---
name: running-outreach-campaigns
description: The front door for running a cold email campaign through Columnline, from a one-line ask to a loaded, approved campaign. Use when someone says "run a campaign for X", "let's go run a campaign", "set up a campaign", "launch outreach to <group>", "new push", "build a list and load it", "refill the campaigns", "we're out of leads", or "nothing is sending". Covers the one upfront approval, sample, full list, campaign, batch record and launch gate, and which Columnline tool does each step.
---

# Running Outreach Campaigns

## In plain English

This is the recipe an AI follows when someone says "let's go run a campaign for X". It turns that one sentence into a plan the person approves once, a small sample of leads to check, a full list saved in Columnline, a campaign with the leads loaded, and a batch record of the push. It stops twice for a human: once to approve the whole plan and its spending ceiling, and once before anything is actually sent. Everything in between it does on its own.

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
- How deep verification goes (verified email required; phone optional).
- What stays manual: the sample check, and the launch.

A yes to this plan covers sourcing, enrichment and saving up to the ceiling. It never covers sending. If the plan changes (new group, higher spend, different offer), ask again.

## Step 2: Sample, then prove fit

1. Pull 10 per group with the cheapest source that fits.
2. Save them with `pursuits_source_samples` (`begin → append → complete → get`). This tool holds **at most 25 people**. It is only for samples.
3. Prove the fit to the person: for each of the 10, one line on why it matches the rule. Count matches. If fewer than 8 of 10 fit, change the search (usually narrower titles or size) and pull a new sample. Do not scale a bad sample.
4. Submit the sample for review with `pursuits_reviews` and read back its review id and state. A "looks good" in chat is recorded as the approval; it does not run anything by itself.

## Step 3: Full list

1. Pull the full list for each group, staying under the approved ceiling.
2. Save it with `pursuits_source_runs` (`begin → append → complete → get`, `alreadyAcquired: true`). One run holds **1 to 1,000 people**. For a larger group, save several runs of up to 1,000 each. Use the `partIdempotencyKey` the `begin` call returns; never invent one.
3. If enrichment is part of the plan (for example a casual company name), run it on 10 to 20 first, show the result, fix the prompt, then run the rest. Keep the research that backs each value.

## Step 4: Campaign

Copy rules unless the workspace's Knowledge says otherwise:

- Two steps. Day 0 first email; day 2 follow-up with a different angle on the same offer.
- The follow-up has its own subject line.
- One variation only (subject or offer), so the test is clean.
- Short, plain, no em dashes. The ask is a one-word reply.
- Every variable used in the copy exists on every lead, with the exact same key.

Create one campaign per group as a **draft** or **paused** campaign, with every healthy mailbox attached and the daily limit at full capacity. Load the saved leads into it. Read the campaign back and confirm the lead count, variables filled on three random leads, and the next sending window.

If discovery returns no tool for creating a campaign or loading leads, do that one step in the connected sending tool through its API with the workspace's own credentials, then read the result back through `outreach_campaign_read`. Say plainly which step was done outside Columnline.

## Step 5: Batch record

Make the batch with `outreach_batch_create`: name, the approach in one line, and every campaign's `platformCampaignId`. **A batch can never be changed or deleted.** Read the name, approach and campaigns back and get a clear yes first. Keep the `request_id` you generated.

## Step 6: Launch gate

Launching sends real email. Before it, show: each campaign, its lead count, the copy, the mailboxes and the first sending time. Launch only on an explicit "launch it" from the person, then read the campaign state back. A review approval, a draft, or a batch is not a launch.

## Step 7: Watch it

- First check after the first sending window: sends happened, bounce rate under 3%, no mailbox paused.
- Keep runway above 7 days. When it drops to 7 or less, start the next push's sample.
- A reply that says yes goes to the reply recipe the workspace uses, fast. Calls are what book the meeting.

## Working efficiently

- Read each record once and keep what you learned. Do not re-read the same lead or campaign to check a value you already have.
- Check a vendor's credit balance once before a paid run and once after, not per contact. Per-contact checks hit hourly limits.
- Run independent groups in parallel.
- Save files and receipts in one working folder per push, named for the push.

## Stop and ask only when

- A step would spend past the approved ceiling.
- The sample fails twice.
- Anything would send email, load leads into a live campaign, or create a batch.
- A tool refuses with a permission error. Report the exact message to the workspace admin; do not work around it.

## Never

- Send, launch, or add people to a live campaign without the explicit go in this conversation.
- Store leads only in the sending tool. Save them in Columnline first.
- Repeat an uncertain write with a new key. Read the saved state, then retry with the same key.

Generated from columnline-ops .claude/skills/running-outreach-campaigns; edit the source.
