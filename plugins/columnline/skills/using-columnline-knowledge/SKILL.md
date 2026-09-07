---
name: using-columnline-knowledge
description: Find authorized Knowledge, follow citations, and check changing facts in their live source. Use for business context, prior decisions, call preparation, and source-backed research.
---

# Using Columnline Knowledge

## In plain English

This is the front door for finding what Columnline knows. It searches the
authorized knowledge base for durable context, then checks the system that owns
anything that can change. It can combine a wiki page, a live Linear issue, an
Attio relationship, a Fathom transcript, and the code without pretending they
all mean the same thing. The answer shows what is current, what is historical,
and what is still uncertain.

## The rule

**Knowledge explains meaning and history. The live owner decides current
state.** Use the smallest set of sources that can answer the question honestly.

| Information needed | Primary owner |
|---|---|
| Durable meaning, history, decisions, policies, patterns, research | Authorized Columnline Knowledge |
| Work status, owner, dates, commitments, approvals, blockers | Linear |
| People, companies, relationships, owners, and deal state | Attio CRM |
| Raw meeting evidence | Fathom or Account Interactions |
| Raw messages and documents | Gmail, Slack, Drive, or the named source system |
| Code, configuration, and deployed behavior | GitHub plus authenticated runtime checks |
| Current balances, invoices, and financial state | The named finance system |

Knowledge may link to the live owner and explain why it changed. Never copy a
live value out of its owner and call the wiki current truth.

## Read workflow

### 1. Frame the question

Name the subject, the requested time horizon, and which parts can change. A
history question may need Knowledge alone. A “current picture” usually needs
Knowledge plus at least one live owner.

### 2. Discover identity and access by capability

Do not assume a server name such as `founder-knowledge` or a connection named
`columnline` (existing `columnline-knowledge` connections also work). Tool prefixes and connection names differ between
the model, OAuth connections, and machine connections, and none of them
grant access. Access is whatever the live identity resolves to on this request.
Connect through the client's own configuration, never a secret checked into the
repo.

1. Find the available tool group that exposes `mcp_whoami`,
   `knowledge_list_bases`, `knowledge_search`, and `knowledge_get`.
2. Call `mcp_whoami` first. It reports who this connection is (a person
   resolved live from their Platform identity, or a machine bound to an
   explicit profile) and the shape of their reach. Read the identity from the
   tool; never infer it from the connection name or the tool prefix.
3. Call `knowledge_list_bases`. Use only the bases it returns for this
   identity, and for each base use only the capabilities it returns on that
   base (read, contribute, propose, direct, and so on). Never assume a base
   exists, and never assume an action a base did not return. A base missing
   from the list has no access, not a base to search anyway. Zero bases means
   zero Knowledge access.
4. Use a Knowledge-base ID for search and get. Internal collection pairings
   are compatibility detail and do not belong in ordinary reasoning.
5. If no Knowledge tool group exists at all, continue with other authorized
   sources and say: **“Columnline Knowledge was not checked because this
   session has no authorized Knowledge connection.”** Do not invent a
   different storage or borrow another person's credential.

Never expose a forbidden tenant or collection name, even while explaining a
denial.

### Connected knowledge for a current workspace

When the task belongs to a specific Pursuits, Sites, or Work context, discover
`knowledge_resolve_context` alongside the read tools. Pass the exact tenant UUID,
module (`pursuits`, `sites`, or `work`), and the current submodule, card, or saved
List when applicable. A connection says where knowledge applies; it never grants
access. All Tenants is not a Knowledge scope: select the relevant tenant first.

Use the returned reader/entry page and active revision. Company context supplies
background. A governing strategy is authoritative only for its explicit purpose.
When a workspace requires a governing strategy, read its complete current source page and preserve the returned receipt. Missing access, conflicting authorities, or partial reads block a claim that the strategy was checked.
Refresh the client's tool catalog when the new resolver has not appeared yet.

Collection scope includes shared links and links from visible cards; a saved
List narrows the card portion. Temporary search and pagination do not change it.
For a general Knowledge question with no workspace scope, keep using the
base-selection workflow below.

### 3. Select before searching

Choose the Knowledge base from the current tenant, client, Work, research lane,
or explicit user request. The server searches the authorized Pages and Facts
behind that base. Prefer maintained Pages in the answer and inspect newer Facts
only for gaps or conflicts.

Legacy internal collection identifiers may still contain `silver` or `gold`.
Treat those as compatibility names only: Facts and Pages are the current words.

Do not run an unscoped search when the question belongs to one known Knowledge
base. Shared research can otherwise outrank the company or client
page that actually owns the context.

### Business Model routing

For offer design, pricing, sales, GTM, monetization, client framing, renewal,
retention, stickiness, or operating-constraint questions, route among the bases
`knowledge_list_bases` actually returned for this identity. The base names below
are search hints, not a promise that a base exists or is authorized; if one is
not in your authorized list, skip it and say so.

1. When a **Business Model** base is authorized, search it first. Prefer
   maintained Pages and inspect Facts only for the evidence behind a
   load-bearing claim.
2. If the question is about Columnline, cross-check the authorized Founder Pages
   that own current doctrine and history, especially `Columnline`, `Operating
   Model`, `Commercial Model`, `Strategy & North Star`, and the relevant client
   or Work Page.
3. Check mutable price, pipeline, ownership, Work state, capacity, and client
   facts in their live owners before presenting them as current.
4. Treat a framework as a lens, not an adopted Columnline decision. Say where
   the framework and current doctrine agree, conflict, or leave a question
   unresolved.

