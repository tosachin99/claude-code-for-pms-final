# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

BEFORE ANYTHING ELSE: interview me. Ask ONE question at a time until you are 95%
confident you understand exactly what I'm asking for. After each answer, tell me
your confidence as a percentage and what is still unclear. Do not share findings
or start any analysis until you reach 95%. Then play back a one-table brief
(goal, audience, my hunch, scope, format, what is out of scope) and wait for me
to confirm. Cover: the decision this serves, who will read the result, what I
already believe, what format I want, what is in and out of scope, and any other
sources I know of.

CONTEXT: I'm the new PM for Rook Dispatch. Release [4.2] shipped on [12 August].
I need to understand what happened, to whom, and how big the impact is.

SOURCES: Use only the rook-wiki (Research interviews), the rook-database (pings,
callouts, responders, handlers, support_tickets), and the files in this folder.

STEP 1: Interviews. Read all of them. Group what the handlers are unhappy about.
For each theme give how many of the interviews raised it, one short quote,
and whether people volunteered it or were asked. Rank by count and by intensity.
Put anything outside Dispatch in a short "parked" list.

STEP 2: Tickets. Read every ticket body, not just the subjects. Group into themes
and count them before and after the release date, by week, by responder, and by
open or closed. Note repeated wording and which complaints nobody filed.

STEP 3: Pings. Compare before and after the release: pings by outcome (taken,
turned down, missed), per responder, the gap between pings, callouts nobody took,
and how often a responder is pinged in their own area. Also test what it is NOT
(time of day, position in the cascade, geography).

STEP 4: Bring it together. Make one table with a row per release change, written as
"I am a ___, trying to ___, but I cannot because ___, which makes me feel ___",
with columns for interviews, tickets, pings, and a verdict. Then make a second,
companion table of findings that did not fit the first.

STEP 5: Write the story at a 5th-grade reading level, then give me a confidence
score from 0 to 95 for each group of numbers, what would firm it up, and the data
we don't have and who to ask for it.

RULES: Name the source of every number. Label what is observed versus inferred.
Flag a small sample once, not repeatedly. Never try to identify the real people
behind cover identities (Security Policy 4.1). Don't save anything outside this
folder, and ask before sending or publishing anything.

### 2.

Open the folder 00-rook/code/dispatch-routing/. This is the part of our software that decides who gets asked to take a job. I have never read code before and I am not going to start now. Walk me through what happens from the moment something goes wrong somewhere to the moment a responder's phone buzzes, in plain English, no jargon. Then tell me which file each step lives in.

### 3.

The pings table on rook-database has last session's numbers. Read that alongside this code. Does it back up what I found in Lab A? And does that answer Marcus's question above?

### 4.

Somebody has been quiet for a month. Walk me through, step by step, exactly what would have to happen for them to start getting work again.
