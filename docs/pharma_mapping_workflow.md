# Drug Family Mapping — Workflow Guide

## Goal

Expand drug search coverage in the blood donation criteria app.
Systematic mapping: drug families → active ingredients → brand names → MDA criteria.
Hebrew and English only at this stage.

---

## Phases

### Phase 1 — Extract from Course Presentations (Baseline)

**Input:** David's pharmacology course slides (based on Lippincott's Illustrated Reviews: Pharmacology, 5th ed.)

**Process:**
- Extract every drug family mentioned in the slides
- For each family: name (HE/EN), mechanism of action (one line), active ingredients listed in slides

**Output:** Baseline table — family × active ingredients from course

**Note:** The slides are the starting point only; not everything is relevant to blood donation and not everything is current.

---

### Phase 2 — Supplement with Newer Drugs (Expansion)

**Input:** Baseline table from Phase 1

**Process:**
- For each family: check whether new active ingredients have been approved since the textbook (2012)
- Sources: web search (FDA approvals, WHO Essential Medicines, DrugBank, etc.)
- Add new generic names to the table
- Flag "new — not in slides" to distinguish from baseline

**Output:** Expanded table — family × all known active ingredients (including new ones)

---

### Phase 3 — Working List in Memory (Accumulation)

**What this is:** A running list maintained in Claude's memory between sessions — NOT in the app.

**Record structure per family:**

| Field | Example |
|---|---|
| Family (EN) | GLP-1 Receptor Agonists |
| Family (HE) | אגוניסטים לקולטן GLP-1 |
| Mechanism — one line | Mimics GLP-1 hormone; inhibits glucagon secretion, slows gastric emptying |
| Active ingredients | semaglutide, liraglutide, tirzepatide, dulaglutide, exenatide |
| Brand names in Israel | Ozempic, Wegovy, Saxenda, Mounjaro, Trulicity, Byetta |
| MDA criterion | [number/description if exists, or "no direct criterion"] |
| Mapping note | "Diabetes — deferral by condition, not by drug" |

**Rule:** We are NOT building anything into the app at this stage. Collect, verify, organize only.

---

### Phase 4 — Ministry of Health Database Scan (Later)

**Input:** Accumulated list from Phase 3

**Process:**
- Use Claude Desktop Agent for manual browsing of the Israeli Ministry of Health drug database
- For each active ingredient: locate the drug page, extract relevant info, save link
- Manual scraping — not automated, due to site structure

**Output:** Enriched list with official Ministry of Health links

---

### Phase 5 — Integration into App (Final)

**Input:** Verified list from Phase 4

**Process:**
- Final mapping of ingredients → existing criteria in DATA_GUIDE
- Add search terms (generic + brand) to the search engine
- Add mechanism explanation lines where relevant
- Content in Hebrew and English

**Output:** App update

---

## Working Rules

1. **Don't build before we finish collecting.** Phases 1–3 are research only.
2. **Hebrew and English only** — translation to other languages only at integration phase.
3. **Memory is the source of truth** until Phase 4 — the list updates between sessions.
4. **Each family is reviewed separately** — David approves before moving to the next one.
5. **New active ingredient = needs verification** that it's actually marketed/relevant, not just approved.
6. **Mapping to MDA criterion = source:** existing criteria in the app + David's professional judgment.

---

## Status Tracker

| Family | Ph.1 | Ph.2 | Ph.3 | Notes |
|---|---|---|---|---|
| _(not started)_ | | | | |
