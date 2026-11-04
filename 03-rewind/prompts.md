# 03 · Rewind — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly.

Last session you read four conversations and every support ticket
since 4.2 — and found the two piles did not agree.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

Use the rook-database connector. Call describe_table on pings, then run_query. Every row is one time we pinged a responder, and whether they took it, turned it down, or missed it. Release 4.2 shipped on 12 August. Tell me what changed after that date. Show me the weekly numbers before and after, and show me the rows you used to get them.

### 2.

Pick one responder from the pings table who went quiet. Show me every week since June: how many pings, and what they did with each. Use their name.

### 3.

_Drafted with Claude's help at my request, then run on 4 Nov 2026. Output: `number-for-helen.md` in this folder._

If I could put only one number in front of the Director of Product, which would it be, and why not the weekly acceptance rate? Show me the rows it came from, and say what the number can't tell her. Use only the pings table. Save it as 03-rewind/number-for-helen.md.
