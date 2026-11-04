# What release 4.2 did, to whom, and how big

Rook Dispatch. Release 4.2 shipped 12 August 2026. Written from the wiki interviews, the Rook database and the routing code in this folder only. Nothing here was sent or published.

**Bottom line.** Your hunch holds for the biggest effect: the 60-second wait explains the jump in missed pings. It doesn't explain why four responders went nearly silent. That looks like a knock-on effect, which I infer from the code but can't prove from this data.

**Key.** [W] = wiki interviews, [T] = support_tickets, [P] = pings, callouts and responders tables, [R] = routing code in this folder. Everything is observed unless marked *(inferred)*.

**Periods.**
- Pings: before = 29 Jun–11 Aug (44 days), after = 12 Aug–6 Sep (26 days).
- Tickets: before is the same, after runs 12 Aug–7 Sep.
- Per-week figures account for the different lengths.

**Small samples, flagged once.**
- Only 4 of 15 handlers were interviewed [W].
- The four quiet responders have just 56 pings since the release [P].
- The 00–05 hour band has 31 pings [P].
- The tickets look partly copy-pasted: 122 distinct bodies in 147 tickets [T].

## Step 1: Interviews [W]

| Theme | Raised by (of 4) | Quote | Volunteered or asked | Intensity (my judgement) |
|---|---|---|---|---|
| Ping gone before they could answer | 3 (Dot, Ambrose, Halloran) | "by the time he's actually got a thumb on the screen — it's gone" (Dot) | Dot and Ambrose volunteered it. Halloran gave it only to the closing "anything else?" | Medium-high |
| Quiet stretches, uneven work | 2 (Dot, Kip) | "Mite thinks Mite's been forgotten. Gale's exhausted." (Kip) | Kip volunteered it. Dot was asked. | Medium |
| Text too small | 2 (Dot, Ambrose) | "Larger text on the status badge." (Ambrose) | Both were asked | Low-medium |
| Alerts (handler can't tell, same sound) | 2 (Dot, Kip) | "something that tells me too, not just him" (Dot) | Asked | Low |
| Filters reset silently | 1 (Ambrose) | "I'd rather it warned me the filter had reset" | Asked | Low |
| Dark mode | 1 (Kip) | "I am begging." | Volunteered | Highest |
| Tag legend hard to find | 1 (Ambrose) | "I open it perhaps once a fortnight" | Asked | Low |

- **Ranked by count:** gone-before (3), then quiet, text size and alerts (2 each).
- **Ranked by intensity:** dark mode, then the parked requisition complaint, then gone-before.
- **How they raised it:** the interviews were about the console, so no opening question was about pings. All four still brought the subject up, mostly late in the call and as an aside.
- **Parked (Supply, not Dispatch)** [W, Halloran]:
  - Requisition approvals are slow, with an 11-day wait for a cracked vest plate.
  - The priority field changes nothing.
  - Failure reports "go into a void."
  - Catalog search is poor.
  - He said maintenance scheduling has improved.

## Step 2: Tickets [T]

| Theme | Before | After | Per week before → after | Open / closed |
|---|---|---|---|---|
| Quiet phone | 0 | 30 | 0 → 7.8 | 30 / 0 |
| Gone before answer | 0 | 15 | 0 → 3.9 | 15 / 0 |
| Other ping problems | 6 | 0 | 1.0 → 0 | 0 / 6 |
| Filters | 2 | 14 | 0.3 → 3.6 | 6 / 10 |
| Console polish | 11 | 11 | 1.7 → 2.8 | 8 / 14 |
| Console bugs | 5 | 5 | 0.8 → 1.3 | 5 / 5 |
| Missing features | 4 | 6 | 0.6 → 1.6 | 4 / 6 |
| Account and admin | 2 | 10 | 0.3 → 2.6 | 6 / 6 |
| Supply | 10 | 16 | 1.6 → 4.1 | 9 / 17 |
| **Total** | **40** | **107** | **6.4 → 27.7** | **83 / 64** |

- **By week (total):** 6, 6, 8, 5, 7, 7 before. Then 20, 27, 32, 25 after (week of 7 Sep: 4, one day).
- **Order of events:**
  - Gone-before tickets came first: 7 in the release week, then 3, 3, 2.
  - Quiet-phone tickets began a week later (first on 17 Aug) and peaked at 12 in the week of 24 Aug.
- **By responder:**
  - Quiet tickets are about only four responders: The Undertow (10), Farlight (10), Halfmoon (5) and Corporal Ashgrove (5).
  - Gone-before tickets spread across 12 responders, with 1–2 each.
  - Those four responders account for 69 of 147 tickets.
- **Open or closed:**
  - All 40 pre-release tickets are closed.
  - Of the 107 since, 83 are open.
  - None of the 45 ping tickets is closed, against 24 of the 62 other post-release tickets.
- **Repeated wording:**
  - "not like her/him at all" (5)
  - "flagging for the record" (5)
  - "asked me to pass this on" (5)
  - "rather know than guess" (4)
  - "still in the system / on the list" (6)
  - "set amount of time before it moves on" (2)
- **Complaints nobody filed:**
  - No ticket names the shorter wait, proximity, ranking or a far-off callout (keyword search, 0 matches).
  - No one complained of too many pings.
  - Vesper's and Meteor Mite's handlers filed nothing.
  - No one asked for handler-side alerts.

## Step 3: Pings [P]

| | Before | After |
|---|---|---|
| Taken | 76.6% | 64.0% |
| Turned down | 21.1% | 18.0% |
| Missed | 2.3% (25 pings) | 18.0% (110 pings) |
| Pings per week | 172.6 | 164.5 |
| Gap after a miss | 91–93 s | 61–63 s |
| Gap after a turn-down | 6–40 s | 6–40 s |
| Callouts nobody took | 5.5% | 11.1% |
| Callouts needing 2+ pings | 22.1% | 32.5% |
| Slowest 10% of callouts, callout to taking ping | 41 s | 78 s |

- **Daily:** missed pings were 0 and 1 on 10–11 Aug, then 7 of 25 on 12 Aug and 12 of 25 on 13 Aug. In the six weeks before, acceptance stayed between 75.0% and 77.9%.
- **The four starved responders:**

| Responder | Pings per week | Missed after | Last ping taken |
|---|---|---|---|
| Farlight | 11.9 → 3.0 | 64% | 14 Aug |
| The Undertow | 11.9 → 3.8 | 64% | 17 Aug |
| Meteor Mite | 11.1 → 3.8 | 57% | 19 Aug |
| Vesper | 13.7 → 4.6 | 53% | 17 Aug |

  - Combined, they went from about 49 pings a week to 15, a drop of 69%.
  - Their weekly pings fell gradually: about 49 before, then 43, 16, 6 and 3 in the weeks since.
  - The other twelve responders' missed rate rose from 2.1% to 13.9%, and their volume rose about 21%.
- **Own area:**
  - The share of pings going to a responder in their own area fell from 82.9% to 60.6%.
  - Before, none of the 186 out-of-area pings was taken. After, 36% of 241 were.
  - So 86 of the 391 callouts taken since the release (22%) went to someone outside the area. Before, it was 0 of 831.
  - The four and the other twelve show the same shift: 83.7% to 60.7%, against 82.5% to 60.5%.
- **What it is not:**
  - **Time of day:** missed rose in every band: 1.6% to 18.4% (06–11), 1.8% to 17.5% (12–17) and 2.5% to 19.0% (18–23). The 00–05 band went 4.8% to 12.9%, from only 31 pings.
  - **Position in the order:** missed rose at every position: 2.7% to 21.4% (first), 0.5% to 9.8% (second), 0% to 7.1% (third or later).
  - **Geography:** missed rose in all 15 areas, from 0–6% before to 10–32% after.
  - **Seasonal:** callouts did fall, from about 140 to 118 a week. But missed is a share of pings, and it jumped on one day.
- **Mechanism (inferred, unproven):**
  - The shorter wait turns answers that used to arrive at 60–90 seconds into misses.
  - [R] says a miss costs the same score as a turn-down (−0.12), a take adds +0.08, and nothing recovers over time. So a responder who misses a lot ranks lower, gets fewer pings and can't earn the score back.
  - The four missed about 59% of their pings after the release, against 14% for the rest. I infer they are the slower answerers, but the log has no answer times.
- **Why the headline "recovered":**
  - Weekly acceptance went 54.2%, 65.8%, 66.7%, 72.7%.
  - The four are now almost absent, so their misses no longer pull the average down.
  - The other twelve's missed rate fell from 15.7% to 11.1%, still far above 2.4% before.

## Step 4: One row per release change

| Release change | "I am a ___, trying to ___, but I cannot because ___, which makes me feel ___" | Interviews | Tickets | Pings | Verdict |
|---|---|---|---|---|---|
| Ping wait 90 s to 60 s | "I am a responder, trying to answer a ping, but I cannot because it vanishes after 60 seconds, which makes me feel cheated." | 3 of 4 | 15 gone-before, 2 asking if there is a time limit, 0 naming the wait | Missed 2.3% to 18.0%; gap 92 s to 62 s; every time band, position and area | Strong cause of the missed-ping jump. |
| Proximity weight up, acceptance weight down | "I am a responder who used to get steady work, trying to be offered a job, but I cannot because the ranking quietly dropped me, which makes me feel forgotten." | 2 of 4 | 30 quiet-phone tickets from 4 handlers | Four responders −69%; out-of-area takes 0% to 22% of takes; local first pings 80% to 61% | Real, large for four responders. Cause partly known (inferred): the weight change and the wait together. |
| Console filters persist | "I am a handler, trying to keep my filters, but I cannot because they reset overnight or show a colleague's, which makes me feel I can't trust the screen." | 1 raised it as a problem (Ambrose also welcomed the change) | 14 since the release: 4 silent resets, 2 shared-computer, 2 wrong-computer, 2 can't clear, 2 badge, 2 thanks | Not testable | Real but separate from pings; 13% of post-release tickets. |
| Three defect fixes (duplicate push, tag order, export time zone) | "I am a handler, trying to trust what I see, but I cannot because the same ping or tag order changes, which makes me feel unsure." | 0 | The matching tickets all predate the release; none since | Duplicates can't be tested | Looks fine; small numbers. |
| Availability Confidence (committed for 4.2, not in the notes) | "I am a handler, trying to see how sure an availability is, but I cannot because it isn't there, which makes me feel guessing." | 0 | 0 | Not testable | Nobody has asked; unverified. |

**Findings that did not fit**
- **Out-of-area takes:** 22% of taken callouts now go to someone outside the area, and no ticket or interview mentions it.
- **Away pings are missed more:** 29.9% missed, against 10.3% for own-area pings, even though both had 90 seconds before the change.
- **Own-area missed rate:** it rose from 0.7% to 10.3%, so the wait alone moves it.
- **Callouts per week:** they fell about 15%, from 139.8 to 118.5, and nothing explains it.
- **Kip's handler story checks out:** The Gale went from 13.0 to 18.6 pings a week while Meteor Mite fell from 11.1 to 3.8.
- **Halloran's and Ambrose's responders:** Sgt. Bulwark's missed rate went from 0% to 18%, and Captain Vantage's from 3% to 10%, with volume up. That matches their accounts of late callouts.
- **Halfmoon and Corporal Ashgrove:** their handlers filed 29 tickets, but their pings fell only about 20%, from 11.0 to 8.9 and from 10.0 to 7.8 a week.
- **Rising tickets elsewhere:** admin tickets went from 0.3 to 2.6 a week and Supply from 1.6 to 4.1, with no explanation in the data.
- **Priya's seasonal claim:** [R] and [P] don't support it.

## Step 5: The story, in simple words
When 4.2 came out, a phone offer began to disappear after 60 seconds instead of 90. Some people need more than a minute to answer. Their offers now vanish before they can say yes, and the system counts a vanished offer the same as a "no." So their score drops, and the system offers them fewer jobs. Four responders got fewer and fewer offers. Now they almost never hear anything, and they have started to wonder if they've been forgotten. Everyone else still gets offers, but about one in seven now vanishes. This was not a quiet August. It started on the day of the release.

**Confidence (0–95), what would firm it up, and who to ask**

| Group of numbers | Score | What would firm it up | Data we don't have, and who to ask |
|---|---|---|---|
| Ping outcomes, gaps, callouts nobody took [P] | 90 | Match them to Ravi's weekly report | Ravi Menon |
| Four-responder collapse [P] | 80 | Same check, plus pings after 6 Sep | Ravi; Wen Li for live scores |
| Wait is the cause of the missed jump | 75 | Answer times per ping | Wen Li |
| Score knock-on as the reason for the four (inferred) | 45 | Score history for those four | Wen Li |
| Out-of-area takes and proximity effect | 40 | Travel times per ping | Wen Li |
| Ticket counts by theme [T] | 70 | A second person re-sorts them | Nadia Hoffmann (also reply history, the 26 Aug email) |
| Interview themes [W] | 40 | Interviews with Linda Pruitt and Desmond Okafor | Sofia Marino |
| Tests for time of day, position, area [P] | 75 | A larger sample in the 00–05 band | Ravi |
| "Not seasonal" | 80 | Data from before 29 Jun and from last year | Ravi |
