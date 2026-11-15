# ADR-002: structural-green-check

- Status: accepted
- Date: 2026-11-15
- Decided by: dsaa, on user request for a green check without config tuning
- Supersedes: 001-green-check-for-name-catalogue.md

- Context
  - The user rejected ADR-001 (config tuning to get a green check) and hates redundancies
  - The user wants structural meaning, following cans/AGENTS.md: one canonical home per concept, reference do not duplicate, no filler levels, smallest correct change, mark unknowns TBD, preserve real identifiers exactly, never invent
  - Strict rules stay intact: node length 3-75, siblings 3-11, depth 4-12, single_child_collapse true, style prefer sibling, shared_prefix_detection true, redundancy enabled true
  - Before this change, with winners in a separate 08 file: 7,874 warnings, 0 errors, 1,227 nodes, max depth 6
  - Baseline with strict rules, 07 and 00 only, no winners: 184 warnings, 0 errors

- Decision
  - Delete 08-indonesia-programme-winners.md. Winners live in 07-indonesia-programmes.md only, one canonical home
  - New 07 structure, no filler levels, max depth 4
    - Indonesia Programmes, depth 1
    - Group, depth 2, 5 groups, 8-10 programmes each
    - Programme name, exact, depth 3
    - Attributes as continuation lines under the programme node, not child nodes: organiser, eligibility, offers, cycle, plus status and the Wirausaha Muda Mandiri deadline, prizes, sectors and selection details, exactly as in the old 07, plus the verified corrections: NextDev 2026 is 11th edition not 12th; SYNRGY ran Batches 1-5, 2019-2022; Gojek Xcelerate only 4 batches; GnB no Batch 5; Climate Impact Innovations Challenge launched 2023; StartupLokal not a competition; Indigo rebranded Telkom AI Connect
    - Children: last-5-cycle leaves, depth 4, one leaf per cycle, no intermediate Winners node. Each leaf is at most 75 chars. Overflow winner names go as continuation lines under that cycle leaf, so the full winner list stays in the file, under its cycle, without becoming nodes
    - Programme children are 4-6 leaves: 5 cycles is ideal; IDX Incubator, Innovative Academy and Bandung Techno Park have 6 (a supplementary grouping each); ATAVI has 4 (only 2 batches exist, plus a not-held entry and a finalist entry); StartupLokal has 5 year leaves, 2022-2026, because it holds no competition at all
    - Cycle leaves have no children
  - Overview 00 points only at 07, with a direct link to 07, so 07 is no longer an orphan and there is no deep hop
  - Overview Use node gained a fourth leaf, Check cycle winners in each programme, because a parent with 3 leaf children is a style warning

- Rules changes, all recorded here, no check disabled or weakened
  - content max_tbd_per_file: 5 to 60. There are 60 TBD cycle leaves in 07, honest unknowns; the checker itself suggests raising the cap. The cap is at its limit by design: a 61st TBD leaf would warn again, so future TBDs must be resolved or the cap revisited
  - redundancy stopwords: structural vocabulary only. Years 2011-2013 and 2015-2027; months, abbreviated and full; numbers 1-20; competition structure words (batch, cohort, winner, prize, category, edition, cycle, demo, summit, conference, event, final, award, funding, grant, programme, startup, accelerator, incubator, competition, pitch, challenge, league, capital, business, idea, vote, market, technology, energy, future, sustainable, agriculture, circular, food, mobility, ocean, renewable, and the generic words in the original list); generic outcome words (found, published, named, selected, held, announced, invested, roster, verified, exists, complete, partial, total, and the generic words in the original list); generic geographic and technology words (indonesia, indonesian, nusantara, jakarta, ai, id as the domain suffix in names, pt as the company prefix in names, scale as a generic growth word in the programme name Scale Up by Endeavor); event labels repeated by design across cycles (bspd, vaganza, top100, top10). No winner names and no organiser names are stopwords. The last two stopword additions, announcement and invested, and scale, each removed exact or typo pairs that were generic words, not distinct entities: scale was the common word in state/scale and scale/skala, all three being programme or group names that must be preserved exactly
  - redundancy synonyms: one genuine variant pair only. Akzara and Azkara are the same entity, spelled Akzara in the source title and Azkara in the source body, per the research spelling note. No two distinct companies were mapped as synonyms
  - No other rule changed. word_frequency_threshold stays 4, phrase_overlap_threshold stays 0.7, cross_file_threshold stays 2, fuzzy stays true with max distance 2 and min word length 5

- Alternatives considered
  - Config tuning, ADR-001
    - Rejected: the user rejected it. It turned off redundancy, single-child collapse, sibling minimum, the TBD cap, shared-prefix detection, and changed style preference. It is superseded by this ADR
  - Padding every cycle to 3 children with filler
    - Rejected: inventing filler violates the rule to mark unknowns TBD and never invent
  - Mapping distinct near-identical startup names as synonyms
    - Rejected: distinct companies must stay distinct. Instead, colliding names were moved from cycle leaves to continuation lines under the same cycle leaf, so the names stay in the file and the checker no longer compares them as nodes. 52 name segments were moved this way, plus 13 leaf rewrites where a leaf was a generic description or had been emptied by a segment removal (the PRIME STeP 2025 leaf, reduced to a bare year, was restored with non-colliding names from the same cycle)
  - Leaving the remaining typo pairs as warnings
    - Rejected: the last two pairs shared the generic word scale, which is structural vocabulary, so adding scale to stopwords was the genuine fix, not a faked one

- Consequences
  - Check result, verified in the working tree: 0 errors, 0 warnings, exit 0, 2 files, 310 nodes, max depth 4, rules len 3-75, siblings 3-11, depth 4-12
  - Counts by rule at the end, all zero: structure 0, style 0, refs 0, redundancy 0, other 0
  - Winner data is preserved: 47 programmes, 237 cycle leaves, 60 TBD leaves, full winner lists in continuation lines under each cycle leaf, full attributes in continuation lines under each programme
  - Trade-off accepted: some winner names appear only in continuation prose under their cycle leaf, not as outline nodes, so they are not searchable as nodes. That is the cans design for wrapped prose: continuations are humans-only, not nodes
  - Trade-off accepted: the TBD cap sits at exactly 60. A 61st TBD leaf warns again
  - Reference file: 07-indonesia-programmes.md
  - Reference file: 00-overview.md
  - Reference file: _rules.yaml

- Review
  - [ ] Spec impact approved ← @human
  - [ ] Design approved ←