Cross-wiki relationships are links, not copies. Business Model owns the source
framework. Founder or client Knowledge owns the durable application to the
current business. CRM, Linear, finance, code, and runtime still own changing
state.

### Recover the connection before giving up

A Columnline repo session normally reaches Knowledge over a hosted OAuth
connection. Discover it by capability every time; a connection name is at most a
recovery hint, never an authorization shortcut, and never something to hard-code
into reasoning.

If the connection is missing, logged out, or `mcp_whoami` does not resolve:

1. Recheck the connection. In Codex, inspect `codex mcp list` and `codex mcp get
   <name>`; in Claude Code, inspect `/mcp`. Reconnect and sign in with this account
   when asked.
2. Once `mcp_whoami` resolves, call `knowledge_list_bases` again. Access follows
   the signed-in Platform identity on every request, so a fresh login is what
   repairs an expired or logged-out connection.

If `mcp_whoami` resolves a real person or machine but `knowledge_list_bases`
returns nothing, that is the honest state for this identity: it has no entitled
bases. Report it plainly and stop the Knowledge path. Do not widen any
Knowledge-base or page permission to force a result, do not provision a standing
key, and do not borrow another person's credential. If the identity should have
access and does not, that is a bug to report, not a permission to grant
yourself.

### 4. Read the evidence chain

1. Search the selected Pages collection with the user's words.
2. If the result is weak, try at most two useful alternate phrasings: a named
   entity/title and a decision/topic phrase.
3. Inspect retrieval metadata such as `answerBasis`, maintained Pages, newer
   Facts, facts-only results, and conflicts when the tool returns them.
4. Open the best Page with `knowledge_get`. Paginate with `offset` until the
   full relevant page and active revision metadata have been read.
5. Follow citations or `knowledge_get_source` for a load-bearing claim, a
   contradiction, a precise quote, or a user request for proof.
6. Treat a Facts-only answer, dirty Page, missing citation, or revision conflict
   as uncertainty. It is not maintained Page truth yet.

Use source links in the final answer when permitted. Never expose private
payloads, opaque internal ids, or raw authorization errors to a user who does
not need them.

### 5. Check changing truth live

Open only the owners needed for this question. Examples:

- “What is going on with this account?” → Knowledge for history, the work tracker for active commitments, and recent source messages for new promises.
- “Why did we choose the managed Work model?” → Knowledge first; root repo
  doctrine only if the question also asks how sessions must behave.
- “Is this feature live?” → Knowledge may explain intent, but GitHub and an
  authenticated production check decide whether it is deployed and usable.

If sources disagree, prefer the live owner for its field, report the conflict,
and identify which durable Page needs correction.

### 6. Use raw sources when the claim matters

Use Fathom, Account Interactions, Gmail, Slack, Drive, or the cited provider
when the user asks what someone actually said, the Page is contradicted, the
claim affects a commitment, or precision matters.

`knowledge_list_meetings` lists only meetings inside collections granted to the
current connection. An empty result does **not** mean no meeting exists. Fall
back to the authorized Fathom or Account Interactions path.

### 7. Answer in three truth buckets

Use only the buckets the answer needs:

- **Confirmed current:** verified in the live owner during this task.
- **Durable context:** supported by an authorized Page and its citations.
- **Unresolved:** missing, stale, conflicting, or not currently authorized.

Cite each material claim near the sentence it supports. Say which system was
not checked when access or evidence is missing. Never turn an inference into a
confirmed fact.

## Writes are a separate operation

A read request never writes automatically. If the user explicitly asks to save,
teach, correct, retract, or update Knowledge, discover the authorized save action and inspect its schema before acting. Its ordinary path is destination → `knowledge_save` → receipt;
the server owns revisions, idempotency, citations, and internal collection
wiring.

A write is possible only on a base whose `knowledge_list_bases` capabilities
include a write action (contribute, propose, or direct), and only up to the
action that base returned for this identity. Do not attempt a write a base did
not offer; the server decides the ceiling live from the person's Platform role
and denies anything above it, so a save beyond the returned capability fails
closed rather than escalating.

When more than one authorized base could plausibly hold the save, ask which one
before writing rather than guessing a destination. After a write, confirm it
with the receipt and an authenticated `knowledge_get` read-back, not the receipt
alone.

If a read uncovers stale Knowledge but no write was requested, report the exact
gap and proposed destination. Do not silently “help” by changing the wiki.

## Failure behavior

| Failure | Required behavior |
|---|---|
| No Knowledge tools | Continue with other sources; disclose Knowledge was not checked |
| No authorized resources | Stop the Knowledge path; reveal no hidden metadata |
| Expired or revoked connection | Treat as no access; do not rely on an earlier grant |
| Empty or weak search | Try two scoped alternate queries, then report the gap |
| Newer Facts or conflict | Check the live owner and label the answer unresolved until reconciled |
| Empty meeting list | Check Fathom or Account Interactions if meeting evidence matters |
| Raw source unavailable | Use the cited Page if sufficient; otherwise label the claim unverified |
| Live owner unavailable | Give historical context only and say current state was not verified |

## Finish check

- The search was scoped to an authorized Knowledge base.
- The relevant Page was read, not inferred from a result snippet.
- Material citations or source links were followed when needed.
- Mutable claims came from their live owner.
- Missing access and contradictions are visible in the answer.
- No Knowledge write occurred unless the user explicitly requested it and the
  authorized tool governed it.


Generated from columnline-ops .claude/skills/using-columnline-knowledge; edit the source.
