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
