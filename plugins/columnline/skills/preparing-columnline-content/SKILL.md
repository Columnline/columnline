---
name: preparing-columnline-content
description: Prepare or revise Columnline Content using the tenant’s approved strategy, formats and review process. Use for content ideas, social drafts, articles, review queues or publishing status.
---

# Preparing Columnline Content

## In plain English

Prepare or revise Columnline Content using the tenant’s approved strategy, formats and review process. This follows the work your account can access and shows what the evidence actually proves.

## Workflow

Discover the tenant's Content tools with `using-columnline`. Read the destination, current item, revision, supported actions and approval state. Before drafting, retrieve the complete current governing strategy and approved format through authorized Knowledge and Materials. Follow citations to the actual source. A partial search excerpt does not prove the strategy was read.

Use that tenant's intended audience, claims, tone, channel and required evidence. If approved direction is missing or contradictory, make the narrow gap clear and prepare only work that does not depend on guessing it. Never take client-specific material from the public plugin or another tenant.

Preserve the item identity, linked destinations and source revision when revising. Discover the current create/update/submit schema rather than guessing a payload. Show or save the requested draft under the existing review process. Human approval, any clinical approval required by this tenant, scheduling and publication each retain their own gate; access to a preparation tool grants none of them.

Posts made in one run can be filed together as a batch, with a name, a reason and a kind (organic or paid). Organic and paid are two kinds of the same content, not two systems. A batch does not approve, schedule or publish anything by itself; each post is still approved one at a time. A post can also carry a saved proposed day. Through the Columnline tools: reading organic batches works where Ads is on for a workspace (`content_batches_read` lists batch rows, never a batch's posts, and never a batch of ads). Making a batch and filing a post into one are not available yet: both are refused in plain words and nothing is created, so send a post without `batch_id` and `proposed_on`. The content workspace's own staging script is the path that will file a batch per run, once its held patch is applied. Read the current schema and use them only if it lists them.

In the app, Content is its own area in the left menu on the new layout. Its tabs are becoming Ideas, Calendar, Batches, Posts and Media as the new layout rolls out; Calendar is what the Posts tab used to be, and Posts is a plain list. Ads tools, where a workspace has them, only read saved campaigns, ad sets and ads and their daily numbers. Nothing in Columnline creates, changes, starts or stops an ad or a budget on the ad platform. An approval of ads or of a spend change is a record of who said yes; a person still makes the change in the ad platform.

If the user explicitly requests publishing and the authorized tool supports it, read the current revision and required approvals before executing. Verify the exact destination and publication receipt afterward. Approval is not publication, and calendar removal is not removal of a live post. For paired destinations, verify each requested result independently. On an uncertain external result, read back before considering a retry.

Generated from columnline-ops .claude/skills/preparing-columnline-content; edit the source.
