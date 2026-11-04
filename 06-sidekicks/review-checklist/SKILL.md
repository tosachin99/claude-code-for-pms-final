---
name: review-checklist
description: Review each Rook Dispatch product brief against four tests (owner named, success measure, scope bounded, problem stated before the fix) and report what is flagged. Read-only. Use when asked to run the review-checklist, or on the Monday schedule.
---

# review-checklist

A weekly check on the product briefs, so gaps are caught before anyone builds. Rook Industries is a fictional course scenario.

This skill is **read-only**. Do not create, edit or delete any file, do not send or publish anything, and do not save anything to memory. Print the report as your answer. (If the student asks, they can save the printed report into `06-sidekicks/` themselves or ask you to.)

## What to review
1. The four briefs on the Rook wiki, "Product briefs" page. Use the rook-wiki connector: `search_wiki` for "Product briefs", then `read_page` on each child page: **Bulk Callout**, **Handler Phone App**, **Requisition Approval Chains**, **Routing Override Audit Log**. If a page is not found, search the wiki by its title and say which one could not be read.
2. The student's own draft in the course folder: `05-super-speed/brief.md`.
3. If `06-sidekicks/briefs/` exists and has files, review those too. If it does not exist, say so in one line. That is not a failure.

## The four tests (answer yes or NO for every brief)
- **owner named:** a person or a named team owns it. "Nobody has picked it up yet" is not an owner. A line like "[GAP] none named" counts as NO.
- **success measure:** it says how anyone would know it is working.
- **scope stays bounded:** it does not grow mid-document. Flag it if it opens with one ask and then adds more asks later.
- **problem stated before fix:** the problem comes before the proposed solution. Flag it if the document opens with the solution.

## Output format (plain text)
```
review-checklist - <manual run | scheduled run>
Started: <today's date and time>
Sources: <the briefs actually read, and any that could not be read>

<brief name>
  owner named ................. yes/NO - flagged
  success measure ............. yes/NO - flagged
  scope stays bounded ......... yes/NO - flagged
  problem stated before fix ... yes/NO - flagged
  -> <n> flag(s): <one plain sentence per flag, quoting a few words from the brief>

(repeat for every brief)

<N> briefs checked, <M> flagged.
```
Then add a short section **What changed since last time**, at most 3 lines, only if you can tell (for example, a brief now names an owner, or a draft contradicts the files in the folder). If you cannot tell, skip it.

## Rules
- Name which brief every claim comes from. Label anything inferred.
- Never try to work out who the real people behind responder cover identities are (Security Policy 4.1).
- Keep the whole report under one page, in plain language for a non-technical reader.
- If the rook-wiki connector is not available, say so clearly, review only the files in the course folder, and do not guess about the wiki briefs.

## Where it runs
- By hand: ask Claude to run review-checklist.
- On a schedule: a scheduled task named `monday-review-checklist` runs the same checks every Monday morning (about 9:06). Its task file is kept by the app outside this folder.
