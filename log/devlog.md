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
