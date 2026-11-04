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

The user is the new PM for Rook Dispatch, started Mon 24 Aug 2026, no overlap with Priya (left 21 Aug).
Sources: Rook wiki, Priya's handoff, Rook database (29 Jun–6 Sep 2026), and part of the routing code (`routing.py`, `config.py`, `history.py`). **Interviews not yet read.** "My read" marks inference.

### Products
Rook sells subscription software, priced per active responder, to independent masked responders and their handlers. Monthly release train (4.x).
- **Rook Dispatch:** ranks available responders for a callout and pings them in order. Handlers use the web console; responders use the phone app.
- **Rook Supply:** requisitions, maintenance and failure reports, for handlers and quartermasters. It reads the Responder Availability Record, which Dispatch writes, so Dispatch changes reach Supply unannounced.
- **Constraints:** routing config ships in a release, not at runtime. Cover identities are never stored; never try to work out who a responder is. Read Security Policy 4.1 before touching responder records (not found in the wiki).

### People (4.2 comment roles mapped)
| 4.2 comment role | Person | Location | Go to them for |
|---|---|---|---|
| Engineering manager | Marcus Oyelaran | Site Aleph | Dispatch engineering; first stop when unsure |
| Staff engineer | Wen Li | Berlin | How ranking works; built it, undocumented |
| Support lead | Nadia Hoffmann | Berlin | Tickets, 4.2 theme split |
| Product designer | Sofia Marino | Site Aleph | Console, phone app, September interviews |
| Not on thread: Director of Product | Helen Achebe | Site Aleph | The user's director; roadmap, commitments |
| Not on thread: Data Analyst | Ravi Menon | Singapore | Weekly acceptance numbers |

Priya said to get numbers from Marcus, but the directory says Ravi owns them. Use Ravi; Marcus offered only a rough pull.

### Vocabulary
- **Callout:** request to attend an incident. **Ping:** a callout offered to one responder.
- **Taken / turned down / missed:** the ping outcomes. Missed means the ping wait ran out. Turned down and missed both move the ping on and lower recent acceptance.
- **Ping wait** (also "ping timeout"): same for everyone, set in the release.
- **Routing priority:** ranking score from proximity (travel time), availability, capability match, recent acceptance.
- **Acceptance rate:** share of pings taken; headline metric, reported weekly. **Time-to-accept:** median seconds to taken.
- **Coverage gap:** nobody available had the required tags, so nobody *could* go. Not the same as low acceptance.
- **Mutual aid** (glossary) and **Shared cover** (roadmap) share a definition; apparently one item.

### Where things stand: 4.2 (shipped 12 Aug)
Proximity weight 0.45→0.60, acceptance 0.40→0.25, ping wait 90s→60s. Also persistent filters and three defect fixes. Figures below are direct counts, not yet checked with Ravi.
- **Headline:** acceptance 76.6% before, 54.3% on 12–18 Aug, 75.2% on 2–6 Sep. Missed 2.3%, then 22.9%, then 12.4%. Callouts with no taker: 5.5% before, 11.1% after, 5.5% in the last week.
- **Not mainly seasonal:** misses jumped on release day; the week of 3 Aug was the best in the data. Callouts did soften (about 139 to 110–127 a week). No prior-year data.
- **The recovery misleads:** Vesper, The Undertow, Farlight and Meteor Mite handled 28% of pings before 4.2, about 12 each a week, and got 2 pings combined on 2–6 Sep. None has taken a callout since 19 Aug. They are skipped locally (Old Town first pings to Vesper: 85% to 13%).
- **Tickets:** about 6 a week before, 20–32 after; of 107, quiet phone 28, gone before answer 13, filters 15. Aunt Dot and Kip (Vesper, Meteor Mite) filed none, so tickets understate this.
- **Likely cause (my read, unconfirmed):** the 60s wait turned slow answers into misses (four: 50% first week; others: 16%). A miss costs −0.12, a take earns +0.08, and nothing recovers over time, so unpinged responders stay stuck. Unproven: the database has no scores or answer times, and the acceptance weight was cut, so the score alone may not explain the skipping.
- **Next:** Wen for live scores of the four (also answers Marcus's open 14 Aug question on whether this was intended); Ravi to verify and report by responder; Nadia to reach Aunt Dot and Kip.
- **Priya's positions:** seasonal, don't discuss reverting, filter tickets are noise. These are views from the person who made the call.
- **Pending:** the regroup after the new PM's first week, no outcome recorded; a written description of how routing decides, which Priya left to the new PM.

### Roadmap (last reviewed 30 Jun; every owner still says Priya)
| Item | Roadmap | Actual state |
|---|---|---|
| Change to who gets pinged | Committed 4.2 | Shipped |
| Ping timeout tuning | Committed 4.2 | Shipped as the 60s wait |
| Availability Confidence | Committed 4.2 | **Not in 4.2 notes; unresolved** |
| Requisition approval chains (Supply) | Committed 4.3 | Brief adds extras to the $2,000 second approval; phasing TBD |
| Handler phone app | Exploring, Q4 | Sofia exploring; unstaffed, no baseline |
| Shared cover | Exploring, Q4 | No brief |

- **Overdue:** settle with Helen what is still a Q3 commitment. Priya says "a couple" of items slipped; only Availability Confidence visibly did.
- **Stale briefs:** Bulk Callout (shipped 4.1) and Routing Override Audit Log (shipped 4.0) still read as unstarted.
- **Unknown:** who owns Supply items now; the directory covers Dispatch only.
