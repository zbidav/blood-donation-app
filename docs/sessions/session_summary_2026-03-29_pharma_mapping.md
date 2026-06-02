# Pharmacology Drug Family Mapping — Session Summary
**Date:** 2026-03-29  
**Session type:** Strategy + POC (Deck 7 — Coagulation)

---

## Decisions Made

### Project Goal (refined)
Two new features planned for the blood donation app:
1. **Drug Guide** — browsable by drug family, with recruiter-level explanations
2. **Condition Guide** — browsable by disease/condition category, linked to relevant drug families
3. **"Similar mechanism drugs"** — added to existing MDA criteria cards, with disclaimer that it's not official MDA info (same pattern as popular destinations feature)

All three will have search capability.

### Reference Source
**WHO ATC Classification** (Anatomical Therapeutic Chemical) chosen as the authoritative reference for verifying drug families and checking for new members since the 2012 textbook (Lippincott's 5th ed.).

### Workbook Structure (4 sheets per deck)
| Sheet | Purpose | Key columns |
|---|---|---|
| **Families** | One row per sub-family (broad level) | Category, Family (EN/HE), ATC code, Mechanism (1 line EN/HE), Source deck |
| **Ingredients** | One row per active ingredient | Name, Family, ATC code, Source (Slides/ATC), Brand names, Notes |
| **Conditions** | One row per disease/condition | Category (EN/HE), Relevant families, Notes |
| **MDA_Links** | Mapping ingredient → MDA criterion | Ingredient, MDA criterion, Similar mechanism drugs, Disclaimer flag |

- Rows sourced from ATC (post-2012 drugs) highlighted in yellow
- Source column distinguishes "Slides" vs "ATC" origin

### Workflow — Per-Deck Then Merge
- **Each session:** Upload MD summary + pharmacology summary PDF + 2-3 presentation decks
- **Per deck:** Extract → ATC check → XLSX output → David approves
- **Output naming:** `pharma_deck_NN_topic.xlsx`
- **Final merge session:** Combine all deck files → `pharma_drug_families_master.xlsx` with deduplication, cross-family links, and consolidated ATC check

### Family Granularity
Broad level chosen (e.g., "Antiplatelets", "Anticoagulants", "Thrombolytics") with sub-families as rows within the Families sheet — not nested hierarchy.

---

## POC Completed: Deck 7 — Coagulation (קרישה)

### Output file
`pharma_deck_07_coagulation.xlsx`

### Statistics
| Sheet | Rows |
|---|---|
| Families | 14 |
| Ingredients | 37 |
| Conditions | 7 |
| MDA_Links | 7 |

### Families extracted (14)
**Reduce clotting:**
1. COX-1 Inhibitors (antiplatelet) — B01AC
2. ADP Receptor Antagonists — B01AC
3. GP IIb/IIIa Antagonists — B01AC
4. PDE-III Inhibitors (antiplatelet) — B01AC
5. Unfractionated Heparin (UFH) — B01AB01
6. Low Molecular Weight Heparins (LMWH) — B01AB
7. Direct Thrombin Inhibitors (parenteral) — B01AE
8. Factor Xa Inhibitors (parenteral) — B01AX05
9. Vitamin K Antagonists (oral) — B01AA
10. Direct Oral Anticoagulants (DOACs/NOACs) — B01AE/AF
11. Thrombolytics (fibrinolytics) — B01AD

**Increase clotting:**
12. Antifibrinolytics (plasminogen inhibitors) — B02AA
13. Antidotes for anticoagulants — V03AB
14. Coagulation Factors — B02BD

### New drugs added from ATC (not in 2012 slides, highlighted yellow)
- **Cangrelor** — ADP antagonist, IV, approved 2015
- **Edoxaban** — Factor Xa inhibitor (DOAC), approved 2015
- **Betrixaban** — Factor Xa inhibitor, approved 2017, withdrawn 2020
- **Idarucizumab** — Reversal agent for dabigatran, approved 2015
- **Andexanet alfa** — Reversal agent for Xa inhibitors, approved 2018

---

## Source Materials
- **Presentation:** 7_קרישה.pdf (35 slides)
- **David's summary:** מבוא לפרמקולוגיה (409-page PDF, pages ~113-126 for coagulation)
- **ATC reference:** WHO ATC code B01 (Antithrombotic agents), B02 (Antihemorrhagics)
- **Workflow doc:** pharma_mapping_workflow.md (in project files)

---

## Notes for Next Session
- David's pharmacology summary covers up to presentation 28; presentations 29-35 have no narrative summary — will lean more on ATC cross-reference for those
- MDA_Links sheet has several "לבדוק" entries that need David's professional review
- Aspirin will appear again in NSAID deck — deduplication handled at merge time
- Next decks to process: TBD by David (likely adjacent topics)

---

## Files Produced
| File | Location |
|---|---|
| `pharma_deck_07_coagulation.xlsx` | /mnt/user-data/outputs/ |
| `session_summary_2026-03-29_pharma_mapping.md` | /mnt/user-data/outputs/ |
