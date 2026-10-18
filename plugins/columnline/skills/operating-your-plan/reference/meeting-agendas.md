# Client meeting agendas in Your Plan

The recipe for getting a recurring client check-in ready in one pass. the owner opens the meeting in Your Plan and walks the agenda top to bottom. Every line he might want to show links to the real thing: the Slack message, the email, the PDF, the process map, or the Platform card.

Proven on the REA weekly sync, 2026-09-28.

## The shape the owner wants

Thirty minutes, time boxes that add up, one line per point:

1. **Header.** Meeting time in Mountain and the client's zone, the Meet link, the shared agenda doc if the client keeps one, a one-line purpose, and a **Reports to open** row listing every PDF delivered since the last meeting.
2. **Last week's progress (about 5 min).** What got done, grouped by area (websites, applications, vendor follow-through, outreach and growth). Each line ends with its links: `[PDF]`, `[Summary]`, `[Details]`, `[Orion email]`, `[Open the library]`.
3. **Walkthrough (about 10 min).** The one process the owner wants to talk through. Open with the current and new process map links side by side, then the numbers in "out of every 100" form, then the plan, the goal and the first read date.
4. **Ads and outreach (about 8 min).** Paid results, what to fix before adding budget, sending infrastructure, and any test.
5. **Decisions (about 3 min).** A table: decision, person to confirm, evidence for the next check.
6. **New today and next steps (about 4 min).** Every ask the client sent since the last sweep. One line each: the ask, the next step, and a link to the message it came from.

Write it for the client: plain sentences, no apologies, no em dashes, no internal ticket numbers, no prospect or resident names. Numbers carry their window ("last 30 days"). Say what was delivered, not how hard it was.

## Collect the links first

Build a link table before writing a word. Every progress line and every new ask needs one.

| Thing | How to get a clickable link |
|---|---|
| Slack message or thread reply | `chat.getPermalink` with `channel` and `message_ts`, using the tenant's user token. It returns the thread-aware URL. |
| PDF or file posted in Slack | Read the message (`conversations.history` with `latest=oldest=ts`, or `conversations.replies` for a thread reply) and use `files[].permalink`. |
| Gmail thread | `https://mail.google.com/mail/?authuser=<address>#all/thread-f:<decimal thread id>`. The Gmail search tool returns this as `viewUrl`. |
| Figma or FigJam node | `https://www.figma.com/board/<fileKey>?node-id=<a-b>` (design files use `/design/`). |
| Platform card | `https://columnline.com/app?prime=app&card=<cardId>`. |
| Google Doc tab | Append `?tab=t.<tabId>` so it opens on the right meeting. |

DM links only open for the people in that DM. That is fine: the owner is the one clicking.

## Find the meeting

```sql
select id from columnline.tenants where slug = '<tenant-slug>';
select id, title, provider_series_id from columnline.engagement_plan_meeting_series where tenant_id = '<tenant>';
select id, starts_at, agenda_revision_id from columnline.engagement_plan_meeting_occurrences
 where series_id = '<series>' and starts_at::date = '<yyyy-mm-dd>';
```

`provider_series_id` is `primary:<Google Calendar recurring event id>`, so the calendar event ID finds the series directly. Use a read-only database connection supplied by the internal operator.

An occurrence with no agenda of its own shows the series' last agenda in the app. That is last week's agenda. Always give today's occurrence its own.

## Save the agenda

The shared MCP has no meeting tools yet. The Platform routes do the governed write. They need a signed-in platform admin, so call them with `fetch` from a columnline.com tab in the in-app browser (the owner signs in once; the session persists).

- **Private draft** (client cannot see it): `POST /api/engagement-plans/meetings/drafts` with `{tenantId, occurrenceId, kind: "agenda", markdown}`. Returns `state: "operator_draft"`.
- **Publish to the client**: `PUT /api/engagement-plans/meetings/<occurrenceId>?tenantId=<tenant>` with `{kind: "agenda", markdown}`. Returns the new `revisionId`. Publishing again replaces the agenda; history is kept.

Publish only when the owner asks for the agenda to be up. Before publishing, read the occurrence's current `agenda_revision_id` and its markdown. Another session may have published in the meantime; build on it rather than over it.

After saving, open `/app?workspace=your-plan&tenantId=<tenant>&planSection=meetings&planView=plan&meetingView=list&meeting=<occurrenceId>` and check the agenda renders with working links.

## Where the content comes from

- **Progress:** the client's Slack since the last meeting (user-token search `after:<date>`, messages from the owner), sent email, Linear issues moved to Done or Shipped, and PDFs the owner posted.
- **New today:** a fresh sweep of the client's Slack and email since the last sweep, minus anything already answered.
- **Walkthrough numbers:** the issue's evidence comments and the delivered PDFs. Never recompute a number live in the agenda that disagrees with a PDF the client already has.
- Client-specific prep rules (for example REA's shared Google Doc agenda) live in that client's check-in skill.
