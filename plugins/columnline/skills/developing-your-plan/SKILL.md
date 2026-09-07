---
name: developing-your-plan
description: Develop a specific Your Plan proposal through a source-grounded the model conversation, then save and review it through the shared Columnline MCP. Use for proposing Work, defining Process/Outcomes/Plan, deciding whether a build is worth its capacity, material plan revisions, client feedback, acceptance preparation, or closeout. Routine field edits and status lookups use the discovered plan tools directly.
---

# Developing Your Plan

## In plain English

This skill helps an operator think through a piece of Work with the model.
The conversation produces a proposal that explains what should change, why it is
worth doing, what it takes, and how the work ends. It saves the proposal in Your
Plan and checks the actual page. A proposal can end in acceptance, revision,
deferral, or a decision not to do it; filling a form is not success.

## One authoring path

The conversation is the main authoring interface. The app is the review surface
and an editor for occasional corrections. Do not build a chat UI or require a
separate slide deck, PDF pair, or copy of the agreement in a repo file.

Use the live Columnline catalog for governed reads and writes. A skill supplies guidance, never permissions. Read the exact plan and its current editor packet before saving.

Use the **shared Columnline MCP** that the teammate and other authorized operators
connect to. Discover its tools, call `columnline_whoami`, and confirm the actual
identity and read/write capabilities. Use `your_plan_list` then `your_plan_get`.
Do not make this workflow depend on a repo `.env`, database key, shell script,
owner credential, or impersonating the owner. Resolve Knowledge access separately
with `using-columnline-knowledge`; lack of Knowledge access is a visible gap.
The shared connection supplies current role-specific instructions.

## Start from the actual Work

1. Identify the tenant, existing Linear project, current plan, and requested
   change. Read the project description AND attached documents. Reuse existing
   records. A lane assignment is not approval of a proposal.
2. Read current plan revisions, drafts, accepted evidence, meetings, linked
   process/prototype artifacts, and the sources for the requested change.
3. Use `using-columnline-knowledge` to read the authorized business context and relevant evidence. Knowledge explains reasoning; live systems own dates, people, and state.
4. Briefly explain the actual problem and proposed outcome in chat. Separate
   known facts, supported estimates, assumptions, and unanswered decisions.
   Ask only what sources and the conversation have not already answered.

## Guide the conversation

Ask a few connected questions at a time, with a recommendation when useful.
Explain which decision an answer changes. Do not dump this entire checklist on
the user, repeat answered questions, or fill every account with the same prose.
Use the actual Work's nouns, handoffs, outputs, constraints, and failure cases.

### Desired change, before drawing the solution

Start with **“What do you want to have happen?”** Establish the observable gap,
who experiences it, what becomes different, and why that difference matters.
Compare the proposed effort with keeping resources on the best current work.
“Do nothing” is an allocation decision, not inactivity. A mandatory repair of an
existing promise is not a discretionary initiative to decline for low ROI.

### Process: can both sides explain the proposed job?

Describe where work enters, how it is handled today, where it stalls, and the
proposed steps through a real finish. Name actors, systems, inputs, outputs,
human decisions, handoffs, exceptions, and manual fallback. Expand a subprocess
when its hidden steps could change scope, ownership, effort, or acceptance.

Create a useful current/future process map when it clarifies the job. Use the canonical
Figma workflow when recurring human interaction needs a prototype. Do not draw
every issue, force the fixed legacy Client/Agent/App lanes onto a richer process,
invent a prototype approval, or redesign an accepted frame in code. Link the
exact reviewable artifact/version and record what is accepted versus proposed.

### Outcomes: does the process make the result plausible?

For each material outcome establish:

- The causal hypothesis: if we change this process, we expect this result, for
  these reasons. Name supporting evidence and uncertainty.
- Baseline, target, unit, evidence source, measurement owner, and review window.
  Separate an early indicator, delivered capability, adoption, and business result.
- What assumptions must hold, including client inputs, volume, access, adoption,
  provider behavior, and data quality when relevant.
- What happens if the measure misses: who responds, within what time, what they
  try, how much additional effort is included, and when to revise, pause, or stop.

Make “reliable,” “better,” “automated,” and “done” observable. A merged PR or an
activity count is not evidence of the business result. Missing baselines become
an explicit measurement step; missing targets remain decisions, never invented
numbers or zero. Label value estimates as estimates and show their basis.

