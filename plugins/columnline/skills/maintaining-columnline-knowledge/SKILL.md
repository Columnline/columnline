---
name: maintaining-columnline-knowledge
description: >-
  Route durable facts, decisions, corrections, source files, and wiki changes
  to the right authorized Columnline knowledge base without duplicating live
  CRM, Linear, finance, code, or memory truth. the model MUST LOAD this
  whenever a user says
  remember this, save this, capture this, add this to the wiki, update or
  correct the knowledge base, we decided, from now on, this replaces the old
  rule, preserve this file or voice note, which wiki does this belong in, or
  wants a founder, teammate, client, research, pattern, or platform wiki to
  learn something. Also use when a teammate wants to contribute to a shared
  wiki or when maintaining a wiki purpose manifest. Uses the real authorized
  Agent Console curator and returns a truthful receipt; never invents a second
  knowledge store or treats session memory as company truth. For designing a
  new knowledge system, involve its authorized administrator. For read-only context
  questions, use using-columnline-knowledge.
---

# Maintaining Columnline Knowledge

## In plain English

This is the traffic cop for information worth keeping. It decides whether the
new information belongs in the CRM, Linear, a wiki, the code repo, or nowhere
permanent. When a wiki is the right home, it calls the authenticated Knowledge
MCP's simple save tool so the write has permissions, sources, history, and a
receipt. It works through the same authenticated connection across supported AI clients.

## The outcome

A person should be able to say “we decided this,” “remember this,” or “update
the wiki” without understanding collections, revisions, or ingestion. The
session still has to preserve three truths:

1. One system owns each changing value.
2. Each person acts under their own permissions.
3. AI-written knowledge goes through the real Knowledge agent, not a hidden
   side path.

This skill operates an existing knowledge base. To design or provision a new one, identify the needed sources and audience and involve the authorized administrator. This package does not provision infrastructure.

## Discover the current save action

Start with `using-columnline` to verify the signed-in identity and discover the
current Knowledge save action. Describe its schema and use the write runner
when the action is not directly loaded. The `knowledge_save` names below are
action examples, not a requirement that every tool be initially visible.
Apply the returned destination capabilities and saving consent before writing.

## First decide whether anything should be saved

Persist the input when it is likely to matter beyond this conversation:

- a confirmed decision, correction, policy, definition, or durable fact;
- research or a reusable pattern with a named audience;
- a source file, recording, or message that establishes something important;
- a standing instruction or repeatable way of working;
- a change that would mislead the next person if it were lost.

Do not persist casual brainstorming, a one-off drafting preference, or a fact
the user explicitly says not to save. An idea or hypothesis may enter an
observation layer, but it must not silently become curated truth.

## Route truth to its owner

One event can create links in several systems, but only one system owns the
changing value.

| Information | Authoritative home | What the wiki may hold |
|---|---|---|
| People, companies, contact fields, relationships, relationship owner, deal stage | The tenant's CRM (Attio for Columnline today) | Durable interpretation, history, and links; never a shadow contact or pipeline record |
| Work, owners, status, due dates, commitments, approvals, blockers | Linear | Durable rationale, lessons, and links; never a shadow task board |
| Code, schemas, configuration, and deployed behavior | GitHub plus the verified runtime | Architecture explanations and links; never a claim that unverified code is live |
| Invoices, payroll, balances, and financial state | QuickBooks, bank, or the named finance system | Policy, definitions, and analysis; never copied balances as current truth |
| Exact email, Slack, meeting, document, image, or recording | Its source system or the wiki's admitted source custody | Citations and derived Facts subject to the source's access boundary |
| Durable decisions, policies, patterns, research, definitions, and reference context | The authorized wiki named by its purpose manifest | Primary home |
| How an agent or automation performs repeatable work | A repo skill or protected Agent configuration | Human explanation only; the wiki cannot change runtime behavior |
| Temporary continuity or a personal conversational preference | Session or user memory | Nothing shared unless the person explicitly promotes it |

Existing Account Operating Context documents remain authoritative until their
owner explicitly migrates them. Do not move or duplicate them merely because a
new wiki exists.

### When one statement affects two homes

Update the live owner first or in the same operation, then add only the durable
context to the wiki.

Example: “the teammate owns the weekly client one-pager now.” Linear owns the Work
owner. The wiki may record why the operating model changed and link to the Work,
but it must not become the place that future sessions read for the current
assignee.

## Choose the wiki without spraying

Only consider knowledge bases the current identity is allowed to discover.
Never reveal a forbidden wiki's name, page count, or contents.

Choose in this order:

1. The user explicitly names the wiki or page.
2. The current tenant and named client, Work, research lane, or product context
   identify one authorized wiki.
3. One authorized purpose manifest clearly admits the input.
4. Otherwise ask one short question: “Should this go in Founder, Platform,
   Pattern Library, or the client wiki?” Offer only destinations the current
   identity can actually use.

Never write the same teaching to several wikis “just in case.” Cross-wiki
relationships are links, not copies. Read
[the wiki manifest contract](reference/wiki-manifest.md) when selecting or
maintaining a manifest.

## Classify the input before invoking the agent

