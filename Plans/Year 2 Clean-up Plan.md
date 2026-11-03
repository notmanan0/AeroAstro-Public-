---
type: plan
status: in-progress
date: 2026-10-30
---

# Year 2 clean-up and upgrade plan

> [!check] Progress (30 Oct 2026)
> Phases 0 and 1 are done. The outstanding Year 2 work was committed as a snapshot (`c53821f`), and the SESA2028 hub was moved to the module root (`840f543`). The transcript indexes already existed for every module, so none were rebuilt, but the SESA2028 index leaves out the 43 ML mini-lecture videos. The prose pass is committed for SESA2027 (`366b7c0`, `f09abbe`), SESA2022 (`6c618ae`) and SESA2023 (`5e6c6c1`): 108 concept notes rewritten, 28 topic notes edited, and links, display equations and figure embeds checked. Phase 3 (SESA2024, SESA2029, SESA2028) is running in a background agent, which commits each block as it goes; SESA2024 and SESA2029 are committed.
>
> Phase 2 (MATH2048) is done. All 19 topic notes were rebuilt from the Lecture 1–30 transcripts, one block per commit: ODE (`237fee9`), FS (`56cd439`), TR (`dee5bee`), PDE (`4967a5d`) and VC (`f91f232`), with the hub and formula sheet in `c6018b0`. Every note follows the Year 3 template, has a transcript-slips table, works the relevant 2023/24–2025/26 exam questions, and has its numbers checked in SymPy. All 30 concept notes were rewritten, and there are new figure scripts for the TR, PDE and VC blocks.

The aim is to bring every Year 2 module up to the Year 3 standard in `CLAUDE.md` (what "good notes" means, plus the Writing style section added on 30 Oct). That means two different jobs depending on the module: some notes already have Year 3 depth and only need the prose pass that SESA3029/3043/3047 just had, while others are thin template notes that need rebuilding from the transcripts.

## Where each module stands

Measured over the topic notes on 30 Oct 2026. Year 3 reference (SESA3029): about 6,000 words per note, 6 bold phrases per 1,000 words, every note with a quick path and self-study list, transcript line references throughout.

| Module | Topic notes | Avg words | Bold /1k | Quick path | Self-study | Transcript refs | Transcripts filed | Verdict |
|---|---|---|---|---|---|---|---|---|
| SESA2022 Aerodynamics | 5 | 6,300 | 15 | 5/5 | 5/5 | 620 | 53 | Depth fine, prose pass |
| SESA2023 Propulsion | 11 | 4,400 | 18 | 11/11 | 11/11 | 520 | 28 (partial) | Depth fine, prose pass |
| SESA2027 Mechanics & Control | 12 | 4,600 | 16 | 12/12 | 12/12 | 720 | 23 | Depth fine, prose pass |
| MATH2048 Maths II | 19 | 980 | 21 | 0/19 | 0/19 | 0 | 50 | Rebuild, week by week |
| SESA2024 Astronautics | 15 | 1,100 | 30 | 0/15 | 0/15 | 0 | 35 | Rebuild |
| SESA2028 Materials & Structures | 19 | 1,400 | 28 | 0/19 | 0/19 | 0 | 112 | Rebuild (two streams) |
| SESA2029 Digital Methods | 28 | 1,400 | 24 | 0/28 | 0/28 | 0 | 38 | Rebuild (CFD, FEA, APDL) |

The thin notes are condensed summaries written from the slides: a bulleted abstract, a `## Key Concepts` list, numbered lists of bold claims, no derivations beyond the result, no worked examples checked against the lecture, no transcript use. SESA2022/2023/2027 already follow the Year 3 structure (and most of that work is still uncommitted), but they read like the pre-clean-up Year 3 notes: stock headings such as "The whole topic in one physical picture", heavy bold, a callout every few paragraphs (205 in SESA2027), and lecturer-said boxes that would read better as sentences.

## Phase 0: housekeeping (one short session)

1. Commit the existing uncommitted Year 2 work (89 files, mostly SESA2022/2023/2027) as a snapshot, so the prose pass has a clean diff to compare against. Year 2 paths only; leave `AGENTS.md`, `.obsidian/` and anything the Year 3 session is touching.
2. Build a transcript index for each rebuild module, like the one in `SESA2023 Propulsion/02 - Sources/Lectures/SESA2023 Transcript Index.md`: lecture number, date, lecturer, topic, which note it feeds. Several modules hold recordings from more than one cohort or duplicate uploads:
   - MATH2048: L1–L30 (Ian Hawke, about 5,000 words each) look like the main series, running ODEs → Fourier series → transforms → PDEs → vector calculus. There are also dated recordings from 2023, 2024 and 2025 to classify (other cohort, catch-up or revision).
   - SESA2028: dated recordings plus `ML1a…ML16d` and `SLx` mini-lectures that partly duplicate them.
   - SESA2029: dated recordings plus the combined `CFD.txt` and `FEA.txt`, and lab videos.
   - SESA2024: dated recordings plus pre-recorded chapter material and quiz walk-throughs.
3. Small fixes: move the SESA2028 hub to the module root (it sits in `01 - Notes/`), and decide the status mapping (see open decisions).

## Phase 1: prose pass on SESA2022, SESA2023, SESA2027

The same edit the Year 3 commits made (`4cce32f`, `fc77b22`, `69a004c`), applied one module per commit:

