# Conversation to saved Your Plan

## Authority and access

Start with `columnline_whoami`. Confirm the signed-in name, Platform role and
`yourPlanRead`/`yourPlanWrite`. Discover the actual tool catalog; a skill grants
no access and a named tool may not be available in a given connection.

The normal shared MCP operations are `your_plan_list`, `your_plan_get`,
`your_plan_save_draft`, `your_plan_publish_revision`, and
`your_plan_publish_update`. The latter two publish client-visible content and
require explicit authorization. `your_plan_get` includes Linear-backed information and, when mirror reads are enabled, `linearSync` freshness. A stale snapshot is context, not proof of current provider state. Never retry an uncertain publish blindly; preserve its receipt and original intent.

**Capability boundaries:** these tools do not, by their names or existence,
provide new-plan creation, lane reordering, meeting editing, acceptance, rejection,
or retirement. Discover a purpose-built tool for the action first. If absent,
use the matching existing Platform control as the same authorized operator, or
the operator's Linear OAuth connection for Linear-owned changes. If neither is
available, return the exact missing action and proposed values. Do not substitute
repo API keys, direct SQL, or owner credentials. Never fake a successful action.

## Writable packet

The live tool schema and returned editor packet are authoritative. Describe the discovered tool before assembling a payload. Read the complete plan immediately before each write.

Use `editor.settings`, `editor.revision`, and `editor.guard`. A complete saved
operator draft takes precedence over the current published copy for continued
authoring; compare its guard/baseline and preserve intentional changes. If a draft
is stale, show the differences and reconcile deliberately before resaving.

| Conversation evidence | Writable field(s) |
|---|---|
| Observed problem, current job and sources | `problemCurrentProcess` |
| Proposed steps, actors, handoffs and exceptions | `targetProcess`; optional `processMap`; map `artifacts` |
| Scope, exclusions, resource needs, opportunity cost, dependencies and risks | `proposedScopePlan` |
| Named job, first useful result, build ending and ongoing service boundary | `workContract` |
| Client inputs, decisions, effort, adoption owner and responsibilities | `clientResponsibilities` |
| Causal hypothesis, business result, confidence, delay and effort | `expectedOutcomeValue` |
| Baseline, target, source, review window and bounded response | `valueMeasures` |
| Defensible monetary model with assumed/measured inputs | `valueEquation`, otherwise `null` |
| Conditions needed for the hypothesis to hold | `assumptions` |
| Existing Linear milestone identities, labels and real timing | `milestones` |
| Observable delivery and closeout tests | `acceptanceCriteria` |
| Decisions about current/future process, scope, outcomes, prototype and delivery | `checkpoints` |
| Exact governed process/prototype/scope/proof artifact links | `artifacts` |
| What proof exists versus what is still needed | `expectedProofStatus` |
| Verified delivery, decision, measurement and operating owners | `owners` |
| Next decision/action, owner and response timing; unresolved readiness gaps | `nextStep` |
| New Work, amendment, small change, urgent rerun and baseline | `planKind`, `basisRevisionId` |

Settings preserve title, linked project/initiative, lane/rank, configured delivery
destination and verified acceptor identity. A draft setting does not move a Linear
project. Use the discovered plan action and read the saved result back.

For each value measure the API requires `label`, `unit`, `baseline`, `target`,
`source`, `measurementWindow`, and `responseWhenMissed`; `current` is optional.
Include the measurement owner in the source/window text and in `owners`.
`responseWhenMissed` names owner, response time, effort limit and next decision.
Do not put invented numbers in missing baseline/target fields. Explicit unknowns
may save as text. An expressly agreed measurement-first commitment can be ready
for that limited scope; an unsupported performance promise cannot. Unknown targets
needed to accept the promised result keep that result not-ready.

New Work requires current-process, future-process, scope, outcomes and delivery
checkpoints; a governed prototype adds its corresponding gate. Do not call a
proposed map accepted. Inline maps retain the actual actor/system/channel names;
keep node labels concise and put expanded explanations in `detail`. Use governed
FigJam/Figma artifacts for richer maps and prototypes. Older deployed versions
may still reject custom lanes: preserve the map and report the required release,
rather than relabeling every person as Client or deleting the process to save.

Keep stable milestone IDs/source IDs. Checkpoint fingerprints, stored source
bindings, acceptance receipts, checksums and publication metadata are server-owned;
never copy them from the raw revision into writable checkpoints. The reader's
editor conversion supplies the writable fields and the server stamps publication.

## Save and review

1. Get the exact plan. Confirm identity, tenant/project match, current revision,
   existing private draft and unresolved drift.
2. Build the complete settings/revision from the editor packet and intentional
   edits; validate the meaning, not only required keys.
3. Call `your_plan_save_draft` with `tenant_id`, `plan_id`,
   `expected_revision_id`, `expected_revision_checksum`, `settings`, `revision`,
   and `change_summary`.
4. Call `your_plan_get` again. Compare `operatorDraft.payload` and returned checksum;
   verify the published revision and existing acceptances are unchanged.
5. Open the actual plan in the Platform and review the private draft through the
   operator editor. The client page continues to show the published agreement.
6. Report the saved draft and unresolved decisions. Publish only when authorized.

A schema error is not permission to weaken validation or replace history. A stale
guard means reload, reconcile, then retry. Do not resubmit an uncertain publish
without reading the resulting revision first. Missing permissions remain missing
permissions; reconnect as the right person, never borrow another person's access.

## Readiness is a business decision

A packet is ready for acceptance when the process is understandable, its outcomes
are measurable or its first measurement step is explicitly agreed, the execution
and resource tradeoffs are feasible, risks/assumptions are visible, and the decision
and ending are specific. A save receipt proves storage only. Mark partial drafts
clearly in the relevant text and next step; do not invent a new readiness field.

Do not expose internal salaries, margins, or sensitive staffing decisions in a
client-visible revision. Put the execution detail in the authorized private Linear
document and publish only the agreed business commitment.
