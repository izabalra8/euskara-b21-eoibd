# Euskara B2.1 — EOI Drassanes · Decisions log
**Instructor:** Eñaut Arretxe · **Course:** EOI Barcelona-Drassanes  
**Project file:** `euskara-b21-eoibd.html` (single-file self-contained app, renamed from `euskara-b21-unitatea01.html` in Session 5 once the app covered multiple units, not just Unit 1)  
**Drag this file into any new session to restore full context.**

---

## ⚡ Portable UX decisions — copy this block to other study-app conversations (e.g. Arian B1.2)

These apply to the app design regardless of unit/content:

1. **Flashcard buttons: only 2.** 😕 Berriz (wrong → marks 🔴 difficult) and 👍 Ongi (correct). No "Erraza" skip button.
2. **Keyboard shortcuts:** Space OR Enter = flip card; after flipping, ArrowRight = Ongi/correct, ArrowLeft = Berriz/wrong. Applies to practice flashcards AND exams. Show the hints in the UI.
3. **Exam (Azterketa) format:** flashcard self-report, not multiple choice. Show front → click/Space to flip → user reports ✓/✗. Pressing ✓/✗ records AND advances immediately — no feedback screen, no "next" button.
4. **Exam content mix:** ~6 vocabulary + ~4 grammar cards, uniform random sampling (never SRS-weighted, so scores stay comparable). Vocab answers feed the SRS; grammar answers count for score only.
5. **Grammar vs. Idazlana:** communicative formulas (opinion, agreement...) are NOT grammar — they go in "Idazlana eta ahozkoa" (tag `use:'idazlana'`). Gramatika holds only structural grammar (verb paradigms, subordination...).
6. **Aditzoina notes:** where aditzoina applies (ahalera, agintera), open the explanation with the pattern "Etor<s>ri</s> zaitez(ke)" — participle ending struck through in red.
7. **Opinion formulas: mark the -(e)la rule.** Verb-initial formulas (uste dut, iruditzen zait, argi dago) take subordinate verb + -(e)la; adverbial ones (nire ustez, dirudienez) take a normal verb. Write the suffix on the formula itself ("Uste dut ...-(e)la").
8. **Notebook vocabulary** goes in its own section (KOAD · Koadernoa 📓) with non-numeric page label, so textbook sections keep clean page references. Always dedupe against existing `eu` keys first.
9. **Vocabulary rules:** lemma form only; no obvious Spanish-Basque cognates; no hika forms anywhere.
10. **Sidebar: no "Atalak" group.** Only one nav group ("Baliabideak"): Hasiera, Nire maila, Hiztegia, Gramatika, Idazlana eta ahozkoa, Ariketak, Azterketa, Lan autonomoa. Per-section buttons removed from the sidebar — sections are reached via the cards on the Hasiera page.
11. **Azterketa: no Historia card.** Only the KPIs and the Bilakaera chart.
12. **Bilakaera chart: points + connecting line,** not bars. Points colored by score (green ≥80%, yellow ≥50%, red <50%), score labeled above each point, date below, turquoise line linking them.
13. **Standing instruction: every decision taken in a session gets written to this decisions file immediately.**
14. **Baldintza Motak table: highlight aspect suffixes in fuchsia caps.** Etor**TZEN** banaiz / Etorri**KO** banintz / Etorri **∅** banintz — the -tzen/-ko/bare-participle contrast is the point of the table; ondorioa always ikasi**KO** (dut/nuke/nukeen).
15. **Explanations: minimal.** No introductory sentences ("Hiru mota daude...", definitions) — go straight to the pattern/rule. Same spirit as the aditzoina one-liners.
16. **Baldintza entry structure:** no top explanation. Order: "Baldintza motak" label + Motak table → "Baldintza hipotetikoa" label + 2 bullets (ba-/-ke rule; D→Z→L trick) → IZAN table → UKAN table. `tables[]` entries support `html` (content blocks without a table) for interleaving notes between tables.
17. **Ondorioa merged into IZAN/UKAN tables as a 4th column** ("Ondorioa (-ke)"), not a separate table. Same pattern for any future paradigm with baldintza+ondorioa pairs — one row per person, all forms side by side.
18. **Ahalera table: single UKAN column,** not split sing./pl. Header just "UKAN" (not "UKAN sing. (dezaket)"), cell shows both forms as "dezaket / ditzaket". Same for IZAN header — no parenthetical example form in the column title.
19. **Baldintza hipotetikoa bullets: 3rd point added** — "Baldintzan aditza + -ko/-go, ondorioan aditza + -ko/-go" with the n/l→-go, otherwise→-ko allomorphy rule and examples (etorriko banintz / joango banintz).
20. **Conjugation tables: person/pronoun only in the first column.** Don't repeat "Ni/Zu/Hura..." in every column — IZAN and UKAN baldintza tables both follow this (matches the NOR-NORK tables' convention too).
21. **Ariketak: exercises split by skill tag,** not lumped under "Gramatika lantzeko". `iritzia-mc` re-tagged `skill:'idazlana'` (was 'gramatika') since its content moved to Idazlana eta ahozkoa. vAriketak now renders two cards: "📐 Gramatika lantzeko" (skill≠'idazlana') and "✍️ Idazlana eta ahozkoa lantzeko" (skill==='idazlana', only shown if non-empty). Any future idazlana exercise must use `skill:'idazlana'` to land in the right card.
22. **New Gramatika entry: `zerk-kasua`** (ZERK kasua — nominalized clause as NORK). From class notes: aditzoina+-tze+-a→-tzea, +-k→-tzeak; used with feeling-causing verbs (sentiarazi, poztu, alaitu, haserretu...). Examples color-code the cases inline: NORK=fuchsia (var(--accent)), NOR=green (var(--success)), NORI=turquoise (var(--primary)) — this color convention should be reused for any future NOR/NORI/NORK case-marking example.
23. **Iritzia emateko formulak: explanation reduced to 2 bullets** (no intro sentence) — same "explanations: minimal" rule (#15) applied here too. Groups expanded with more formulas from class notes: "aditz normala" gained Agian/Beharbada; "+ -(e)la" gained Apustu egingo nuke / Lepoa jokatuko nuke / Esango nuke; new group "Ziurgabetasuna · + -t(z)ea" added for Baliteke (different suffix pattern — nominalization, not -ela).
24. **New Idazlana entry: `kausalak`** (title: "Kausalak", subtitle: "Zergatik zaude hemen?" — matches notebook heading verbatim) — causal connectors eta/-lako/bait-/-(e)nez gero/-gatik, all demonstrated on the same base sentence ("asko gustatzen zait") so the contrast between connectors is clear.
25. **Kausalak: no top explanation.** Removed the intro bullets (connector list + -gatik note) — entry goes straight from title/subtitle into the groups/examples. Same "explanations: minimal" rule (#15); `gramHTML` already handles a missing `explanation` field gracefully.
26. **NOR-NORK orainaldian + NOR-NORK lehenaldian merged into one entry** (`id:'nor-nork'`, title "NOR-NORK", subtitle "Conjugación transitiva: presente eta pasado"). Uses `tables[]` with two labeled blocks (Orainaldia, Lehenaldia), each carrying its own explanation via `html` + its own 6×6 table, in that order. Examples combined into one array, orainaldia's 3 first then lehenaldia's 3, each tagged "(orainaldia)"/"(lehenaldia)" in the Spanish gloss. General pattern for merging two time/aspect variants of the same paradigm into one entry.
27. **Agintera and Ahalera each got a clarification bullet:** "Agintera → Ahalera (Potentziala) → Subjuntiboa" — just the chain, no label or explanatory clause. Added as the last `<li>` in each entry's explanation `<ul>`.
28. **Fixed "too much color" readability problem in Idazlana/examples.** Root cause: `.wpill b` and `.gex-eu` forced every single Basque phrase to bold turquoise, so nothing stood out — highlighting only works as contrast against a neutral base. Fix: `.gex-eu` base color → var(--text) (highlighted words still pop via existing `.gex-eu b` turquoise+pill). `.wpill` no longer force-wraps the whole phrase in `<b>`; new `.wpill-eu` class is bold but neutral-colored, and only text explicitly wrapped in `<b>` inside the item data (e.g. the `-(e)la`/`-t(z)ea` suffix) gets fuchsia highlight (`var(--accent)`, matching the aspect-suffix convention from rule #14). **Standing rule: color = contrast tool, not decoration — always leave a neutral majority of text so the highlighted part is the one your eye lands on.** Applied retroactively to the Iritzia emateko formulak groups.
29. **New `light:true` flag for `tables[]` entries** renders a light cream background (`#f4f1ea` bg, dark text) instead of the default dark card table — `.gtable.light` CSS class. Applied to the Baldintza Motak table so the TZEN/KO/∅ fuchsia highlights stay legible on a lighter surface. Use this flag for any future table where the highlighted colors need a light backdrop to pop.
30. **Bug fix: `ahalera-gap` exercise mixed two valid-but-different constructions.** Items 1 and 5 had "aditzoina + ahal + potential aux" ("bidaiatu ahal naiteke/zaitezkete") — redundant, since "ahal" (periphrastic possibility) and the synthetic -ke potential aux both mark ability; you use one or the other, not both. Standard alternatives: (a) potential aux alone — "Bidaiatu naiteke" (puedo viajar), or (b) ahal + plain aux — "Bidaiatu ahal naiz" (soy capaz de viajar). Fixed by dropping "ahal" from items 1 and 5, matching items 2–4 which already used the clean potential-aux-alone pattern taught in the Ahalera grammar entry. This exercise feeds both Ariketak and Azterketa (via buildExamCards' gap-mc sourcing), so the fix propagates to both automatically.
31. **Removed `txistu` (flauta vasca) from vocabulary** at user's request.
32. **Correction to Baldintza Motak, row 3 (Lehenaldiko baldintza):** changed "Etorri ∅ banintz" to "Etorri ∅ *(izan)* banintz". This resolves an earlier ambiguity flagged mid-session: bare participle + banintz alone (no izan) is actually usable for BOTH present-unreal (bizi banintz = si viviera) and past-unreal readings, so it doesn't reliably signal Type 3 on its own. Inserting **izan** between the participle and banintz ("etorri izan banintz") is what actually marks the analytic pluperfect/past-unreal reading in the baldintza clause itself — the ondorioa's -keen (nukeen) alone isn't the full story. Rule #19 (the -ko/-go bullet) still stands for Types 1–2 but should not be read as a strict Type-2-vs-3 discriminator; that job belongs to izan-insertion (baldintza clause) + -keen (ondorioa clause) together.
35. **New section: Mnemotekniak** (🧠, new top-level Baliabideak entry, storage key `b21_01_mnemo`). Fully user-editable — no pre-written per-word mnemonics, only a general strategies card (phonetic similarity, image/story, word-splitting, rhyme). Word source = `hardWordsList()`: union of manually-marked 🔴 difficult words + statistically hardest words (same accuracy-sort logic as vMaila), deduped, difficult-flag words first. Each word gets a textarea + "Gorde" button; empty text deletes the key on save. Nav count shows saved-mnemonic count once any exist, else the hard-word count as a nudge.
38. **Mnemotekniak simplified: removed the intro paragraph, the "sortzeko ideiak" tips card, and the "🔴 Zure hitz zailak" card header** — page now goes straight from the title into the word rows, no explanatory scaffolding. Added a per-word **✕ Kendu zerrendatik** (dismiss) button using the existing `.vab` style; dismissing a word adds it to `MNEMO_SKIP` (storage key `b21_01_mnemo_skip`), and `hardWordsList()` now filters against that set so dismissed words never resurface as suggestions again (their saved mnemonic text, if any, is left untouched in `MNEMO`).
41. **Azterketa exam length is now selectable: 10/20/40 questions**, via `examLenChips()` (same visual pattern as `lenChips()` for flashcards), stored as `EXAMLEN` in `b21_01_examlen`. `buildExamCards(n)` scales to ~60% vocab / ~40% grammar of the target `n`, and tops up with extra unused vocab if the grammar pool runs short (grammar pool is small and fixed, so 40-question exams lean more vocab-heavy — expected, not a bug).
42. **Added `MNEMO_SUGGEST` — optional pre-written mnemonic suggestions,** keyed by `eu`, shown as a pre-filled (but unsaved) textarea value with a "💡 Iradokizuna" label when the user hasn't written/saved their own yet. First entry: `musutruk` → real etymology (musu=beso + truk=trueke, "a cambio de un beso") since it's a stronger memory hook than an invented association. This supersedes rule #35's "no pre-written content" for specific words the user explicitly asks to have filled in — the mechanism is additive/optional, never overwrites a saved `MNEMO` entry.
40. **Mnemotekniak word source: `hardWordsList()` now sorts the union of manually-flagged 🔴 + statistically-hard words together by failure rate** (accuracy ascending, then wrong-count descending), instead of showing all 🔴-flagged words first as an unsorted block followed by the sorted statistical ones. Words with no reliable accuracy (null, e.g. flagged but under-tested) rank at the very top as worst-case. Standing convention: any future "hardest words" list should merge candidate sources into one array before sorting, not sort each source separately and concatenate.
39. **"Euskal Herrian (bizi izan)" exercise restructured so the ondorioa is also tested, not just shown for free.** Previously the sentence displayed "...jaiak gehiago ezagutuko nituzke" in plain text, so only the baldintza clause was being graded. Now the whole clause is a single blank: sent = "Euskal Herrian (bizi izan) _____." blank = "biziko banintz, jaiak gehiago ezagutuko nituzke", with 3 full-phrase wrong options mixing up -ko/-go, banintz vs izango banintz, and the ondorioa aux (nuke/dut vs nituzke). Note: `drawGapMc`/`gapPick` only support one blank + one flat opts array per item — this is the pattern to reuse whenever a question needs both the baldintza and ondorioa graded together (bundle into one long blank+options rather than trying two separate blanks).
37. **Bilakaera chart recolored: gradient instead of red/yellow/green semantic colors.** New `pctColor(pct)` interpolates deep indigo (0%, rgb(91,42,134)) → marine blue (50%, rgb(37,99,172)) → turquoise (100%, rgb(0,229,196)), so higher scores are both higher on the Y-axis AND brighter/more turquoise — position and color reinforce each other. The connecting line uses a matching SVG `linearGradient` (`#azterLine`, same 3 stops, vertical). Applies to azterChart() points and line; grid/axis labels unchanged (still `var(--border)`/`var(--muted)`).
36. **Baldintza-gap exercise item for "bizi izan" restructured with an explicit infinitive hint:** "Euskal Herrian (bizi izan) _____, jaiak gehiago ezagutuko nituzke." with blank = full phrase "biziko banintz" (not just one piece), testing the whole construction instead of leaking half of it via the sentence shape. Kept **nituzke** (not "nuke") since jaiak is plural — flagged to user, not silently changed.
34. **Bug fix: Kausalak connector items leaked the answer into their own flashcard front.** In Azterketa, idazlana group cards use `front:item.es, back:item.eu`. The Konnektoreak items had the connector name written inside the `es` gloss's parentheses ("...porque (-lako, atzizkia)."), so the front of the card literally contained the back's answer. Fixed by keeping the category hint (position/register: "esaldi bukaeran", "atzizkia", "aurrizkia, jasoagoa") but removing the literal connector word from all `es` fields in that group. **Standing rule: never name the target word/suffix inside an item's `es` field** — that field becomes flashcard front verbatim; category hints are fine, literal answers are not.
33. **Correction: light-verb compounds (bizi izan, nahi izan, behar izan...) take -ko/-go on the LEXICAL part, not on "izan".** Standard forms: nahiko dut (not "nahi izango dut"), beharko dut (not "behar izango dut"), biziko naiz (not "bizi izango naiz"). "Izan" stays bare as the auxiliary. Fixed the Baldintza hipotetikoa example from "Euskal Herrian bizi banintz..." to "Euskal Herrian biziko banintz...", and the matching `baldintza-gap` exercise item (blank changed from 'banintz' to 'biziko', sentence restructured so the blank targets the verb not the auxiliary) — this exercise also feeds Azterketa via buildExamCards, so the fix propagates there too. Supersedes the "bizi izango banintz" suggestion floated earlier in the same session — that was wrong for this verb class.
43. **Removed the whole "Lan autonomoa" section** at user's request: sidebar nav button (`n-lan-autonomoa`), the `'lan-autonomoa'` entry in `renderChrome()`'s toggle array, the `render()` routing line, the `LAN_AUTONOMOA` data array (6 session objects), and `vLanAutonomoa()`.
46. **Removed the `eskozian-tf` exercise** ("Oporrak Eskozian", 10-item egia/gezurra) at user's request — it tested comprehension of a Moodle audio listening exercise whose transcript was never added to the app, so it was unanswerable from app content alone. Standing rule: any future listening/reading-comprehension exercise needs its source text or audio embedded in the app, or it shouldn't be built as a quiz here.
47. **Multi-unit architecture added.** The single `const UNIT={...}` became `const UNITS=[{...}]` (an array of unit objects); `let UNIT` is a mutable pointer reassigned by `switchUnit(idx)`. Every unit object needs a unique `key` (storage prefix, e.g. `'b21_01'`, `'b21_02'`) and `num` (display number, e.g. `'02'`) in addition to the existing schema (level/title/intro/objectives/sections/vocabulary/grammar/exercises). All storage — progress (`P`), session log (`LOG`), exams (`EXAMS`), mnemonics (`MNEMO`/`MNEMO_SKIP`), exam length (`EXAMLEN`), session length/direction (`LEN`/`DIR`) — is namespaced per unit via `uk(suffix)` = `UNIT.key+'_'+suffix`, loaded/reloaded by `loadUnitState()`. **Decision: progress is fully separate per unit** (user's explicit choice over a shared/global pool) — switching units gives a clean SRS slate, separate exam history, separate hard-word list. Only the "which unit is currently open" preference (`b21_active_unit`) is global, not per-unit.
48. **Navigation: unit selector at top of sidebar (Recommended option, user's choice)** — a `<select id="unit-sel">` replaced the old static `#unit-title` div, populated by `renderUnitSelector()` from `UNITS`. Every section (Hiztegia, Gramatika, Idazlana, Ariketak, Azterketa, Mnemotekniak) automatically filters to the active unit because they all read from `UNIT.*` (unchanged), not a hardcoded unit. `SECLBL`/`SECICON` (hardcoded per-section-id maps) were replaced with `secLbl(id)`/`secIcon(id)` helpers that read `label`/`icon` straight off `UNIT.sections` — each section now needs an `icon` field. `document.title` and the "UNITATEA `${UNIT.num}`" tag on Hasiera update on switch via `updateUnitChrome()`.
50. **Bilakaera chart simplified: removed the per-point "score/total" text label and the 0/5/10 solid axis grid** (both felt like clutter) — now just the colored points + connecting line, plus a single dashed reference line at the 50%-correct mark (`stroke-dasharray`, muted/translucent) so it's easy to see at a glance whether an exam landed above or below half. Date labels under each point stay. Standing rule: keep this chart minimal — data-as-position/color, not data-as-numbers.
51. **Bilakaera chart: added plain solid lines at the 0% and 100% edges** (top and bottom of the plot area, `var(--border)`, no dasharray) — frames the range so the dashed 50% line in the middle reads as a threshold rather than floating with nothing to anchor it against. No numeric labels on any of the three lines, per rule #50.
53. **Added `ekin` (afrontarse, acometer; dedicarse a, ponerse a) to Hiztegia**, KOAD section — came up while building a mnemonic for `etekin` (see mnemonic-related notes above); confirmed via web search that `ekin` is a real, common Basque verb (e.g. "bideari ekin" = ponerse en camino, "ekin eta jarrai" = perseverar y continuar), not the invented "-kin = con" hook used for `etekin`'s current mnemonic. That mnemonic is still flagged as invented in the app; `etekin`'s real link to `ekin` (benefit = what striving/effort yields) is more plausible but unconfirmed — no update made to the mnemonic text itself yet.
54. **Unit 2 ("Euskara eta biok") added as `UNITS[1]`** (key `b21_02`), built from the uploaded Moodle unit-planning PDF (28 pages, text-extractable, no OCR needed). Sections: 02a Harremanaren hasiera, 02b Euskarak sentiarazten didana, 02c Biziraungo al dugu?. Grammar entries: -arazi (causative), nominalizazioa (-tzea/-tzen/-tzeari/-tzeak), NOLA vs NOLAKOA, BEZALA vs BEZALAKOA, konparaketak (bezain/bezainbeste/adina/baino), instrumentala (-z), menpeko esaldiak overview. ~29 vocabulary words from explicit "Hiztegia" callouts + reading passages. **Deliberately skipped:** the PDF's page-21-28 appendix drill bank (worksheets with blanks but no answer key visible in the PDF) and the two listening/reading-comprehension exercises (Bidaia Intimoak, Martxelo Otamendi egia/gezurra) per rule #46 (no source text/audio in the app = not answerable). Superseded in part by rule #55 below — an answer key for the appendix bank was found after this unit was built.
59. **Baldintza erreala→hipotetikoa exercises show ONLY the real-conditional sentence, never a partial hypothetical reveal.** `sent` has no `_____` placeholder and no arrow/second sentence — just the real sentence as-is; `blank` is the FULL correct hypothetical sentence (both clauses), tested against 3 full wrong-sentence distractors. `drawGapMc`'s `.replace('_____',...)` silently no-ops when there's no placeholder, so the sentence just displays unchanged with the MC options below — that's the mechanism, no code change needed. Standing rule for **all** baldintza erreala→hipotetikoa transformation-drill items (not the single-blank `baldintza-gap` exercise, which stays as-is): don't give away the target structure, make the student produce/recognize the whole transformed sentence.
60. **Unit 2 grammar/exercises enriched using the Desktop JSON answer keys + notebook photos**, now that rule #55's missing answer key is resolved: added `nor-nori-nork` grammar entry (orainaldia + lehenaldia tables, own-verified against standard paradigm, cross-checked against the photographed notebook table), a `-TZERA` row to the nominalizazioa table (goal/purpose nominalization: joan/etorri/ausartu + -tzera), and four new exercises — `nola-nolakoa-gap-02`, `konparaketak-gap-02`, `menpeko-gap-02` (all gap-mc, answers straight from the verified JSON files), and `menpeko-mota-02` (mc, erlatiboa/konpletiboa/zehar-galdera classification) built from a photographed classroom worksheet by independently analyzing each sentence's grammar rather than trying to read faint red grading marks — safer than guessing at ambiguous marks in a photo.
55. **Found a local folder of pre-made, mostly-verified grammar exercises: `~/Desktop/euskara/gramatika`** (JSON files per topic — nor_nork, nor_nori_nork, baldintza_hipotetikoa, ahalera, nominalizazioa, arazi, nola_nolakoa, konparazioak, menpeko, errelatiboa, trinkoak — plus some .docx/.html reference files). This is a much better source than re-deriving exercises from scratch: it supplies the answer key that was missing for Unit 2's PDF appendix drills. **Caution — not error-free:** `baldintza_hipotetikoa/01_ondorioa.json` has a wrong UKAN-ondorioa "zu" form ("zuk lukezu/lituzkezu" — should be "zuk zenuke/zenituzke", per the already-verified table in Unit 1 rule and confirmed independently by the teacher-corrected worksheet in rule #56). Standing rule: cross-check anything pulled from this folder against Unit 1's verified paradigm tables (or a teacher-corrected source) before using it as an answer key — don't import silently.
56. **Added `baldintza-erreal-hipotetiko` exercise to Unit 1** (gap-mc, section 01a) from a photographed, teacher-corrected homework worksheet (baldintza erreala → hipotetikoa transformation, 8 items). Used the 7 items with legible corrections (1,2,3,5,6,7,8); item 4 ("Taberna hori ixten badute...") skipped — the correction was illegible in the photo, not guessed. Feeds Azterketa automatically via the existing gap-mc → exam-card pipeline, no extra wiring needed.
57. **Vocabulary dedupe caught twice this session: `irmo` and `hizlari` were both already in Hiztegia** when the user asked to add them again (as "irmoa"/"hizlaria" — declined forms) — kept the existing lemma-form entries, only enriched `hizlari`'s gloss with "conferenciante". Reinforces rule #4 (dedupe check) and rule #1 (lemma form only) — always grep the `eu` key before adding, even when the user's phrasing suggests a "new" word.
58. **New instruction: extract vocabulary "as if at a B1 level"** — when mining source material (PDFs, Moodle, notebooks) for vocabulary, don't just flag advanced/unfamiliar B2 words; also include foundational words a B1 learner (not yet B2) might not know. Broadens rule #2 (no *obvious* cognates) without replacing it — the bar for "obvious" should assume a B1 baseline, not B2. Applies going forward to any vocabulary extraction pass, including a planned fuller re-pass over the original Unit 1 PDF (`1. IKASTUNITATEA 25-26.pdf`) that hasn't been fully mined yet.
52. **Fixed gap-mc → Azterketa grammar flashcards showing an uncontextualized "Erantzuna."** `buildExamCards()` used to set the flashcard back to the bare `item.blank` fragment alone — fine for short blanks (front already gives strong context), but unusable for full-clause blanks like the "Euskal Herrian (bizi izan) ___" item, where flipping revealed just "biziko banintz, jaiak gehiago ezagutuko nituzke" with zero visible link back to the question (card flip hides the front face entirely — you can't see both sides at once). Fixed by making the back the **full completed sentence** (`item.sent` with `_____` replaced by `<b>${item.blank}</b>`), not just the bare blank — the answer is now always self-contained and shows what's being tested even in isolation. Applies to every gap-mc-sourced grammar flashcard, not just this one item.
49. **Recipe for adding unit 02 (or any new unit):** append a new object to `UNITS=[...]` with the same shape as unit 01 (`key`, `num`, `level`, `title`, `intro`, `objectives[]`, `sections[]` — each needs `id`/`label`/`icon`/`title`/`pages`/`desc` — `vocabulary[]`, `grammar[]`, `exercises[]`). No other code changes needed — the sidebar selector, all six section views, exams, and progress tracking pick it up automatically. Follow rules #1–#46 (vocabulary hygiene, grammar-vs-idazlana tagging, exercise shuffling, etc.) for the new unit's content same as unit 01.
44. **Ariketak: "Hurrengoa →" manual-next button removed everywhere — answering now auto-advances.** Applies to all four static exercise flows that had it: `gap-mc` (`gapPick`), `mc` (`mcPick`), `truefalse` (`tfPick`), and the vocabulary quiz (`quizPick`). Each now shows the same right/wrong feedback as before, then calls `exNext()`/`quizNext()` via `setTimeout(...,1100)` — no click required. This matches the standing pattern already used by practice flashcards (`fcAns`) and Azterketa (rule #3) and match-pairs (`matchClick`); those three needed no change.
45. **Exercises now shuffle on every playthrough, so the correct answer isn't always option 1 and questions aren't always in the same order.** `startEx(id)` clones the exercise and shuffles `items`/`q` (`Math.random()-.5` sort) once per session; `drawGapMc` and `drawMcEx` additionally shuffle each item's `opts` array before rendering (matching against the stored correct value, not position, so this is safe). Fixes `iritzia-mc` and `baldintza-gap`, and applies generically to any future `gap-mc`/`mc` exercise — the vocabulary quiz (`drawQuiz`) already shuffled its options and is unaffected.

---

## App architecture

Single HTML file, no dependencies, no build step — opens from `file://`.  
All logic, CSS, and unit data live in the one file.  
Progress stored in `localStorage` with in-memory fallback (`STORE_OK` flag for Safari on `file://`).

**Storage keys:**
| Key | Contents |
|---|---|
| `b21_01_progress` | SRS word records `{lv, seen, right, wrong, streak, last, due, f, d}` |
| `b21_01_log` | Session log `{sessions, reviews, right, lastSession}` |
| `b21_01_exams` | Exam history array `[{date, score, total, secs, pct}]` |
| `b21_01_len` | Flashcard direction preference |
| `b21_01_dir` | Sort/filter preference |

---

## Visual theme — neon/cyberpunk

Fonts loaded from Google Fonts:
- **Display / headings:** `Orbitron` (logo, section titles, card-h, modal title, table th, KPI numbers, nav labels)
- **Body:** `Jost` (all body text, buttons, inputs)

CSS variables:
```css
--bg: #080c10          /* near-black background */
--sidebar: #05080b     /* sidebar */
--card: #0d1117        /* card background */
--primary: #00f5c8     /* neon turquoise — main interactive color */
--primary-dark: #00c9a4
--accent: #ff0080      /* electric fuchsia — badges, highlights */
--success: #39ff7a     /* neon green */
--danger: #ff2255      /* neon red-pink */
--text: #d8e4f0
--muted: #4a6070
--border: #141e28
```

Body font-size: **17px**. Key sizes: nav links 15px, card-h 15px, vocabulary words 17px, page title 26px, flashcard word 32px.

Glow effects: logo (`text-shadow: 0 0 18px rgba(0,245,200,.5)`), active nav (`box-shadow: inset 0 0 20px rgba(0,245,200,.04)`), card hover (`box-shadow: 0 0 24px var(--glow-c)`), progress bar fill (`box-shadow: 0 0 6px var(--primary)`).

---

## Content sources (Unitate 01)

| Source | Access | Content used |
|---|---|---|
| Moodle book id=583257 | `https://agora-eoi.xtec.cat/eoibdrassanes/moodle/` | 6 Klase Birtuala chapters + 6 Lan Autonomoa chapters |
| PDF "1. IKASTUNITATEA 25-26.pdf" | Uploaded by user | Oinarrizko hiztegia (p.8) + turismo vocab (pp.10-12), grammar summary |
| Elhuyar dictionary | `https://hiztegiak.elhuyar.eus/` | Lemma verification for uncertain forms |

Moodle navigation: use Claude in Chrome + JavaScript `.click()` on nav links (query-string hrefs are blocked by the extension). Log in first via Chrome, then retry.

## Content sources (Unitate 03) — standing instruction

**Always use Claude in Chrome to browse Moodle for new units — don't ask permission first, just navigate.** Moodle has no dedicated MCP connector, so browser automation is the only path in.

| Source | Access | Content used |
|---|---|---|
| Moodle book id=598216 | `https://agora-eoi.xtec.cat/eoibdrassanes/moodle/mod/book/view.php?id=598216&chapterid=59096` | Unit 3 "Bada, ez bada" — klase-birtuala chapter log (mintzamena/sare sozialak, ZAIT-type nor-nori verb morphology, hitanoa/hika register) |
| PDF "3. ikastunitatea B2.1.pdf" | Uploaded by user | Main unit 3 source material |

Confirmed working 2026-08-13: navigated directly to the chapterid URL above, `get_page_text` returned full chapter content with no login prompt (session already authenticated in the connected browser). This book module likely has multiple chapters/sections — check the book's table of contents for sibling chapters before assuming this one URL is the whole unit.

---

## Section structure

```
SECLBL  = {all:'Guztiak', atarian:'ATARIAN', '01a':'01A', '01b':'01B', '01c':'01C'}
SECICON = {atarian:'🌞', '01a':'✈️', '01b':'🎉', '01c':'🏙️'}
```

**Sidebar nav order:** Hasiera → [section cards] → Nire maila → Hiztegia → Gramatika → Idazlana eta ahozkoa → Ariketak → Azterketa → Lan autonomoa

---

## Vocabulary rules — strictly enforced

1. **Dictionary/lemma form only.** No declined endings — e.g., `mendizaletasun` not `mendizaletasuna`.
2. **No obvious Spanish-Basque cognates.** Words removed: `turista, turismo, paisaia, abentura, esperientzia, autostop, kanpin, pasaporte, maleta, aireportu, kontsumitu, pribilegio, kalitate, masifikazio, ekonomia, tradizio, bidaia-agentzia, kultura`. Rule: if the Basque word looks very similar to the Spanish one, remove it.
3. **B1.1/B1.2 level target.** Include rich vocabulary; don't be shy about quantity.
4. **Duplicate key check.** `vocabulary[].eu` is the SRS progress key — two entries with the same `eu` silently merge records.
5. Use Elhuyar dictionary to verify uncertain lemma forms before adding.

---

## SRS algorithm constants

```js
const IVL       = [0, 1, 3, 7, 16, 35];               // days by level; lv>=3 = learned
const STREAK_K  = [1, 0.95, 0.8, 0.25, 0.15, 0.08];  // weight multiplier by streak

// correct: lv+1 (max 5), streak+1, clears 🔴 flag if streak>=3
// wrong:   lv-2 (min 0), streak=0, sets 🔴 flag if hard=true
// isDue(): uses end-of-day comparison, not timestamp — a word due today is due all day
```

Exam sampling: **uniform** (not weighted) so scores are comparable across attempts.  
Practice sampling: **weighted** (weak words appear ~28× more than mastered words).

---

## Grammar section rules

Grammar entries tagged `use:'idazlana'` appear in **Idazlana eta ahozkoa**, not in Gramatika.

**Current idazlana entries:**
- `id:'iritzia'` — Iritzia emateko formulak (opinion / agreement formulas)

**Gramatika entries** (structural grammar only):
- Baldintza hipotetikoa (conditional)
- Agintera (imperative) — **hika forms removed** (ezak/ezan/hadi rows deleted)
- Ahalera (modal: capability)
- NOR-NORK lehenaldian (past transitive)
- NOR-NORK orainaldian (present transitive)

---

## Ariketak (exercises)

Shows only `skill:'gramatika'` and vocabulary flashcards. Does not show `skill:'idazlana'` exercises.

Current exercises:
- `baldintza-gap` — gap-mc (fill blank), section 01a
- `iritzia-mc` — mc (multiple choice), section 01b, skill:'gramatika'
- `agintera-gap`, `ahalera-gap`, `nor-nork-gap` — (add if created)

---

## Azterketa (exam)

**Format:** Flashcard self-report — show front, click to flip, user reports ✓ or ✗. No multiple choice.  
**Mix:** ~6 vocabulary cards + ~4 grammar cards per 10-card exam.  
**Sampling:** Uniform (not weighted) for comparable scores.  
**SRS feed:** Vocab answers feed `rec()`. Grammar answers counted for score only.

Grammar card sources:
- `gap-mc` exercise items: front = sentence with `_____`, back = correct verb form
- Grammar group items (`use:'idazlana'`): front = Basque formula, back = Spanish

---

## Lan autonomoa

6 sessions, displayed most recent first (session 1.1 = latest).  
Each session: `{date, gram, vocab:[], tasks:[]}`.  
**No songs** — removed at user's request. Keep: grammar theory, some exercises, vocabulary.  
Dates: session 1.1 (10/28) → session 6.1 (09/23).

---

## Decisions log

| Date | Decision |
|---|---|
| Session 1 | Built from index.html Arian B1.2 format, not from Moodle klase birtuala HTML |
| Session 1 | Removed hika forms everywhere (ezak/ezan/hadi rows from agintera table) |
| Session 1 | Removed songs from Lan autonomoa |
| Session 2 | Vocabulary enriched significantly — target B1.1/B1.2 level, no shy about quantity |
| Session 2 | All vocabulary in dictionary/lemma form |
| Session 2 | Removed obvious cognates (see list above) |
| Session 3 | Full visual redesign: neon/cyberpunk (black + turquoise + fuchsia), Orbitron + Jost fonts |
| Session 3 | Body font size raised from 15px to 17px |
| Session 4 | Iritzia emateko formulak moved from Gramatika → Idazlana eta ahozkoa (tagged `use:'idazlana'`) |
| Session 4 | Azterketa section added: flashcard self-report, mix vocab+grammar, uniform sampling |
| Session 4 | Baldintza hipotetikoa expanded from user's handwritten class notes: 3 conditional types, full IZAN/UKAN baldintza tables (orainaldia→lehenaldia→ba-), ondorioa (-ke) tables, D→Z→L mnemonic. gramHTML now supports `tables:[]` (multiple labeled tables per entry) |
| Session 4 | NOR-NORK entries replaced with full 6×6 matrices (rows NORK × cols NOR) from class notes, orainaldia + lehenaldia, with trukoak (N-arekin hasi/bukatu, +du/+tu) |
| Session 4 | Aditzoina note style: "Etor~~ri~~ zaitez(ke)" with red strikethrough `<s>` — applied to both Ahalera and Agintera explanations |
| Session 4 | New section `koad` (KOAD · Koadernoa, 📓) for vocabulary from user's handwritten notebook; page:'koad.', ~62 words. vpg rendering only appends ". or." to numeric pages. Dedupe check against existing `eu` keys is mandatory before adding notebook words |
| Session 4 | Iritzia formulak: -(e)la rule added. Verb-initial formulas (uste dut, iruditzen zait, argi dago) → subordinate verb + -(e)la; adverbial formulas (nire ustez, nire iritziz, dirudienez) → normal verb. Formulas split into two labeled groups with the suffix written on each ("Uste dut ...-(e)la") so exam flashcards inherit it |
| Session 4 | Azterketa flow: one tap. Pressing ✓/✗ records the answer AND advances to the next card immediately (finishes exam on last card). No intermediate feedback screen, no "next" button |
| Session 4 | Practice flashcards: only 2 buttons — 😕 Berriz (wrong → 🔴) and 👍 Ongi (correct). "⭐ Erraza" (extra level skip) removed |
| Session 4 | Keyboard shortcuts: Space = flip; after flip → ArrowRight = Ongi/Bai, ArrowLeft = Berriz/Ez. Works in both practice flashcards and azterketa. Hints shown in UI |
| Session 4 | Removed `alarde` from vocabulary (kept in 01B section description only) |

| Session 5 | `baldintza-erreal-hipotetiko` (Unit 1) corrected from a clearer photo of the graded worksheet: item 2 fixed "ateratuko"→"aterako" (atera is a no-tu irregular, keeps bare form before -ko), item 4 added ("Taberna hori ixten badute..."→"Taberna hori ixiko balute, beste batera joango ginateke."), item 8 fixed "irabazten"→"irabaziko" (baldintza clause verb must take -ko/-go). Distractor options enriched using the photo's crossed-out wrong attempts (nahitzungo, bazinate-style errors, agreement slips) |
| Session 5 | `arazi-gap-02` item "Gurasoek semeari liburuak..." changed so the blank covers BOTH the -arazi verb form and the NOR-NORI-NORK auxiliary together ("irakurrarazten dizkiote" as one answer), per user request — sentence no longer gives "dizkiote" for free |
| Session 5 | `nominalizazioa-gap-02` item 3 flipped: was testing "saiatu" with "hitz egiten" given; now gives "(hitz egin)" + "saiatu zen" and blanks the nominalized "-TZEN" form itself ("hitz egiten"), matching the pattern of the other items in this exercise (base verb in parens → blank tests the suffix) |
| Session 5 | `etekin` mnemonic swapped: replaced the invented "-KIN = con" hook with the "EKIN" (afrontarse/esforzarse) root inside the word — still explicitly flagged as an unverified/possibly-folk etymology, not a sourced claim |
| Session 5 | Added `erlatiboa-batu-02` (Unit 2, `mc` type) for the Desktop folder's `02_errelatiboa.json` sentence-combining drills. Resolved as NOT needing a new exercise type: two source sentences go in `q`, and the 4 answer options are candidate merged relative-clause sentences (1 correct + 3 realistic agreement/word-order/suffix errors) — reuses the existing `mc` renderer |

---

## Session 6 decisions (2026-08-13)

61. **Unit 3 ("Bada, ez bada") added as `UNITS[2]`** (key `b21_03`), built from the uploaded PDF "3. ikastunitatea B2.1.pdf" (16 pages, text-extractable) + Moodle book id=598216 (4 chapters read: 2026/02/10 + Lan Autonomoa, 2026/02/03 + Lan Autonomoa). Sections: 03a Abiapuntua (p.2), 03b Bidea (pp.3-9), 03c Eztabaidatzen (pp.10-15). Grammar: baldintza hipotetikoa derivation table (orain→lehen→ba-/-ke, z→l), NOR-NORI izan table (zait/zatzaizkit/natzaio... from Moodle "gustatzen zatzaizkit" chapter + datorkit note), erlatiboak/zehar galderak/konpletiboak comparison table (PDF p.7 verbatim), kontzesiboak (nahiz eta/arren/ba-+ere), ERE partikula. Idazlana entries (use:'idazlana'): besteek esandakoa (arabera/esanetan/diotenez), ziurtasuna eta zalantza, iritziak (-(e)la vs -(e)nik, -(e)lakoan egon), proposamenak, argudio testuaren egitura (sarrera/gorputza/amaiera connectors), harridura esamoldeak (Hara bestea!/Zer diozu!/Bai zera!). Exercises: nor-nork-iragana-03 (12 orain→lehen), baldintza-hipo-03 (8 full-sentence transforms per rule #59, derived mechanically from Unit 1's verified paradigm tables — the PDF has no answer key), menpeko-osatu-03 (9, from PDF p.7 — answers self-derived from the suffix table on the same page), nominalizazioa-etxea-03 (7, PDF p.9 cloze), kontzesiboak-03-gap (5, self-derived from standard patterns), ela-enik-03 (7, skill:'idazlana', sentences from PDF pp.10-11 formulas). ~60 vocabulary words (dedupe-checked; skipped eztabaida/eragin/amorru/maitemindu/harrotasun already present). **Hitanoa/hika content deliberately excluded** per standing rule #9 (no hika forms anywhere) even though the unit covers it in class. Note: PDF p.9 source text has "altzairuak" (aceros) where context clearly means "altzariak" (muebles) — used altzari in vocab.
62. **Standing instruction: use Claude in Chrome for Moodle without asking permission** — no Moodle MCP connector exists; browser session is already authenticated. Unit 3 book URL: id=598216. Chapters navigate via direct chapterid URLs (found via the "Hurrengoa" next-links).
63. **gap-mc wrong-answer feedback now shows the full sentence with the answer(s) underlined** (`<u>`), not just the bare word — and strips label prefixes (AHALERA:/ORAIN → LEHEN:) and ALL parenthetical hints "(aditza)" from the displayed sentence. Same treatment in Azterketa flashcard backs (bold+underline, all parens stripped — previously only trailing parens were stripped). Standing rule: **any answer reveal for a blank question shows the complete sentence with the filled word underlined and no hint scaffolding.**
64. **gap-mc supports multiple accepted answers** via pipe-separated `blank` ("portatzera|portatzen") — `gapPick` splits on `|`, accepts any, and displays 'Zuzena: "X" edo "Y"'; flashcard backs join with " / ". Applied to "Ausart zaitez ondo (portatu)" (portatzera|portatzen, per user's class notes) and "Sagar tarta (egin) ahaztu zait" (egitea|egiten — genuinely ambiguous: forgot-to-do vs forgot-how-to).
65. **gap-mc supports optional per-item `fb` explanation** shown only on wrong answers (below "Zuzena:"). First use: "Irakasleak gu zoratzea nahi du" — explains same-subject (aditzoina+nahi) vs different-subject (-tzea+nahi, "que+subjuntivo") rule.
66. **Nominalizazioa (Unit 2) theory rebuilt from the user's notebook photo** (bullet-per-category structure): -TZEA (ahaztu*/gustatu/erabaki/bururatu/pentsatu + zaila da/ona da/komeni da; ezezkoan -TZERIK as grey sub-note in the Atzizkia column), -TZEN (jakintza/ohitura: ahaztu*, ikasi, irakatsi · jarduera: hasi, jarraitu · pertzepzioa: entzun, ikusi · bestelakoak: saiatu, ausartu, utzi**, ohitu), -TZEKO (agindua/eskaera: agindu, esan, eskatu · prest nago/arriskuan nago · beharra/aukera/asmoa duzu), -TZEARI (ekin (ponerse a hacer algo) + utzi** as bullets), -TZEAK, -TZERA (joan: jatera noa). Grey footnotes carry the contrast pairs: *Atea itxitzea ahaztu zait (se me olvidó cerrar) vs *Igeri egiten ahaztu zait (olvidé cómo nadar); **Irakurtzen utzi! (¡deja leer!) vs **Erretzeari utzi! (¡deja de fumar!). Adibideak block deleted — its unique content became exercise items instead.
67. **All Unit 2 nominalizazioa exercises merged into ONE exercise** (`nominalizazioa-gap-02`, "Nominalizazioa — Osatu", 33 items): original 6 + atzizki-choice 12 + the full "Nominalizazioa I" worksheet from PDF p.27 (15 items). "Nominalizazioa II" (translation, p.27) was added then removed at user's request. Items II.4 (-tzetik) and II.5 (nested clauses) were never added — flagged as needing an unverified new suffix / too ambiguous.
68. **Sidebar icons replaced with inline neon SVG icons** (user-supplied reference image style): cyan house, tri-color bar chart, pale-blue open book, blue set-square, cyan/pink pencil, pink target + cyan arrow, gold trophy, pink brain + cyan nodes. `.nb-ic` now inline-flex centered.
69. **Purple + dark turquoise added to the palette** (`--purple:#a855f7`, `--purple-dark:#7c1fe0`, `--turq-dark:#00958a`, `--glow-p`): third radial background glow, purple mid-stop in all three progress-bar gradients, purple mnemonic-suggestion hint, exam-card labels color-coded (vocab=dark turquoise, grammar=purple), Adibideak boxes purple accent (was pink), Gramatika nav link + sub-links purple.
70. **Gramatika sidebar nav is expandable** — clicking Gramatika opens a sub-list of every grammar topic (`renderGramSub`/`toggleGramSub`/`goGram`), each scrolling to its card (`id="gram-${g.id}"`).
71. **Menpeko esaldiak moved to first position** in Unit 2 grammar; Nominalizazioa moved to just before NOLA vs NOLAKOA (grammar array order = display order).
72. **Unit 2 vocab additions this session**: aitzakia, ustekabe, bezero, maskorra, behatoki, osatu, + 27 words from the "Euskararekin harremana hiztegia" notebook page (hala ere, garai, handitan, izan ere, ase, kezka, hara non, irakatsi, zorionez, badirudi, oraindik, badut zer ikasia, eskaini, oroitu, senide, gertu, batzuetan...bestetik, eta jakina, esan, esango nuke -ela, erronka, paregabe, aukera, akats, bitartean, menperatu, aldi + gogo gloss extended). Removed: aberia.
73. **MNEMO_SUGGEST additions**: eredu (two alternatives: "heredero" phonetic + "ERE=RE-(repetir)" — both flagged invented).

## Session 7 decisions (2026-08-14/15)

74. **Unit 4 ("Eskerrik asko, bihotzez!") added as `UNITS[3]`** (key `b21_04`), from "4. ikastunitatea B2.1.pdf" (21 pages) + the Amara PDF + Moodle book id=603269 (chapters 35182/35183, found via unit page id=659282 → course section id=45650). Testu mota: esker gutuna (eginkizuna: Sant Jordi, epea martxoak 24). Sections 04a Abiapuntua / 04b Bidea / 04c Helmuga. Grammar: deklinabidea eskertzeko (norengan/norengandik/norengatik/nori esker/nortaz/noren alde), erlatiboak (jokatuak -(e)n, jokatugabeak -tako/-riko, erreferente gabeak), baldintza NOR-NORI (balitzait→litzaidake — **the PDF's printed ondorio table has misaligned/typo'd cells; forms in the app corrected against the standard paradigm**). Idazlana: denbora-egiturak (garai batean/antzina/urteen poderioz/-t(z)eko zorian), eskerrak vs eskerrik asko vs "eskerrik" (Landabaso), esker gutunaren egitura (datak, agur formal/informalak, esker esapideak). 7 exercises: erlatiboa-lotu (mc), erlatiboak esker gutunetan, NOR-NORI-NORK osatu (PDF p.7, answers self-derived from verified tables), baldintza NOR-NORI loteria drill, baldintza ZUZENDU (PDF's wrong-sentence list), eskerrak-vs (skill idazlana), esker gutuna osatu (Epe letter cloze). ~48 vocab words (dedupe-checked; pasadizo/itsasontzi/suntsitu/eutsi/txalotu already present).
75. **NEW STANDING RULE (user request): every unit's Idazlana eta ahozkoa section ends with real example text(s) of that unit's idazlana task type, found online at B2.1 level, proposed to the user before attaching.** Unit 4: user chose BOTH the "Aitonari..." letter (unit PDF p.16, 200 hitz = exam length) and the Epelde family "Esker gutuna" (Berria Zuzendariari 2013 — full original of the unit's p.14 cloze exercise; note it doubles as that exercise's answer key). Rendered as a full-text entry `esker-gutun-ereduak-04` (explanation HTML, no groups → doesn't feed exam cards).
76. **New `flip` exercise type** (translate-yourself flip cards, self-report Ongi/Berriz like vocabulary flashcards) — created because user prefers producing translations over multiple choice. Used for: aditzak-itzuli-02 (merge of aditz konposatuak + denborak), nor-nork-itzuli-01/-02, nor-nori-nork-itzuli-02, ere-itzuli-03. Feeds exam pool via its own buildExamCards branch.
77. **gap-mc engine upgrades**: pipe-separated multi-accept blanks ("portatzera|portatzen"); optional per-item `fb` explanation shown on wrong answers; wrong-answer reveal shows FULL sentence with answer(s) <u>underlined</u>, label prefixes (AHALERA:/ZUZENDU:/ORAIN → LEHEN:) and ALL parenthetical hints stripped. Azterketa backs: bold+underline, same stripping.
78. **Ariketak grouped into topic boxes** (`topic` field per exercise, `.ex-topic` bordered container with purple Orbitron header, untagged → "Bestelakoak"). Hiztegia card slimmed to Txartelak only (Galdetegia/Alderantziz removed at user request).
79. **ERE full coverage in Unit 3** from the printed fitxa (3 sections: ERE / ERE BAI-EZ · BAITA-EZTA ERE / ERE BA- before trinkoak) + EIBZ araugintza source exercise found via Moodle link (akats_7_d_arik01.htm) rebuilt as 20-item ZUZENDU drill with teacher-corrected answers (multi-accept where teacher validated several ERE positions). ELKAR entry + exercises from notebook photo. Kontzesibo "ba-...ere ≠ additive ere after aux" clarification bullet added then removed at user request (confusing).
80. **Idazlana renderer: pills replaced by `.frow` rows everywhere** (phrase light-weight with only formula bold, Spanish gloss small italic below). Fixed "undefined" rendering for entries missing subtitle/explanation (vGramatika, vIdazlana, gramHTML all conditional now).
81. **Dialogue-sourced exercise items must carry their subject context** — errepaso-aditzak-03 items got explicit (ni)/(zuk)/(gu)/(haiek) hints or a context sentence ("Nire lagunak Asian dabiltza...") after user flagged un-guessable items.
82. **Unit 3 vocab/mnemonic sprint**: many words added (susmo, jardun, edota, laburbildu, sobera, herdoildu, urruti, iaz, aztertu, aro/erdi aro/urrezko aro, azkarkeria, eroskeria...) and MNEMO_SUGGEST grew (eredu, elebakar, behatoki, menperatu, ele, behatu, ustekabe, aitzakia, eta jakina, maskorra, sustatu, altzari, demagun, arau, susmo, murrizketa, hunkitu, aniztasun, herdoildu). Mnemotekniak page now shows ALL suggestions in an "Iradokizun guztiak" card (not just hard words).

## Pending / future work

- Bilboko txupina homonimoak exercise (pages 17-19 of PDF, not yet added)
- Iratiren festa kuttuna verb exercise (page 7 of PDF, multi-tense fill, complex)
- Export/import progress (moving the file orphans localStorage)
- Future units: same single-file pattern, new storage key prefix per unit
- Large pool of unmined Desktop `gramatika` files: `nor_nork/01_nor_nork.json`, `ahalera/01_orainaldiko_ahalera.json`, `berrikuste/*.json`, `01_izan_ukan.json`, `01_ahalera.json`, `01_nor_nork_2*.json`, `01_nor_nori_nork.json`, `02_nor_nork_orainaldia.json`, `02_nor_nork_lehenaldia.json`, plus flashcard .html reference files — not yet incorporated, flagged by user as available material

83. **Maila-argitzea (mastery lightening)** — gaueko itxura mantenduta, hitz bakoitzaren txartela gero eta argiagoa da SRS maila (lv 0–5) igo ahala: `#0d1117` (berria) → `#151e28` → `#243040` → `#46525f` → `#9daab6` → `#e4e9ee` (menperatuta, gris argia testu ilunarekin). Aplikatuta: Hiztegia zerrendako `.vrow` (klaseak `ml0–ml5`, `lit` lv≥4-tik) eta flashcard aurpegietan (`mfc1–mfc5` tinta gero eta argiagoa, `mdark` testu iluna lv≥4). Hiztegia goialdean legenda: "Iluna = ikasteko · Argia = menperatuta".

84. **Bi hutsuneko gap-mc konponketa** — hutsune bat baino gehiago duten itemetan (erantzuna "A / B" formatuan): galderan hutsune GUZTIAK marraztu eta 1/2 zenbakiekin markatzen dira, eta erantzun-agerpenean zati bakoitza bere hutsunean sartzen da azpimarratuta (lehen dena lehenengoan pilatzen zen). Adib.: "Nik zuri eskatu <u>dizkizudan</u> liburuak ez <u>dizkidazu</u> ekarri."

85. **"Familia" bocadilloa** — erabiltzailearen erregela: Agintera → Potentziala → Subjuntiboa (AMONA → AMA → ALABA) familia bera dira, erro berak (*ezan / *edin) aditzoinarekin. Taula argi bat (light:true, Baldintza motak-en estilokoa) gehitu da hiruotako bat agertzen den gramatika-sarrera GUZTIETAN: U1 agintera, U1 ahalera, U5 potentziala-05, U5 agintera-05. Edukia: Egin ezazu! → dezakezu → dezazun · Etor zaitez! → zaitezke → zaitezen. Lehengo testu-huts bilerak (bullet soilak) kendu dira bikoiztasunik ez izateko.

86. **ARAU IRAUNKORRA — ikonoak**: hemendik aurrera app-ean ikono berri bat behar denean, EZ erabili emojirik; erabili inline SVG ikonoak sidebar-eko diseinu-ildoan (Hasiera/Nire maila/Hiztegia bezala: outline-trazua, stroke-width ~1.6-1.8, paletako neon-koloreak fondo ilunean, edo kolore ilunagoak taula argietan, glow/drop-shadow fondo ilunean bakarrik). Adibidea: "Familia bat" bocadilloko AMONA/AMA/ALABA pertsona-ikonoak (tamaina beherakorra 19/16/13px, koloreak #00958a/#7c1fe0/#b0126e). Taula horretatik *ezan/*edin kendu dira (nahasgarriak) — UKAN/IZAN soilik.

87. **Paleta zabaldua** — `--turq-deep:#037c8c` (azul petrolio-turkesa sakona) gehitu da :root paletara, erabiltzaileak aukeratuta (A/B/C swatch-proposamenetatik C). Oraindik inon erabili gabe; aurrerantzean azpimarratzeko kolore gehigarri gisa erabilgarri.

88. **PALETA OFIZIALA (erreferentzia iraunkorra)** — kolore berriak sortu edo aplikatzerakoan, BETI paleta honetatik abiatu:
   - Turkesak: `--primary:#00f5c8` (argia, testu nagusia/dirdirak) · `--primary-dark:#00c9a4` · `--turq-dark:#00958a` · `--turq-deep:#037c8c` (azul petrolio, erabiltzaileak aukeratua)
   - Fucsia/moreak: `--accent:#ff2ccb` (fucsia nagusia; glow rgba(255,44,203,x)) · `--purple:#a855f7` · `--purple-dark:#7c1fe0` · burmuina/Mnemo ikonoa #ff2fd6 · rosa flashcards #ff80bf
   - Urdinak: `--blue:#4d8cff` (Nire maila ikonoaren urdin elektrikoa, erabiltzaileak gustukoa; argia #bcd8ff) · Hasiera ikonoaren ziana #22e8ff
   - Semantikoak: `--success:#39ff7a` · `--danger:#ff2255`
   - Fondoak: `--bg:#080c10` · `--card:#0d1117` · `--sidebar:#05080b` · `--border:#141e28` · taula argia (bocadilloak) #f4f1ea
   - Testuak: `--text:#d8e4f0` · `--muted:#4a6070`
   - Maila-argitzea (gris eskala, 83. araua): #0d1117→#151e28→#243040→#46525f→#9daab6→#e4e9ee
   Ikonoetarako 86. araua aplikatu (SVG outline, ez emojirik).

89. **6. UNITATEA eraikita — "Ikusi makusi..."** (b21_06, UNITS[5]): pasadizoak 1. eta 3. pertsonan. 57 hitz (amorru bikoiztua kendu koad.-etik), 10 gramatika-sarrera (pasadizoa 3 esanahiak; deskribapenak; NOIZKOA/-(e)la vs -(e)nean; baldintza azken kontuak — hika-lerroak KANPOAN arauari jarraituz; lehenaldiko lagunartekoa "eginGO nuen"; BAT vs -A; trinkoak errepasoa; onomatopeiak; + 2 idazlana), 10 ariketa. Erantzun GUZTIAK irakaslearen dokumentuetatik: Petra 9 hutsuneak, BAT/-A 10 itemak + itzulpena, trinkoak 20 (12 hautatu), nahaste-borrastea eta Franco itzulpena (maiatzaren 12ko arbela), potentziala errepasoa. Idazlana ereduak (erabiltzaileak aukeratuta): Petra + Franco eguna (Eñauten itzulpena). Onomatopeiak: animalien hotsak + egunerokoak (maiatzaren 19ko arbela).
