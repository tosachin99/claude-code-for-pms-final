# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

The user is the new PM for Rook Dispatch (started 24 Aug 2026; Priya left 21 Aug, no overlap). Sources: wiki, Priya's handoff, database (29 Jun–6 Sep), interviews, routing code. "My read" marks inference. Figures are my own counts, not yet checked with Ravi.

### Products and constraints
Rook sells per-responder subscription software to independent masked responders and their handlers, on a monthly release train (4.x).
- **Dispatch:** ranks available responders per callout and pings them in order. Handlers use the web console; responders use the phone app.
- **Supply:** requisitions, maintenance, failure reports, for handlers and quartermasters. It reads the Responder Availability Record that Dispatch writes.
- **Rules:** routing config ships in a release, not at runtime. Cover identities are never stored; never try to work out who a responder is (Security Policy 4.1 is not in the wiki). Interviews hold household details about responders; keep them out of notes.

### People
4.2 comment roles: engineering manager = **Marcus Oyelaran** (Dispatch engineering, first stop); staff engineer = **Wen Li** (built the ranking, undocumented); support lead = **Nadia Hoffmann** (tickets); product designer = **Sofia Marino** (console, phone app, interviews). Not on that thread: **Helen Achebe**, Director of Product and the user's director; **Ravi Menon**, data analyst, owns the weekly numbers (Priya pointed to Marcus; use Ravi).

### Vocabulary
- **Callout** is an incident request; a **ping** offers it to one responder, who takes it, turns it down or misses it (ping wait ran out). Turned down and missed both move the ping on and lower recent acceptance.
- **Ping wait** (also "timeout") is the same for everyone, set per release. **Routing priority** is the ranking score: proximity, capability match, recent acceptance, with availability as a filter.
- **Acceptance rate** (share of pings taken) is the headline metric; **coverage gap** means nobody available had the tags. **Mutual aid** and **shared cover** appear to be one item.

### 4.2 (shipped 12 Aug)
Proximity weight 0.45→0.60, acceptance 0.40→0.25, ping wait 90s→60s; also persistent filters and three defect fixes.
- **Data:** acceptance 76.6% before, 54.3% in the first week, 75.2% on 2–6 Sep; missed 2.3%, 22.9%, 12.4%. Misses jumped on release day, so not mainly seasonal (no prior-year data).
- **Hidden:** Vesper, The Undertow, Farlight and Meteor Mite got about 12 pings a week each before, and 2 combined on 2–6 Sep; none has taken a callout since 19 Aug. 74% of callouts end at the first ping, so low rank means never pinged.
- **Likely cause (my read):** the 60s wait turned slow answers into misses; a miss costs −0.12, a take adds +0.08, and nothing recovers over time. Unproven: the database has no scores or answer times, and the acceptance weight was cut.
- **Tickets:** 147 total, 107 since 12 Aug, 83 open. Quiet phone 30 and gone before answer 15 (all open), filters 14, Supply 26.
- **Interviews vs tickets:** 11 handlers filed 146 tickets and none was interviewed; the four interviewees filed one. Farlight and The Undertow (40 tickets) were not interviewed; Vesper and Meteor Mite (interviewed) filed none. Interviewees understate pings. Only in interviews: Kip's quiet-versus-busy gap and Aunt Dot's wish for handler alerts. Only in tickets: filters, Supply fulfilment, console bugs, admin.
- **Priya's view:** mostly seasonal; filter tickets are noise; don't revert. It's the view of the person who made the call.
- **Open:** Marcus's 14 Aug question (was the change meant for decliners?); the regroup outcome; a written description of routing, left to the user. Next: Wen for live scores, Ravi to verify by responder, Nadia to reach Aunt Dot and Kip. Draft questions for owners exist in chat only.

