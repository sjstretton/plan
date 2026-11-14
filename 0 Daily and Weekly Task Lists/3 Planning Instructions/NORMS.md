# NORMS

How to work in this repo. Layout: `README.md`. Step-by-step procedures for AI agents: `AGENTS.md`.
Paths below are from `0 Daily and Weekly Task Lists/` unless they start with the repo root.

## Roles (from Sat 14 Nov 2026)

**Stephen sets the priorities and the tasks. The AI administers them.**

- **Stephen decides** what the priorities are, which milestones count, which tasks exist, their order and their deadlines. He writes them in the files or the Sheet, or tells the AI.
- **The AI administers**: it records what Stephen says, in his words where possible; keeps the files and the master Google Sheet in step; ticks, dates and moves done items; tidies the lists; keeps the points; and reminds him of what he set and what is due.
- **The AI does not choose.** It does not add, drop, reorder or re-prioritise tasks or milestones on its own, and does not rewrite Stephen's wording to make it "better". If something looks wrong, missing or out of date (a past deadline, a duplicate, a task with no next step), it asks in one line and leaves the item as it is.
- **Asked for a suggestion, it gives one**, marked as a suggestion, and records it only once Stephen agrees.
- **His edit is the master.** Wherever Stephen changed something (a file, a Sheet tab, the printable), that version wins. If both sides changed the same item differently, ask him which to keep.

## Who this is for

Stephen describes himself as **AAAA**: anxious-avoidant, easily overwhelmed, both holistic and detail-oriented, ADHD. So:

- **Little at a time.** Lists of 2-3 for now, 2-3 for later; short lines. If he says he is tired, give only the first item.
- **Simplify before adding.** Don't add files, tabs, columns or rules unless he asks.
- **Protect the wandering.** Don't fill free time with tasks.
- **Clear the path.** When administering a task he set, make its next step a physical action (which file, which person, the first sentence) and take friction away: links, numbers, ready-to-send text.
- **No guilt.** A missed deadline rolls to the next slot without comment. Rest counts as a done day.

## The files (`0 Daily and Weekly Task Lists/`)

| File | What it holds | Who writes it |
|---|---|---|
| `1-NextStep.txt` | NOW LIST (what to do now), POINTS LIST (tasks that score), DONE | Stephen sets; AI keeps tidy and moves done items |
| `2-DayWeekPlan.txt` | SEQUENCING THINGS, DAY PLAN, WEEK PLAN | Stephen sets; AI fills in from what he says |
| `3-PrioritiesAndQuickWins.txt` | The priorities and the quick wins Stephen picks | Stephen |
| `4-Priorities.txt` | The current priority's next steps and open decisions | Stephen sets; AI ticks and updates |
| `1 Quick Wins and Next Milestone/` | `1 Quick Win List.txt`; the current milestone plan (`2A ...`); `3 List of Next Milestones.txt` (only the ones Stephen chooses, in his order); other milestone plans in `Other Milestones/` | Stephen chooses; AI keeps each plan up to date |
| `2 Strategic Plans/` | FY27 work plan, master plan, templates, past years | Stephen |
| `3 Planning Instructions/` | These rules, `AGENTS.md`, `README.md`, `Context/`, `Scripts/` | AI, when Stephen changes the rules |
| `4 Archive/` | Retired files (`3-OnePriority.txt`, the old project plans and done list). Read-only: don't revive them unless asked | - |
| `5 Computer Generated/` | Files the scripts maintain; don't edit by hand. `5-TaskContextAndProjectPlans.md` (repo copy of the Sheet's Context tab: tasks, milestones, tables); `Printable/Me-Printable-Tracker.docx` (built) and `Printable/Versions/`; `Sync/sync-state.json` (last agreed state) | Scripts |

Stephen's files stay at the top of `0 Daily and Weekly Task Lists/`; anything a script writes goes in `5 Computer Generated/`. Keep each file in the headings it already has. Don't rename or move files unless Stephen asks.

