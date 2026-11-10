# Mission agents

A **Mission** is one objective an agent owns on an existing initiative: an ask, a project, or an ongoing operating
job. It is a row in the Columnline Scheduled list with a `mission` block. Timer runs and on-demand runs read the same
instructions, context and receipts, so a run started by hand at 3pm knows what the 7am run did.

Read [system.md](system.md) first. Everything there still holds. A Mission adds no authority.

## The two kinds

- **Finite.** Stops when its objective is shown done, with evidence. Example: "Every REA website form gets a reply
  in under five minutes, measured for two weeks."
- **Ongoing.** Keeps operating after a milestone, and improves within the same objective and permissions. Example:
  "Five or six qualified prospect meetings a week; then raise their quality." That example is not permission to
  launch outbound or contact anyone.

Mission state (stopped, active, completed) is separate from the initiative's board stage. A setup, milestone or
Proven display on the board never stops a standing service. A real stop or cancellation of the initiative does: it
wins, and the Mission's owner stops the Mission. Plan approval, delivery acceptance and every other pipeline gate
still apply. Never move a board stage because a Mission ran.

## Where things live

| What | Where |
| --- | --- |
| Objective, plan, decisions, lessons, progress | The initiative itself. Project: project updates (`initiative_post`) are the run report. Ask: the issue and its comments. Never force an ask into a new project. |
| Current-state summary | One Linear document on the initiative, saved as the Mission's `context_url`. Rewrite it; never append forever. |
| Run receipts | The Mission's Scheduled row (`mission_check_out`). Never post a run log as a Linear comment. |
| Reusable lessons | Promoted deliberately at a review or at the Proven/case-study step: a skill, repo guidance, or Knowledge (`maintaining-columnline-knowledge`). There is no Mission knowledge base. |
| On/off switch | The Mission's state, `active` or `stopped`. Only its owner switches it (`mission_set_state`). It starts stopped. |

## Every run, in order

1. **Check in.** `mission_check_in` with the Mission id, the trigger (`scheduled` for a timer, `api` for on demand)
   and a `work_key`. Use one key per unit of business work, the same whichever trigger starts it: the day and slot
   ("2026-11-03 am") for both a timer and a hand-started run covering that slot. If `go` is false, stop: either the
   Mission is not active, or that key already has a receipt and another run owns it. Never retry a check in to get
   a different answer; read the receipt with `mission_get` and `run_id`. Keep the `run_id` it returns.
2. **Load context, smallest first.** Stop reading as soon as you know the next step.
   1. The current-state summary (`context_url`).
   2. Unresolved feedback: comments on the last few project updates or on the ask, plus open notes on its screens.
      Every piece of feedback is either answered in this run's report or carried forward by name. Never drop one.
   3. The last few receipts from `mission_check_in`. Do not redo what they did.
   4. Deeper history only by link, only when the summary points you there.
   `initiative_get` returns 2 and the stage's next step in one call.
3. **Do the next step**, using native tools and records: Signals, Batches and Pursuits, Outreach drafts, Materials,
   AnyMail Finder verification, Content. Never build a parallel record. A started job is not a finished job, and a
   finished job is not a verified outcome. Wait for the job, then QA the result.
4. **Report on the initiative.** One `initiative_post` (project) or comment (ask) when something changed. See the
   standard below. Skip it on a quiet run.
5. **Refresh the summary** when the picture changed: objective, where it stands, what is next, open feedback.
6. **Check out.** `mission_check_out` with `run_id`, a one-line summary, `report_url` (the update or comment from
   step 4; on a quiet run, the current-state summary), and a result of `progress`, `blocked`, `milestone` or
   `achieved`. `achieved` needs evidence links and ends a finite Mission. On an ongoing Mission use `milestone`; it
   keeps running. Every admitted run checks out, even one that stopped early (`blocked`), or the next run is held.

**On demand:** `mission_run` with a `work_key` wakes the owner's existing background worker, which then follows the
same steps. A key with a receipt is never fired again. It returns a `jobId`; if the outcome is unclear, pass that
`jobId` as `run_id` to `mission_get` to read the dispatch's saved state before doing anything else. Only the
Mission's owner can read it, and the worker's own status updates can never change the saved request.

## The report standard

- **Real numbers, with their period and a comparison.** "11 qualified meetings, Oct 27 to Nov 2, up from 6 the week
  before", with a link to the source.
- **Measured or estimated, said out loud.** An estimate is labelled as one. Missing is never zero.
- **A picture when it helps.** A chart of the trend, attached with `initiative_post`'s `picture`. Label both axes and
  the period. Good subjects: qualified meetings, cost per customer, SEO and AI-search results, quality trends.
- **Plain words.** Clients can read project updates. No ticket codes, tool names or internal prices.

## Never

- A Mission, its feedback, or a subgoal an agent writes never widens permission to spend, send, deploy or change
  access. Standing authority that already exists for an operating job still holds, and runs do not ask again for
  it. Any new action, new recipient or larger amount needs its own real approval first.
- Never create a token, credential or new standing access while setting up or running a Mission. That is a separate,
  explicit approval.
- A run never starts, pauses or deletes a timer, and never switches its own Mission on. Timer changes happen only
  in the move below, by a person, with the owner's yes.
- Never claim a Mission achieved from a status, a label or a finished job alone.

## Moving an old goal or agent workspace onto a Mission

One record at a time, never in bulk, with the owner's yes for each:

1. **Inventory it.** Owner, timer id and engine, whether the timer still fires, its last real run, the initiative it
   serves, its links and history.
2. **Turn the old timer off and let it drain.** With the owner's yes, switch the timer off in its own engine, then
   wait until its last run has checked out. Never move on while the old timer can still fire: the old prompt and the
   Mission must never cover the same work, in any slot.
3. **Clear the registry row.** Archive the old Scheduled row for that timer. This only edits the list. A Mission
   cannot bind a timer while an unarchived legacy row holds it.
4. **Register the Mission** on that same initiative, with that timer in `schedule`. It starts stopped. Put the
   standing rules in `authority` and the current-state summary in `context_url` (no more `workspace_get`).
5. **Prove one run.** Switch it on, run it once with `mission_run`, then read the receipt and the report.
6. **Repoint the timer** to the Mission's prompt (from `mission_register`) and switch it back on, with the owner's
   yes. Only now does the timer drive the Mission.
7. Archive only the legacy workspace the person approved for that move. Keep its history and links.

Nothing starts or stops silently. The register key and contract are fixed once saved; a changed objective is a new
Mission with a new key. **First-release limit:** a timer stays bound to the first Mission that claimed it, even after
that Mission completes or stops. Give a new objective its own timer; moving a timer between Missions is not built yet.
