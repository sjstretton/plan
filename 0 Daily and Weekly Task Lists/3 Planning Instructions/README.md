# Planning

Stephen's planning repo (`cpmodelai/planning`). **Stephen sets the priorities and the tasks; the AI administers them** (records, keeps the files and the Sheet in step, ticks, tidies, keeps the points). The rules are in `NORMS.md`.

**Start here each morning:** the **Today** tab of the master Sheet, or `0 Daily and Weekly Task Lists/1-NextStep.txt`.

## Files

```
.
├── AGENTS.md, CLAUDE.md, README.md, NEXT-STEPS.md (PhD application checklist, 1 Nov)
└── 0 Daily and Weekly Task Lists/
    ├── 1-NextStep.txt                  NOW LIST, POINTS LIST, DONE
    ├── 2-DayWeekPlan.txt               sequencing, day plan, week plan
    ├── 3-PrioritiesAndQuickWins.txt    priorities and quick wins
    ├── 4-Priorities.txt                the current priority's next steps and decisions
    ├── 1 Quick Wins and Next Milestone/  quick win list, next milestone plan (2A), list of milestones,
    │                                     Other Milestones/ (2B website, 2C journal paper)
    ├── 2 Strategic Plans/              FY27 work plan, master plan (.xlsx and link), weekly (Word),
    │                                   Planning Templates/, past years (FY24, FY25, FY25-26, FY26), Team Workshop/
    ├── 3 Planning Instructions/        NORMS.md (the rules), AGENTS.md, CLAUDE.md, README.md (this file),
    │                                   CheckRepo.bat, Context/ (routines, weekly log, repo directory),
    │                                   Scripts/ (update.py: sync, build, render, eod, check; make_printable.py)
    ├── 4 Archive/                      retired files (one-priority briefing, done list, ...)
    └── 5 Computer Generated/           written by the scripts only: 5-TaskContextAndProjectPlans.md (task table),
                                        Printable/ (Me-Printable-Tracker.docx, Versions/), Sync/ (sync-state.json)
```

## Master Google Sheet

[Open](https://docs.google.com/spreadsheets/d/1WEHemG3x0kJ3yk-u1RcSheqYsX0T2aAXmiba9veaQag/edit). Tabs: **Today** (start here), Dashboard, Track 2, Tracker, Plan, Strategic plan (hidden), Context, Regular lists, Updateable lists, Links. Dashboard, Plan, Context and the two lists tabs are built and synced by `Scripts/update.py` (see `NORMS.md`).
