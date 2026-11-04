# Quiet responders: a comeback path (DRAFT one-pager)

For Helen Achebe. Draft, not decided. **[GAP]** marks what we still don't know. Sources: pings and tickets tables, the September interviews, the routing code (folder copy last changed 8 Oct, may not match live).

## The problem
Since 4.2 (12 Aug), four responders went from about 12 pings a week each to about 3 to 5: Farlight, The Undertow, Meteor Mite and Vesper. None has taken a ping since 19 Aug. Almost all their pings are now missed (53–64%).

Likely cause, **inferred, not confirmed**: the 60-second wait turns a slow answer into a miss. The code scores a miss the same as a "no" (−0.12; a yes is +0.08), and the score never recovers on its own, so a quiet responder stays quiet.

## Who it happens to
- **Farlight:** 75 pings before the release, 11 since, last taken 14 Aug, none since 28 Aug. Their handler Linda Pruitt has filed 10 tickets about it and passed on Farlight's words: "starting to wonder if im still even in the system."
- **Kip** sees it on his screen: Meteor Mite dead quiet, The Gale "on fire" (13 to 19 pings a week). He says: "I don't even know what I'd want it to tell me."

## What we'd build (proposal, for Helen to react to)
Not a setting. A visible comeback path:
- **Responder:** after a quiet stretch (**[GAP]** how many days), the next callout that suits Farlight, with the right skills and close enough, goes to Farlight first with a longer wait. A slow answer isn't lost.
- **Handler:** the responder's card says, in plain words, "No pings for 5 days. The next suitable callout goes to Farlight first." Linda and Kip stop guessing.
- **Underneath:** a missed ping stops costing the same as a "no" (**[GAP]** how much), and scores ease back over time. This answers Wen's 2019 note, which assumed silence means someone stopped taking work. With a 60-second window, silence can just mean slow.

## Success measure (targets are proposals; **[GAP]** baseline from Ravi)
- The four back to at least 8 pings a week within three weeks, from about 4.
- Their yes-rate at 60% or more. Below that, the score keeps falling.
- No responder with zero pings for 7 days.
- New quiet-phone tickets: from about 8 a week to none within four weeks.

## Scope
**In:** the comeback path, the handler line, the missed-ping fix.
**Out:** proximity and capability weights, the handler phone app, Supply, console polish.
**Rule:** works from skills, availability and ping history only, never identity (Security Policy 4.1).

## Owner
**[GAP]** none named. Suggested: PM owns the brief; Wen Li and Marcus Oyelaran own the build; Sofia Marino designs the handler card; Ravi Menon owns the numbers. Confirm with Helen.

## Gaps before it can be built
1. **Real scores and answer times** (Wen Li). Without them the cause is a strong guess.
2. **Does the live code match this copy?** Six pieces here are empty placeholders.
3. **One chosen approach and a named owner.**
4. **Baselines and targets per responder** (Ravi Menon).
5. **Side effects:** sending the four more pings may shift load off others, and Supply reads the availability record (**[GAP]** Supply owner).
6. **Release and rollback:** routing ships with a release. We need a date, an approver, a test on the ping log first, and a way to undo.
7. **Policy 4.1 text**, which isn't in the wiki.

## This week
- Reply to Linda Pruitt, Desmond Okafor, Aunt Dot and Kip. They shouldn't wait for the build.
- Ask Wen: "Was a missed ping meant to cost the same as a 'no' once the wait dropped to 60 seconds?"
- Sofia mocks the handler card; Helen picks a direction.
- Still to make: the clickable prototype (not built).
