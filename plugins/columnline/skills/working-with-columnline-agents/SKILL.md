---
name: working-with-columnline-agents
description: Read agent status and collaborate through authorized Columnline actions. Use for agent progress, starting a supported job, reviewing output, human approvals or correcting an agent result.
---

# Working with Columnline agents

## In plain English

Read agent status and collaborate through authorized Columnline actions. This follows the work your account can access and shows what the evidence actually proves.

## Workflow

Discover available agent tools and choose the tenant with `using-columnline`. Client interaction may be disabled even when an agent or Work card is visible. Use only returned capabilities; a skill cannot enable a disabled workflow.

Read the agent's observed state and source freshness. Distinguish a live observation, an old snapshot, a queued request, an active run and a completed result. Never infer health from an agent's name or a saved Live label. Follow the associated Work and output evidence for the job's actual outcome.

When the user asks the agent to do work, use the authorized conversation/start action if available. Include the concrete task, intended result and relevant source references. Keep the chosen tenant, agent and conversation fixed. Reuse the returned session and run identities; do not start another conversation merely because a response is slow. Read status before retrying an uncertain submission.

For a correction, identify the specific output and what is wrong, preserve its source, and use a discovered feedback or message action. Do not claim the agent learned permanently unless its saved record proves that. Protected role instructions and permissions cannot be rewritten through conversation.

Read a pending approval's exact action, recipient or destination and revision before acting on a user's decision. Approval remains personal and scoped to that action. Report the resulting receipt and any remaining execution step. If interaction is unavailable, return the authorized app link or the precise missing capability; do not call raw operator controls.

Generated from columnline-ops .claude/skills/working-with-columnline-agents; edit the source.