| Input | Default treatment |
|---|---|
| Confirmed human fact or decision | Call `knowledge_save` with capture intent. It becomes durable and searchable immediately; Page curation may happen later. |
| Idea, hypothesis, rumor, or unresolved contradiction | Fact/observation only until confirmed; label uncertainty and provenance |
| Correction or retraction | Name the page and call `knowledge_save`. The server preserves history and performs the revision check. |
| Exact page plus exact user-authored replacement text | Manual edit path is allowed if the user's grant has that write target; preserve the returned revision receipt |
| AI-authored synthesis or “fit this into the wiki” | Governed proposal or the manifest's real curator Agent; never bypass revision, citation, or approval rules |
| New page, merge, rename, delete, or hierarchy change | Structure proposal and approval; never silently reshape the wiki |
| “From now on,” “always,” “never,” or a recurring behavior rule | Standing instruction on the responsible Agent, not a knowledge fact |
| A better way to perform an existing workflow | Skill or protected Agent instruction proposal, not a wiki fact |
| File, voice note, email, meeting, or image | Preserve the source according to the manifest's admission/source policy, then derive cited Facts |

Sources, Facts, and Pages are the current vocabulary. Older collection ids,
tools, and migrations may still contain `bronze`, `silver`, or `gold`; treat
those as compatibility names, not the words used in new guidance. A knowledge
base may use one collection or the full staged pattern. Follow its manifest and
preserve whatever lineage it requires.

## Use the real write path

### Over MCP from any the model session

the owner standing rule: **company operating knowledge — processes, SOPs,
decisions, current states, ideas — is recorded in the Columnline knowledge
base through its MCP connection.** Not crammed into Linear, not written as
repo markdown, not minted as a skill nobody needed. Pure work and
implementation detail stays in Linear; that split is the whole test.

The ordinary mechanics are deliberately short:

1. **Identify the authorized destination.** Use `knowledge_list_bases` only
   when the user's words or the session do not already identify one. If the
   connection has exactly one valid destination, use it. Never reveal a hidden
   tenant or base.
2. **Call `knowledge_save` once.** Send the teaching or requested change plus
   the base or page name the user supplied. Add source links and `as_of` when
   they exist. Use capture for a confirmed teaching, propose for uncertain or
   major semantic changes, and direct for exact user-authored page content when
   the surfaced capability permits it. Do not manufacture collection IDs, a
   request key, a revision ID, a full replacement page for a small teaching,
   processing-policy wiring, curator runs, canary checks, or maintenance jobs.
3. **Report the receipt.** Say Saved, Proposed, Needs a destination, Needs
   review, or Not authorized. Include only the base, saved fact or page,
   revision/proposal identifier, and safe link the receipt returns.

`needs_destination` is not a reason to investigate. Present only the allowed
choices returned by the tool. `needs_merge` means another writer changed the
page; show the current revision and ask for the intended merge. Exact request
replay is handled by the server.

The Agent Console conversation path below remains fully valid — it is the
same door with a chat interface. This section exists so a coding session
never has an excuse to write company knowledge anywhere else.

### Inside an Agent Console conversation

Use the tools the server provides; the server, not the model, decides authority:

- durable taught fact: `capture_learning_signal`;
- correction or retraction: `rollback_learning` or the target's revision-safe
  page tool;
- standing behavior: `set_standing_instruction`;
- workflow method: `propose_skill_edit`;
- semantic wiki maintenance: `read_knowledge_page` then
  `update_knowledge_page` with its expected revision;
- structural change: `propose_knowledge_structure_change`.

### From the model outside the Console

1. Identify the authorized destination, using `knowledge_list_bases` when
   needed.
2. Call `knowledge_save` with the teaching, optional base/page hint, source
   links, `as_of`, and intent.
3. Report the returned receipt. If no authenticated write path exists, say
   **not saved**. Do not query the database directly, borrow the owner token, or
   claim success.

Use a proposal for AI judgment about a major merge, delete, hierarchy change,
or real semantic conflict. Scheduled Extractor/Organizer/Writer machinery is
an operator concern for bases that deliberately use it; it is never part of an
ordinary save conversation.

Do not route every wiki through the Librarian. The manifest names the curator
for that particular knowledge base.

## Team and service identities

- Each teammate authorizes their own connection. Never use the owner credential
  to make a teammate's write appear to be the owner.
- A member with direct authority may publish according to the collection's
  write policy.
- A contractor or propose-only member creates a pending proposal.
- An outsider, unverified sender, or service without write authority contributes
  an observation at most.
- A downstream automation uses a separate read-only service identity scoped to
  only the Pages it needs.
- Private raw Sources are never exposed through a Page or Fact grant.

The live decision is the intersection of the current identity, tenant
membership, collection/page grant, Agent binding, requested action, and expiry.
A token's old scope is not evidence that access still exists.

## Receipt required

After an ordinary Knowledge save, report:

- disposition: Saved, Proposed, Needs a destination, Needs review, or Not authorized;
- Knowledge base and page, captured fact, or proposal;
- revision/proposal identifier and safe link;
- the one next action only when blocked.

If those fields are unavailable, say exactly what was and was not proven. A
model response, local file, green test, or HTTP success alone is not a saved
knowledge result.

## Safety checks before finishing

- The selected wiki admits this material and the current identity may act.
- The live system still owns changing operational state.
- The source's access boundary did not widen in Facts or Pages.
- A major AI-authored revision was based on the current page.
- Concurrent edits use revision checks rather than last-write-wins.
- Structural changes wait for the required approval.
- The response includes a real receipt or says not saved.

## Read first

Use [Using Columnline Knowledge](../using-columnline-knowledge/SKILL.md) when the task requires existing context before a save.

Generated from columnline-ops .claude/skills/maintaining-columnline-knowledge; edit the source.
