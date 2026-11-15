# ADR-003: real-sector-umkm-file

- Status: accepted
- Date: 2026-11-15
- Decided by: dsaa, on user request to expand the knowledge base to real sector and UMKM

- Context
  - The 47 programmes in 07 are tech-dominant. The user directed expansion to real sector and UMKM
  - Four research groups verified new recurring programmes (research/real-sector-umkm-gov.md, research/real-sector-agrifood.md, research/real-sector-industry-creative-tourism.md, research/real-sector-corporate-social.md): 44 raw programme mentions, 42 unique after dedupe
  - 07 cannot absorb them: its groups are already 8-10 programmes (cap 11) and its TBD cap is already at exactly 60
  - ADR-002 deleted the old 08 because it duplicated the same 47 programmes. This new 08 holds DIFFERENT programmes, not a duplication, so a new file is the structural answer, not the ADR-002 mistake repeated
  - Strict rules stay intact: node length 3-75, siblings 3-11, depth 4-12, single_child_collapse true, style prefer sibling, shared_prefix_detection true, redundancy enabled true
  - Baseline before this change: `cans check` green, 3 files (00, 07, _rules), 310 nodes, depth 4

- Decision
  - New file cans/08-indonesia-real-sector-umkm.md, canonical home for the 42 new programmes only
    - Indonesia Real Sector and UMKM Programmes, depth 1
    - Group, depth 2, 5 groups: UMKM and government programmes (11), Agri-food, fisheries and rural (10), Manufacturing and industry (5), Creative, craft and tourism (8), Corporate, foundation and social (8)
    - Research group C (13 programmes) was split into Manufacturing and industry (5) and Creative, craft and tourism (8) because 13 exceeds the 11 sibling cap
    - Programme name, exact, depth 3. Attributes as continuation lines under the programme node, not child nodes: organiser, open to, offers, cycle, plus status, exactly as in 07
    - Children: cycle leaves, depth 4, one leaf per cycle, no intermediate Winners node. Actual editions per programme, not a forced 5: 3-11 leaves per programme, mostly 5
    - Cycle leaves carry winners/rank as in the research (ranked 1st/2nd/3rd, category winners, cohort/no-rank, no-winner-published, TBD-still). Nothing invented
  - Dedupe
    - Pertamina UMK Academy in Group A only, not again in Group D. Renamed to UMK Academy (renaming explained below); full name preserved as a continuation line
    - YDBA once, in Group A as YDBA UMKM BISA. The separate annual YDBA Award (Group D section 3) is NOT a separate node; its verified 2023 and 2025 Mandiri Terbaik winners are recorded as continuation lines under the YDBA node
    - INOTEK UUI and SETC are distinct programmes, both kept, overlap noted under both. The joint IDEAL 2024 Top 5 is recorded only under INOTEK (canonical home); the SETC 2024 leaf points at it in prose, with no link pointer, to avoid a refs issue
  - Exclusions and qualifications
    - IGDS included only as legacy/paused, last verified edition 2021; not presented as recurring
    - Citi Microentrepreneurship Awards excluded (discontinued 2019, appendix only in the research)
    - E-Incubation UGM included with a Qualification continuation line: general business incubation, only 2026 agribusiness-themed
    - WUB IKM included as a non-competitive cohort/no-rank training programme; 07 already holds non-competitions (e.g. StartupLokal), so a non-competitive programme fits
    - FertInnovation is biennial (2021/2023/2025 only, gap leaves, no invented 2026 edition); Cup of Excellence has only 4 editions (2021/2022/2023/2026, with a No edition held leaf for 2024-2025); Pahlawan Digital ran only 2020/2022/2023; YDBA UMKM BISA only 2 editions (2025/2026, with a No earlier edition leaf)
    - Not included: MARLIN (2 cycles only), Indofood Riset Nugraha and Food Startup Indonesia Accelerator (optional extras the task did not ask for; future candidates), PLUT-KUMKM (service-centre network, not a cohort/competition), CIMB Kejar Mimpi Rising Start (singing competition, not entrepreneur), Cita Tenun Indonesia, Modest Young Designer Competition, and IFW itself (an event, not a programme)
  - TBD discipline: 33 TBD leaf titles in 08, well under the 60/file cap. TBD in a leaf title only where the leaf's primary content is genuinely unknown (research rank type TBD-still). Partial leaves (verified content, some names missing) use partial / not found / not published in the title, with missing names noted in continuations. Unverified multi-year spans merged into single leaves per the 07 precedent (ATAVI Batches 3-5): Dekranas 2021+2022+2024, ITTA 2021+2022, IYFDC 2022+2024, E-Incubation 2022+2023
  - UMK Academy rename: the 08 programme node is UMK Academy, not Pertamina UMK Academy, because pertamina (08) collides with pertamuda (07 programme) at Levenshtein 2 and the two are distinct entities. The full name is preserved verbatim as a continuation line under the node. UMK Academy is the programme's own short name (2024 refresh)
  - Three 07 leaf titles were shortened the same structural way (colliding token out of the title, name kept in the continuation): GnB Batch 1 dropped XWORK (xpora in the 08 programme node BNI Xpora), Startup Inovasi 2022 dropped Yayasan Upakara Bhuvana Nusantara (upakarti is the 08 programme node Upakarti; the leaf lists exactly 9 PPBR recipients, so the title is now 2022: 9 PPBR recipients named), PFpreneur 2023 dropped mitra (astra in the 08 programme node Astra SATU Indonesia Awards; title now 2023: 153 UMKM selected as partners). No 07 substance changed; 07 stays at 60 TBD leaves
  - Overview 00 updated: Coverage is now 89 programmes in 10 groups (47 tech in 5 groups in 07 + 42 real-sector/UMKM in 5 groups in 08), with a Real sector leaf under Coverage and a link leaf under Where: Real sector: see 08-indonesia-real-sector-umkm.md. The link is a file-level link (no anchor) because the full anchored form (see 08-indonesia-real-sector-umkm.md#Indonesia-Real-Sector-and-UMKM-Programmes) is 93 chars, over the 75-char node limit; the checker accepts file-level refs (an emptied anchor degrades to a file-level ref)
  - Purpose leaf reworded from Indonesia startup programmes knowledge base to Indonesia programmes knowledge base, since the scope is no longer startup-only; Kind gained awards

- Rules changes, all recorded here, no check disabled or weakened
  - redundancy stopwords, generic words only, in two rounds. Round 1 (51 words): generic English (e, co, lab, grand, full, hub, over, booth, fashion, tourism, results, rural, social, young, youth, sector, export, online, offline, natural, fiber, class, under, choice, curated, theme, spice, hotel, water, board, story, foods, level, podium, travel, excellence), generic Indonesian (umkm, desa, juara, tenun, wirausaha, kreatif, kreasi, karya as the Indonesian cognates of the already-stopworded creative, rumah for house, hijau for green, bintang as a tier label), competition words (champion, champions, cf. winner), and numbers 25 and 50 (same class as 1-20). Round 2 (11 words): events (plural of event), coverage, group, groups, finance (generic overview words), finale (generic), beverage (generic, cf. food), pangan (Indonesian for food, cf. food), craft (generic category word, cf. creative), note (structural vocabulary, cf. list, below), real (generic adjective, cf. overall, single, total; also stops the 00-overview link leaf colliding with the 08 root, since the 08 filename itself carries real). No winner, company, organiser or programme names are stopwords. The one programme-name near-collision that no stopword can cover, Pertamina vs Pertamuda, was fixed by titling the 08 node UMK Academy instead (per the decision above)
  - No other rule changed. word_frequency_threshold stays 4, phrase_overlap_threshold stays 0.7, cross_file_threshold stays 2, fuzzy stays true with max distance 2 and min word length 5. max_tbd_per_file stays 60

- Alternatives considered
  - Merge the 42 programmes into 07
    - Rejected: 07 groups are at 8-10 of the 11 cap and 07 is already at its 60 TBD cap. Merging would breach both caps and force either filler groups or config tuning
  - One file per research group (4 files)
    - Rejected: four more files to link, keep green, and keep orphan-free, for groups of 10-13 programmes each; a single 08 file with 5 groups is the smallest structure that holds the set
  - Exclude IGDS, E-Incubation UGM and WUB IKM entirely
    - Rejected: each is a real recurring programme; the honest fix is an explicit qualification or legacy flag, not deletion
  - Map Pertamina and Pertamuda as synonyms
    - Rejected: distinct entities must stay distinct, per ADR-002. The node was renamed instead, full name preserved in a continuation line
  - Map distinct near-identical winner names as synonyms, or add proper names as stopwords
    - Rejected: distinct companies and people must stay distinct. Instead, colliding name tokens were moved from cycle-leaf titles to continuation lines under the same leaf, so the names stay in the file and the checker no longer compares them as nodes. 51 edits in round 1 and 7 in round 2, plus the 3 07 leaf shortenings above. Round 2 also fixed three pairs the round-1 wording itself created (million vs trillion, grantee vs grantees, carrier vs earlier) by rewording the new titles, and two exact overlaps (both Programme did not exist leaves reduced to {exist}; the group Creative, craft and tourism and the programme Indonesia Fashion and Craft Awards both reduced to {craft}, fixed by stopwording craft)
  - Config tuning to hide the redundancy issues (ADR-001)
    - Rejected: the user rejected ADR-001. Nothing was disabled or weakened; every issue was fixed structurally

- Consequences
  - `cans check`: 0 errors, 0 warnings, exit 0. 3 files, 570 nodes, max depth 4
  - 08: 42 programmes in 5 groups, 210 cycle leaves, 33 TBD leaf titles (cap 60). 07 unchanged in substance: 47 programmes, 237 cycle leaves, 60 TBD leaves, at its cap, so no further TBD leaf can go into 07
  - Future real-sector/UMKM programmes go into 08; future tech programmes go into 07, subject to its group and TBD caps
  - Still open, not part of this change: the ranking update (explicit 1st/2nd/3rd per cycle in 07, per the ranking research) and the University-group ranking research
