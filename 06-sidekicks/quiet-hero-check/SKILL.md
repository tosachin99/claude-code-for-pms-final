---
name: quiet-hero-check
description: List any Rook Dispatch hero whose offers in the last seven days are under half their usual week, using only the Rook database. Read-only. Use when asked to run the quiet-hero check, or on a schedule.
---

# quiet-hero-check

Finds heroes (responders) who have gone quiet, before their handlers have to file a ticket. Rook Industries is a fictional course scenario.

This skill is **read-only**. Use only the rook-database connector. Do not create, edit or delete any file, do not send or publish anything, and do not save anything to memory. Print the report as your answer.

## What counts as quiet
A hero is **quiet** when the offers they received in the last seven days are **less than half** their usual week.
- **Usual week:** their offers per week from the start of the data up to the day before the 4.2 release (12 August 2026). That period is 44 days.
- **Last seven days:** the seven days ending on the date of the latest offer in the data. The data in this course stops on 6 September 2026, so the window is 31 August to 6 September.

## How to check
Run this one query with `run_query` from the rook-database connector, and nothing else:

```sql
with latest as (select max(sent_at)::date as d from pings),
usual as (select responder, count(*) / (44 / 7.0) as usual_per_week
          from pings where sent_at < '2026-08-12' group by responder),
recent as (select responder, count(*) as last_7_days,
                  count(*) filter (where outcome = 'taken') as taken,
                  count(*) filter (where outcome = 'missed') as missed
           from pings, latest where sent_at >= latest.d - 6 group by responder)
select u.responder, round(u.usual_per_week, 1) as usual_per_week,
       coalesce(r.last_7_days, 0) as last_7_days,
       round(100.0 * coalesce(r.last_7_days, 0) / u.usual_per_week) as pct_of_usual,
       coalesce(r.taken, 0) as taken, coalesce(r.missed, 0) as missed,
       (coalesce(r.last_7_days, 0) < u.usual_per_week / 2.0) as flagged,
       (select d from latest) as window_ends
from usual u left join recent r using (responder)
order by pct_of_usual, u.responder
```

## Output format (plain text, under one page)
```
quiet-hero-check - <manual run | scheduled run>
Started: <today's date and time>
Window: <first day> to <last day> (the latest offer in the data)

QUIET (under half their usual week)
  <hero>: <last_7_days> offers vs <usual_per_week> usually (<pct>%), <taken> taken, <missed> missed
  ...

WATCH (50 to 80% of usual)
  <hero>: ...

<N> of <total> heroes are quiet.
```
Then add **What changed since last time**, at most 3 lines, only if you can tell from an earlier run saved in `06-sidekicks/`. If you cannot tell, skip it.

## Rules
- Name the table every number comes from (pings).
- Say plainly that "quiet" means few offers, not that the hero did anything wrong. A quiet hero may not have been asked at all.
- Never try to work out who the real people behind cover identities are (Security Policy 4.1).
- If the rook-database connector is not available, say so and stop. Do not guess.