- abstracts cut to two to four sentences of prose;
- the stock physical-picture heading removed, keeping its paragraphs as the opening prose;
- bold down to defined terms (target under 8 per 1,000 words);
- callouts kept only for transcript slips, real traps, numerical checks and stand-alone intuition; "what the lecturer said" boxes folded into the text with their line references;
- numbered lists of bold sentences turned into paragraphs;
- concept notes rewritten as a short definition, a few paragraphs, then **Related**;
- hub and formula sheet tidied to match.

No content is dropped except repetition, and every derivation, example and line reference stays. While in each note, I'll also check scope against the transcripts and fill any gaps. SESA2023 is missing transcripts for lectures 3–15, so those weeks stay slide-based and the note says so.

Effort: about one session per module.

## Phase 2: MATH2048, week by week

MATH2048 is the first rebuild, as asked. Each week of lectures (about three transcripts) is one unit of work:

1. Read that week's transcripts and the matching chapter of `LectureNotesMATH2048.pdf` and problem sheet.
2. Rewrite the topic notes for that material to the Year 3 standard: abstract, quick path, physical or geometric picture in prose, full derivations one step per line (including what Hawke leaves as an exercise), worked examples from lectures with each answer checked in SymPy, transcript slips flagged with line numbers, and self-study tasks citing where each was set.
3. Use the existing `m2048_` figures and add new ones only for geometry or plotted behaviour (Gibbs, half-range extensions, eigenfunction shapes, flux surfaces), never for derivation text.
4. Update concept notes, the formula sheet, the tutorial-solution notes and the hub as each week lands.

The current block names (ODE1–3, FS1–3, TR1–3, PDE1–5, VC1–5) match the course's own chapters, so by default I'd keep them and add the lecture and week numbers to the frontmatter and section headings (see open decisions). That's about ten weeks of material, or three to four sessions at two or three weeks per session.

## Phase 3: rebuild SESA2024, SESA2029, SESA2028

The same week-by-week routine, in this order:

1. **SESA2024 Astronautics** (35 transcripts, 15 chapters). It's the smallest rebuild, and the orbital mechanics is derivation-heavy, which suits the routine. The two quiz walk-through transcripts become the self-study tasks. About three sessions.
2. **SESA2029 Digital Aerospace Methods** (CFD stream A, FEA stream B, APDL stream C). Streams A and B get the full treatment. The APDL notes C1–C6 are workflow notes and need little more than a prose pass and a check against the lab videos. The Navier-Stokes deep-dive note stays as it is. About four sessions.
3. **SESA2028 Materials & Structures** (112 transcripts, M and S streams). It's the largest, so it goes last. The S stream (S1–S11) is derivation-heavy and gets the full routine. The M stream is descriptive, so it needs fuller explanation, the case studies from the ML transcripts and the worked lifing and creep calculations, but few derivations. About five sessions.

> [!info] Phase 3 status (30 Oct 2026)
> All three modules are committed. SESA2024: every chapter rewritten (`da2485f` to `d59395a`). SESA2029: A1–A11 and B1–B10 rewritten in full, C1–C6 given a prose pass against the lab videos, concept notes restructured (`5c48a27` to `22cf986`). SESA2028: S1–S11 rewritten from the transcripts (S11 spinning discs marked `draft`, not lectured in 2025–26), M1–M8 given a structural pass (quick path, sources, self-study tasks) but not a full rewrite, concept notes moved to the concept format, formula sheet structures half put into course notation, ML mini-lectures added to the transcript index and the broken contact-sheet embed removed (`20be302` to `e911d17`). Still open: a full rewrite of M1–M8 from the ML transcripts with their numbers re-verified, and a hand rewrite of the scripted SESA2029 and SESA2028 concept notes.

## How each session runs

- Work only in Year 2 paths and commit only Year 2 paths, so this work never collides with the Year 3 session or the Thursday weekly job.
- Don't edit `CLAUDE.md`, `Templates/` or the weekly skill. They're shared with Year 3, and any change goes to you first.
- Year 2 figure scripts import `Year 3/_shared/year3_style.py` rather than forking it, so figures look the same across years. One script per topic in each module's `01 - Notes/Figures/`, with the existing prefixes (`m2048_`, `materials_`/`structures_`, etc.).
- Before each commit: check every wikilink, heading link and embed resolves, look at every new PNG, and recompute every worked-example number.
- One commit per module (Phase 1) or per week of material (Phases 2–3).

## Rough budget

| Phase | Sessions |
|---|---|
| 0 Housekeeping and transcript indexes | 1 |
| 1 Prose pass (2022, 2023, 2027) | 3 |
| 2 MATH2048 | 3–4 |
| 3 SESA2024 / 2029 / 2028 | 3 / 4 / 5 |
| Total | about 19–20 |

Thursday stays free for the Year 3 weekly job.

## Open decisions

1. **MATH2048 naming.** Keep the block names (ODE1…VC5) and work through them in lecture order (recommended, since links already point at them), or rename to `MATH2048 W0x - …` to match SESA3029?
2. **Status values.** Year 2 notes say `status: complete`, which isn't in the current vocabulary. Proposal: rebuilt and prose-passed notes become `lectured`, and you promote any you've already revised.
3. **Snapshot commit.** OK to commit the existing uncommitted Year 2 changes as the Phase 0 snapshot?
4. **Order.** Prose pass first (fast, visible improvement), then MATH2048, or MATH2048 first?