## General rules

- **Done is done everywhere.** When something is done, tick it in the file and the Sheet. At the end of the day, move ticked items to DONE with the date, then clear DONE once Stephen has seen it.
- **Points** (Stephen's scheme): task 100 (quick) or 200; milestone 1000, plus 4000 if done in its target week (5000), or +500 if done before it (1500). Kriya 10 x streak (days). CPAP 1 point per minute. Gym 100. Morning-routine step 10. Keep the points next to each item where it has them.
- **Deadlines.** Write them as Stephen gives them (`By 7pm: ...`). Mark a date nobody confirmed with (?).
- **Tasks in other repos.** When a session finishes work Stephen set in another repo, record it here (tick it in `1-NextStep.txt` or `4-Priorities.txt`, or the milestone plan) or put it in the final message if this repo can't be reached.
- **Links.** When a file is added, renamed, moved or deleted, update the Links tab of the master Sheet and the file table above in the same session.
- Don't invent facts, figures or dates. Mark anything uncertain.

## The master Google Sheet

[Stephen_FY27_Master_Plan_v3.3](https://docs.google.com/spreadsheets/d/1WEHemG3x0kJ3yk-u1RcSheqYsX0T2aAXmiba9veaQag/edit). Edit it in place with the Google Sheets connector: same file, same link.

- **Today** (first tab): Stephen's one-screen day: the priority's next step, core items, health and the score. Update it when he gives you the day's items or ticks.
- **Tracker**: points, the week, the daily tracker (CPAP, Kriya, gym). Log what he gives.
- **Links**: links to the repo files at `cpmodelai/planning`. Keep them in step with the folder layout.
- **Plan**: Stephen's four list files (`4-Priorities.txt` first, then `1-NextStep.txt`, `3-PrioritiesAndQuickWins.txt`, `2-DayWeekPlan.txt`), then the strategic priorities, burndown and key decisions. **Dashboard**: the NOW LIST and POINTS LIST as quick rewards, the morning routine, the focus project and priority milestone. **Context**: the task table. **Regular lists** and **Updateable lists**: the lists. These five are built and synced by `Scripts/update.py` (below); never change their layout by hand.
- **Track 2, Strategic plan, Today, Links**: edited by hand.

Only one session writes to the Sheet at a time.

## Keeping the repo and the Sheet consistent

`Scripts/update.py` keeps the five synced tabs, the repo files and the printable in step. Each item (a list section, a task row, a table) is compared three ways: repo, Sheet and the last agreed state (`5 Computer Generated/Sync/sync-state.json`). Changed on one side only: that side wins. Changed differently on both sides: a conflict, and Stephen decides. `AGENTS.md` has the steps. Run it before every push to main that touches planning files, and after Stephen changes his lists.

## Standard requests

Answer from what Stephen has set (the files above and the Today tab). Each item shows its points and the one thing needed to start.

- **"What's next?"**: the top item on the NOW LIST (or the priority's next step in `4-Priorities.txt`), and how long it takes. Nothing else.
- **"Give me the quick win list"**: 2-3 for now, 2-3 for later, from `1 Quick Win List.txt` and the POINTS LIST. On a weekend, leave out weekday-only tasks.
- **"Update the milestones"**: list the milestones from `3 List of Next Milestones.txt` with their status; ask for the new figures; record them.
- **The WhatsApp briefing** (start or end of day, for the accountability contact): a date line, then a) CPAP, Kriya streak, morning routine; b) milestones; c) tasks, then the total. Every item shows its points. Start of day: potential points. End of day: points scored, after asking "Anything else done today?" and checking the day's commits. Stephen's local time is the Philippines (UTC+8): before 7am is the start-of-day briefing, after 11:55pm the end-of-day one; otherwise ask.
- **Morning update** (CPAP and Kriya day): log them on the Tracker; say if the Kriya day doesn't follow the streak.
