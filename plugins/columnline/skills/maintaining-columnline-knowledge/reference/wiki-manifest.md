# Wiki Purpose Manifest

Use this reference when selecting an existing wiki or establishing the routing
contract for a new one. A manifest describes why the wiki exists. It is not an
access token and cannot grant permissions.

## Storage rule

Keep machine-routing fields in the Knowledge collection configuration when the
platform supports them. Keep a human-readable, revisioned `Wiki Manifest` page
inside the wiki. The server's current grants and Agent bindings remain the
security authority if either copy drifts.

Do not hardcode collection IDs, tokens, or credentials into a repo skill. Resolve
live identities through the authorized Console/MCP connection.

## Template

```yaml
identity:
  name: "<human-readable wiki name>"
  tenant: "<tenant slug or id resolved live>"
  knowledge_base: "<stable knowledge-base identity>"
  owner: "<human steward>"
  curator_agent: "<real Agent Console slug>"

purpose:
  jobs_supported:
    - "<recurring question, decision, or job this improves>"
  out_of_scope:
    - "<what this wiki must not become>"
  routing_signals:
    - "<topics, projects, clients, regions, or explicit phrases>"

audience:
  humans:
    - "<role or named group>"
  agents:
    - "<explicitly bound Agent>"
  service_identities:
    - "<separate read-only automation identity, if any>"

authority:
  live_systems:
    crm: "<people and relationship truth>"
    work: "<Linear or other Work system>"
    code: "<code host and verified runtime>"
    finance: "<finance system>"
  source_precedence:
    - "<source that wins on conflict>"

admission:
  accepts:
    - "<durable facts, sources, or decisions>"
  rejects:
    - "<spam, unsupported claims, unrelated material>"
  uncertain_material: "observation_only | review_required"

layers:
  bronze:
    enabled: false
    custody: "<encrypted/source storage when enabled>"
    mcp_access: "never"
  silver:
    collection: "<resolved live>"
    audience: "<who may read observations>"
  gold:
    collection: "<resolved live>"
    audience: "<who may read curated pages>"
    write_policy: "read_only | propose | direct"

structure:
  charter_page: "<Wiki Charter page>"
  map_page: "<Wiki Map page>"
  page_types:
    - "<decision, account, pattern, research, policy, etc.>"
  new_structure_requires_approval: true

curation:
  confirmed_human_teach: "<direct or propose>"
  ai_synthesis: "curator_agent_run"
  contradiction_policy: "<retain both, flag, adjudicate>"
  citation_policy: "<required source precision>"

freshness:
  review_cadence: "<cadence or event trigger>"
  expires_or_supersedes: "<rule>"
  stale_signal: "<how failure becomes visible>"

security:
  discoverability: "authorized identities only"
  default_human_access: "none"
  default_service_access: "none"
  page_scoping: "<if used>"
  forbidden_content:
    - "credentials"
    - "Bronze through MCP"

evaluation:
  representative_questions:
    - "<question the wiki must answer with citations>"
  required_denials:
    - "<identity and path that must fail closed>"
  write_proof: "<fresh teaching to revision and receipt>"

stewardship:
  owner: "<human>"
  failure_queue: "<where stale, blocked, or conflicting items surface>"
  curator_schedule: "<visible Agent schedule, if any>"
```

## Selection rule

Compare the input with `purpose.routing_signals`, `admission`, and `authority`.
The manifest with the most specific authorized fit wins. If two fits are equally
strong and neither is explicitly named, ask once. Do not use audience breadth as
a tiebreaker; a broader wiki is not a safer default.

## Manifest acceptance

A manifest is usable when:

- its owner and real curator Agent exist;
- its Silver/Gold collections resolve live;
- its source and write policies match the live bindings;
- an allowed identity can answer one representative question;
- a denied identity cannot discover or retrieve the same material;
- one controlled teaching produces the stated receipt and revision;
- no line in the manifest claims access the server does not enforce.
