# Client meeting agendas in Your Plan

The recipe for getting a recurring client check-in ready in one sitting. the owner opens the meeting in Your Plan and walks the agenda top to bottom. Every line he might want to show links to the real thing: the Slack message, the email, the PDF, the process map, or the Platform card.

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
| Slack message or thread reply | Use the permalink returned by the connected Slack read action under the signed-in person's own access. |
| PDF or file posted in Slack | Read the message (`conversations.history` with `latest=oldest=ts`, or `conversations.replies` for a thread reply) and use `files[].permalink`. |
| Gmail thread | `https://mail.google.com/mail/?authuser=<address>#all/thread-f:<decimal thread id>`. The Gmail search tool returns this as `viewUrl`. |
| Figma or FigJam node | `https://www.figma.com/board/<fileKey>?node-id=<a-b>` (design files use `/design/`). |
| Platform card | `https://columnline.com/app?prime=app&card=<cardId>`. |
| Google Doc tab | Append `?tab=t.<tabId>` so it opens on the right meeting. |

DM links only open for the people in that DM. That is fine: the owner is the one clicking.

## Find the meeting

Check identity with `columnline_whoami`, then discover and describe `your_plan_meetings` when it is available. Read the intended tenant and occurrence, its current published agenda, newest draft and recap. Use the returned meeting identity, time and source links. If the action is absent, open the meeting in Your Plan under the same person's existing access. Missing access is a gap to report, never a reason to go around the connection or act as another person.

An occurrence with no agenda of its own shows the series' last agenda in the app, labeled "From an earlier meeting in the series". That is an old agenda. Always give today's occurrence its own.

**Start from last time.** A meeting in a series returns `lastTime`: the meeting it follows, with its agenda, recap and open items. For the build team's standups that is the previous weekday (same people, same time), not last week's same weekday. Open the new agenda with `nextAgendaStarter` (last time's open items as unchecked boxes), then write the rest. In the app, Prepare agenda starts with the same section, and the meeting shows a Last time panel.

## Save the agenda

Discover and describe `your_plan_meeting_agenda_save`. It publishes by default, so set `publish: false` for preparation or a requested private draft. Publish only when the owner explicitly asks for the agenda to be up. Read the occurrence immediately before saving, preserve its current content and revision requirements, and use only the fields in the live schema. If the action is absent, use the matching Platform control as the same authorized operator. If neither route is available, keep the draft local and report that it was not saved.

Read back the saved draft or published revision and inspect its actual state. Another session may have changed it; read again and merge on a conflict rather than overwriting it. After an uncertain write, read the saved occurrence before retrying.

After saving, open `/app?workspace=your-plan&tenantId=<tenant>&planSection=meetings&planView=plan&meetingView=list&meeting=<occurrenceId>` and check the agenda renders with working links.

## Comments on the agenda and recap

People comment on a meeting's agenda or recap in the app, and `your_plan_meetings` returns them as `comments` on each meeting (who, when, which one). Read them before you write the next agenda and answer or fold in what they raise. To reply or flag something, discover and describe `your_plan_meeting_comment` (tenant, occurrence, `agenda` or `recap`, body). It saves under your name and shows to everyone who can open the meeting, the client's people too on a client's meeting, so never put pricing, renewal or internal notes in it. Change the agenda itself with `your_plan_meeting_agenda_save`, not with a comment. Each meeting's `fullScreenUrl` opens it full screen; that is the link to send the team.

## Where the content comes from

- **Progress:** the client's Slack since the last meeting through the connected person's own access, sent email, Linear issues moved to Done or Shipped, and PDFs the owner posted.
- **New today:** a fresh sweep of the client's Slack and email since the last sweep, minus anything already answered.
- **Walkthrough numbers:** the issue's evidence comments and the delivered PDFs. Never recompute a number live in the agenda that disagrees with a PDF the client already has.
- Client-specific prep rules and any shared agenda document come from that client's authorized Knowledge and meeting records.