Explain the desired result, confidence of achieving it, time to first useful
value, and client effort. These are decision questions, not a fabricated numeric
Hormozi score. Only use the app's monetary calculation when defensible inputs
exist; it is a different model from the qualitative value equation.

### Plan: is the result worth what success requires?

Reverse-engineer success before declaring the current resources sufficient.
Name scope and exclusions, minimum useful delivery, milestones, people, time,
dependencies, required access, costs, client responsibilities, and risks.
State what current Work loses resources and who can authorize the tradeoff.
Distinguish included work, a proposed scope tradeoff, and work needing a separate
commercial decision. Never invent a price or promise free added scope.

Keep confidential staffing costs and internal allocation detail in the private
Linear execution document. Client-visible Plan content carries the agreed price
or commercial decision, effort required from the client, dates, and consequences.
Have the builder own the feasible execution sequence; do not infer that ownership
from assignment. Keep accepted issues in their existing project and milestone.

### Decision and ending

Read back the proposal in plain words: what changes, what each side owns, first
value, evidence, timing, cost/tradeoff, assumptions, and the decision requested.
Have the decision-maker explain their understanding at material acceptance gates.
Do not repeat an approval already explicit in this session.

Define build completion separately from the business-result observation window.
A finite build ends on its agreed evidence and acceptance. Continuing measurement
has an owner and a review date/window; it does not silently keep the build open.
If operating Work continues, define cadence, monitoring, fallback, service scope,
adoption evidence where needed, and the named operating owner. Use real operating
evidence before placing it in Operating. Otherwise document completion/handoff.

## Save a decision-ready proposal

Read [reference/packet-contract.md](reference/packet-contract.md) before assembling
the writable packet. Preserve existing drafts and unrelated fields. Use fresh
MCP revision guards and **editor.settings / editor.revision**, not the raw
read model. Save a private draft first, then get it again and inspect the actual
page as the intended operator. API-valid is not decision-ready.

If the Work has no plan record yet, create it first: `your_plan_setup_options`
for the tenant, then `your_plan_create` with the chosen lane project, one
tenant-owned destination (or a new `external_destination` link when the Work
has no card), an acceptor seat, and the complete first revision. Creation is
neither publication nor acceptance; the client sees nothing new until a revision
is published. Details in the discovered plan tools § Creating a plan.

If facts are incomplete, save an honest partial draft when the API permits it;
put the exact unresolved questions and their owners in nextStep and the relevant
section. Do not invent identity/destination fields to force a save. If a draft
cannot be saved, report that limitation and preserve the work in the authorized
project document; do not claim a saved Platform proposal.

Publish only after the user explicitly authorizes the reviewed revision. Publishing
is not client acceptance. Acceptance, activation, delivery, adoption, and Operating
are separate claims with separate evidence. Prepare the next exact meeting's
agenda from unresolved decisions and evidence; do not send it or change invitees.

## Respond to feedback

| Event | Action |
|---|---|
| Correction within scope | Amend the private draft, preserve unrelated fields, and read it back. |
| Extra feature/material change | Explain outcome, capacity, date, cost and risk changes. Draft a revision against the accepted baseline; retain the existing agreement until superseded. |
| Awaiting acceptance | Name the decision-maker, question, and response date or explicit date-needed. Do not auto-change Linear status. |
| Revisions requested | Record the feedback against the exact revision. Name Columnline's next action; use the existing revisions-requested flow where available. |
| Proposal declined/deferred | Record the decision, reason and restart condition if applicable. Withdraw only the proposal through a supported action. Never retire accepted service to reject a new revision. |
| Build delivered | Review evidence, complete the required outcome/closeout acceptance, release build capacity, and agree the next owner. |
| Outcome misses | Execute the previously agreed, bounded response; larger work requires a new explicit scope/capacity decision. |

Automatic proposal-to-Linear status synchronization is outside this workflow.
Do not equate unaccepted with waiting on client, or rejected with blocked.
Read [reference/examples.md](reference/examples.md) for the tricky cases.

## Finish with evidence

Return the plan link, saved revision/draft receipt, readiness status, unresolved
decisions and their owners, actual versus proposed Linear changes, and the next
meeting agenda destination. Explicitly separate saved, published, accepted, and
Operating. If the page or tools block completion, name the exact missing action.

The quality test: can the decision-maker explain **what they get, why it should
work, what it costs in resources, how they will know, and when the obligation ends**?

Generated from columnline-ops .claude/skills/developing-your-plan; edit the source.