### Roadmap and gaps
- **Roadmap** (last reviewed 30 Jun, every owner still Priya): Availability Confidence was committed for 4.2 but isn't in the notes. The requisition brief adds approval while handlers say approvals are too slow, and the priority field does nothing. Phone app and shared cover are Q4 exploring. Bulk Callout and audit-log briefs are stale (shipped 4.1, 4.0). Who owns Supply is unknown.
- **Doc vs code:** the glossary lists availability as a routing input, but the code only filters on it. 82 callouts ended with no taker after one ping, unexplained. Helen's "ship this afternoon" conflicts with routing shipping in releases.
- **Missing:** wiki and database stop in early Sept (today 4 Nov, repo has a 13 Oct run); no 4.3 or Q4 roadmap; `06-sidekicks/briefs/` absent.
- **All 147 tickets, my grouping:** quiet phone 30, gone before answer 15, other ping problems 6 (all before 4.2 and closed; the three duplicate-notification tickets fit the 4.2 fix), filters 16, console polish 22, console bugs 10, missing features 10, admin 12, Supply 26.
- **Who files:** four handlers (Desmond Okafor, Linda Pruitt, Simone Fischer, Yusuf Demir) filed 69 of 147 tickets; Aunt Dot, Kip and Halloran filed none.
- **Not yet done:** talk to Linda and Desmond (starved, vocal, not interviewed) and to Aunt Dot and Kip (starved, silent, interviewed).
- **Impact report** is saved at `01-origin-story/4-2-impact-report.md`. The 90s to 60s wait is the strong cause of the missed-ping jump: missed rose in every hour band, ping position and area, and the gap after a miss went 92s to 62s. It is not time of day, position, geography or season.
- **New:** since 4.2, 22% of taken callouts went to a responder outside the area (0% before), and out-of-area pings are missed 30% of the time. No ticket or interview mentions it.
- **Farlight, week by week:** 75 pings before 12 Aug, 11 since; last taken 14 Aug, none since 28 Aug. Linda Pruitt's ticket dates match the log exactly.
- **Confidence (0–95):** ping counts 90, wait as cause 75, score knock-on for the four 45 (needs Wen's score history and answer times), ticket grouping 70, interviews 40.
- **Routing in five steps:** find who's free (`availability.py`), score and rank them (`routing.py`, weights in `config.py`), keep the "said yes lately" score (`history.py`), ask the top person and wait 60s (`offer.py`), move down on no or miss. Six functions (three each in `availability.py` and `offer.py`) are empty placeholders, and the folder was last changed 8 Oct, so it may not match what's live.
- **Code vs pings:** a yes adds 0.08 and a no or miss takes 0.12, so a responder needs 60%+ yes to stop sliding. Before 4.2 all 16 were above that; after, exactly the four fell below (18–29%). Across the 16, yes-rate after vs change in pings correlates 0.94; decline rate before only −0.27. So misses, not declines, hurt.
- **Marcus's 14 Aug question:** the code has one formula and no special case for decliners. Whether the combination was intended is unanswered; the sharper question for Wen is whether a missed ping should cost the same as a "no" once the wait is 60s.
- **Recovery for a quiet responder** (inferred, no real scores): needs about a 19-minute travel edge over a top-score rival (about 40 before 4.2), or everyone above them to decline. At 70% yes it's about 25 pings to get halfway back, roughly two months at 3 a week. Since 26 Aug the four were pinged 8 times, none taken. Fixes (restore 90s, stop counting a miss as a "no", ease scores back, reset the four) each need a release.
- **Module 5 files:** `05-super-speed/brief.md` is a draft one-pager for Helen's request (not a setting; something Kip would notice and a quiet responder would feel). `05-super-speed/prototype.html` is a clickable handler console plus phone, with Linda Pruitt and Kip tabs and a Today vs comeback-path switch. Tested in the in-app browser; the screen states are made up, not real routing.
- **The proposal (for Helen to react to):** after a quiet stretch, the next suitable callout goes to the quiet responder first with a longer wait; the handler's card says so in plain words; a missed ping stops costing the same as a "no", and scores ease back.
- **Still missing before it can be built:** Wen's real scores and answer times; whether the live code matches this copy; one chosen approach and a named owner; per-responder baselines and targets (Ravi); side effects (load on others, a Supply owner); release date and rollback; the text of Policy 4.1. Quiet-stretch length (shown as 5 days) and wait length are open.
- **Meteor Mite in Kip's view** (illustrative, her starting numbers rounded from the pings table): today she isn't asked while The Gale takes the callout; with a 90s comeback wait she takes it at 75s; at 60s the offer expires. The user refers to Meteor Mite as "her". Next: reply to Linda Pruitt, Desmond Okafor, Aunt Dot and Kip; ask Wen whether a miss should cost the same as a "no" at 60s.
