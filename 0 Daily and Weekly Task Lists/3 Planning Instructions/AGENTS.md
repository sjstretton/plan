# AGENTS

**Stephen sets the priorities and the tasks; you administer them.** Record what he says, keep the files and the master Google Sheet in step, tick and tidy, keep the points, remind. Don't add, drop, reorder or re-prioritise anything on your own: if something looks wrong, ask in one line. Read `NORMS.md` ("Roles" and "Who this is for") before any work.

Paths below are from `0 Daily and Weekly Task Lists/`.

## Where things are

- Day to day: `1-NextStep.txt`, `2-DayWeekPlan.txt`, `3-ProjectPlanPhD.txt`.
- Quick wins and milestones: `1 Quick Wins and Next Milestone/`.
- Strategic plans: `2 Strategic Plans/` (FY27 work plan `Stephen_FY27_Work_Plan_v2.6_15thOct.docx`).
- Rules and context: `3 Planning Instructions/` (this folder).
- Retired files: `4 Archive/`. Don't edit or revive them unless asked.
- Computer-maintained files: `5 Computer Generated/` (task table, printable, sync state). Only the scripts write there.
- Master Google Sheet: https://docs.google.com/spreadsheets/d/1WEHemG3x0kJ3yk-u1RcSheqYsX0T2aAXmiba9veaQag/edit. Edit it in place with the Google Sheets connector.

## When Stephen gives you priorities or tasks

1. Write them into the file he names, or the one that fits (`NORMS.md`, "The files"), in his words and in that file's existing headings.
2. Put the same items on the Sheet's **Today** tab if they are for today.
3. If a file or a Sheet tab changed, update the Links tab and the file table in `NORMS.md`.
4. Tell him in two or three lines what you recorded and where. Ask about anything unclear; don't guess.

## Sheet

- Read a tab with `get_values` before you write to it; Stephen may have changed it.
- Today, Track 2, Strategic plan and Links are edited by hand. Dashboard, Plan, Context, Regular lists and Updateable lists are built by `Scripts/update.py`: use the procedure below.

## Sync: keep the repo, the Sheet and the printable consistent

Run the scripts from `3 Planning Instructions/`. Only one session writes to the Sheet at a time. Stephen's change is the master wherever he made it; if both sides changed the same item differently, ask him which to keep.

1. `git pull`.
2. Read the Dashboard, Plan, Context, Regular lists, Updateable lists and Tracker tabs with `get_values` (range `A1:K400` each) and save them as one JSON file in your scratchpad: `{"Dashboard": values, "Plan": values, ...}`. Run `python3 Scripts/update.py check-sheet --snapshot <file>`.
3. `python3 Scripts/update.py sync --snapshot <file> --apply`. Exit code 2: conflicts; show Stephen each one and stop until he decides. Exit code 4: a tab is missing from the snapshot.
4. `python3 Scripts/update.py build` (`--force` only after folding a hand edit of the printable into the sources).
5. `python3 Scripts/update.py render --out <payload> --snapshot <file>`. For each changed tab, send its `requests` with `update_spreadsheet`, then write its `values` from A1 with `update_values` (replace an empty row `[]` with `[""]`). Then write each `Tracker ranges` entry. Read the tabs back and check them.
6. `python3 Scripts/update.py baseline`, then `python3 Scripts/update.py check` (must print OK).
7. Commit and push.

## End of day (Stephen asks for "the end-of-day tidy")

1. Read the Today tab and the files; ask "Anything else done today?"
2. Sync steps 1-3, then `python3 Scripts/update.py eod --snapshot <file>` (dry run): show Stephen what it will close; then run it with `--apply`. Done anywhere is done everywhere.
3. Ask Stephen for tomorrow's items if he hasn't given them; don't invent them. Put what he gives into `1-NextStep.txt` and the Today tab.
4. Sync steps 4-7 (`build --date <tomorrow>`), then delete the temporary .eod-tracker.json in 5 Computer Generated/Sync/ (git-ignored). Push to the assigned branch, or main if Stephen asks.
