## 2026-11-15 — structural-green-check — dsaa (subagent)

### touched_files

- cans/07-indonesia-programmes.md (rewritten: winners merged in as cycle leaves, depth 4)
- cans/08-indonesia-programme-winners.md (deleted)
- cans/00-overview.md (points directly at 07 only)
- cans/_rules.yaml (stopwords structural vocabulary only, synonym akzara/azkara, max_tbd_per_file 5 to 60)
- cans/_adr/001-green-check-for-name-catalogue.md (Status superseded)
- cans/_adr/002-structural-green-check.md (created)

### test_outcomes

- npx cans check: 0 errors, 0 warnings, exit 0, 2 files, 310 nodes, max depth 4, rules len 3-75, siblings 3-11, depth 4-12
- npx cans check --json: ok true, exitCode 0, counts errors 0, warnings 0
- 47 programmes, 237 cycle leaves, 60 TBD leaves, leaf lengths 9-75 chars, programme children 4-6

### still_open

- TBD cap sits at exactly 60; a 61st TBD leaf warns again — resolve TBDs or revisit the cap
- Local only, not committed or pushed; pushing still needs a fresh working token from the user

## 2026-11-15 — ranked-winners-compile — dsaa (subagent)

### touched_files

- cans/07-indonesia-programmes.md (every cycle leaf now states rank type; 3 window shifts: SYNRGY Batches 2-6, Greater Hub BSPD 9th-13th, Startup Weekend last-5 verifiable editions)
- cans/_adr/004-ranked-winners.md (created; rank format, tally, shifts, corrections, names moved to continuations, TBD-cap note)
- research/ranked-government.md, research/ranked-corporate-bank.md, research/ranked-university.md, research/ranked-incubators-accelerators.md, research/ranked-community-private.md (plus per-pair/part sub-files)

### test_outcomes

- cans check: 0 errors, 0 warnings, exit 0, 3 files, 571 nodes, depth 4, rules len 3-75, siblings 3-11, depth 4-12
- 238 cycle leaves: ranked 1st/2nd/3rd 20, 1st partial 17, 1st only 11, category 9, cohort/no-rank 94, TBD-still 54, no cycle 8, not a competition 10, no winner published 6, published order 1, named winners no rank label 6, Vietnam-only 1, in progress 1
- TBD leaves 60 -> 54 (12 fills, 6 honest tokens added where research lists the gap TBD-still); cap left at 60, _rules.yaml untouched
- Leaf rules that kept the check green: rank detail in continuation lines, never "rank" or "x" in leaves; colliding names moved to continuations (Netaly, Sutan, Medika, Pelita, Faber, Skuling, Wattr, Libere, Bakso Dandang, Belah Doeren, Project 1945, Yoona, Sourcy, Denim It Up, Aslan, AC Biode, Fluger)

### still_open

- 54 TBD leaves remain; biggest blocks: ClimateLaunchpad Indonesian national winners all 5 cycles, KUMPUL-X cohort names, SKALA 2024/2025 funded lists, Antler Jul 2026 / Jun 2025 invested lists, Endeavor Batch 7 names, GIA Batch 11 cohort
- Re-check dates: GIA Batch 14 after 20 Nov 2026; SheHacks 2026 winners Dec 2026; IA 2026 Demo Day after 10 Dec 2026; WMM 2026 final 10-15 Jan 2027; SkyStar Batch 13 Demo Day late 2026 / early 2027; GVV Batch 9 graduation early 2027; UI Studentpreneurs 16th 27 Feb 2027
- Local only, not committed or pushed; pushing still needs a fresh working token from the user. Did not touch the other workstream's files (cans/08-*, cans/_rules.yaml, research/real-sector-*.md — committed in 1fbbbc0).
