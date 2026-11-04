# 02 · Super Hearing — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session you built a context file and met the
company.

You still do not know what actually went wrong.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

Use the rook-database connector. Call describe_table on support_tickets, then run_query. There are 147 tickets. Same treatment as before: group them, tell me how many are in each group, and quote one line from each. Count every row, including ones that look unrelated.

### 2.

You've now read both piles. Where do they disagree? What's loud in the interviews but rare in the tickets, and what's all over the tickets that nobody brought up in the interviews?

### 3.

_Drafted with Claude's help at my request, then run on 4 Nov 2026. Output: `interview-guide.md` in this folder._

The four handlers I interviewed aren't the ones filing the quiet-phone tickets. Draft an interview guide for Linda Pruitt and Desmond Okafor: seven questions, plain language, none that lead them to blame the release. Use only what's in the tickets and interviews, and save it as 02-super-hearing/interview-guide.md.
