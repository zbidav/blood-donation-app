# Blood Donation Eligibility App — CLAUDE.md

## What This Is

A single-file, fully offline HTML/CSS/JS blood donation eligibility app for Magen David Adom (MDA) volunteers and donors in Israel. The app helps recruiters (מתרימים) and donors navigate eligibility criteria, drug lookups, country-based deferral rules, and the full donation process.

The main file is `index.html` (~2.1MB, ~14,000+ lines). All data, styling, and logic are embedded inline — no CDN, no external calls, no server, no build step. It runs on `file://` and GitHub Pages alike.

## Core Principles

- **"אוסף, לא שופט"** — The app collects and presents information. It NEVER makes eligibility decisions. All final decisions rest with on-site MDA staff.
- **Reason over drug** — The reason a donor takes a drug matters more than the drug itself. Always assume a motivated donor will show up regardless of treatment severity.
- **All info visible** — Condition-dependent drug entries show ALL branching information at once, never hidden behind prompts. ("מעדיף שתמיד כל המידע יהיה מול העיניים")
- **Offline-first, single-file** — Vanilla JS/CSS only. No frameworks, no CDN, no npm. `file://` compatible. Data files must declare global JS variables (not JSON) for `file://` compatibility.
- **Privacy** — Data is never saved or transmitted. This is critical for encouraging honest donor answers on sensitive topics (HIV risk, drug use, etc.).
- **Global disclaimer** — Appears on all drug search results. The app is not a substitute for medical consultation.

## Architecture

### Languages
4 languages: Hebrew (`he`), English (`en`), Russian (`ru`), Arabic spoken (`ar_spoken`).
Hebrew is the default. RTL layout.

### Translation System
- `T` object: 265 content keys × 4 languages
- `T3_AR` lookup table: ~814 entries for Arabic
- `_gT()` helper function for multi-language string resolution
- `t(key)` function for T-object lookups
- UI strings, QUESTIONNAIRE (62 items), Part D (21 items), General Info sub-tabs (~254 strings) — all translated to 4 languages
- `DATA_GUIDE` (~600 medical strings): Hebrew + English only; Russian/Arabic fall back to English
- `DATA_DESTINATIONS`: Hebrew + English only

### Drug Registry
- 4,936 drugs embedded inline as JS objects
- Global variables: `DRUG_REGISTRY`, `DRUG_NAMES_EN`, `DRUG_ROUTES`, `INGREDIENTS`, `ATC4_GROUPS`, `ATC4_CRITERIA`
- Unified search: MDA results first, then registry results with toggle + disclaimer
- Search covers: name, ingredient, ATC group, indication, note, fuzzy matching
- ~103 condition-dependent entries use `conds` arrays; ~50 fully implemented via `getCondsForGeneric()`
- Per-ingredient criteria display (not worst-only)
- Injection route → "not on injection day" warning (suppressed for `defer_perm`)
- 24-hour pre-donation deferral note for SC/IM self-administered injectables (~603 drugs)

### 12-Screen Donor Wizard ("שאלון מהיר לתרומה")
- Advisory flags only — nothing blocks progression
- Every question produces colored flags; eligibility decisions remain with staff
- Screen 1 translation complete (44 keys, `QZ_SCREENS` uses `tKey` references)
- Screens 2–12: inline Hebrew, awaiting translation to `t()` calls

## CRITICAL: How to Edit the Main File

**NEVER read the full HTML file into context.** It is 2.1MB / 14,000+ lines. Loading it will blow the context window.

### Edit Pattern — Python `content.replace()`

All edits use Python scripts with exact string replacement:

```python
# Read
with open('index.html', 'r', encoding='utf-8') as f:
    content = f.read()

# Replace — ALWAYS use count=1
content = content.replace(old_string, new_string, 1)

# Validate the replacement worked
print("OK" if new_string in content else "FAILED")

# Write
with open('index.html', 'w', encoding='utf-8') as f:
    f.write(content)
```

### Rules for File Edits

1. **Use exact multi-line anchor strings** — copy enough surrounding context to be unique
2. **Always `count=1`** — ensures exactly one replacement
3. **Validate after every edit** — `print("OK" if new_string in content else "FAILED")`
4. **Run `node --check index.html`** after JS changes (will fail on HTML but catches syntax errors in `<script>` blocks — use a temp `.js` extraction if needed)
5. **For large data replacements** — use `content.find()` and `content.rfind()` for start/end markers rather than matching full old strings
6. **Hebrew strings in Python** — write scripts to a file first using `cat > file.py << 'ENDSCRIPT'`, then run separately. This avoids encoding issues.
7. **Never use grep, echo, or sed** for edits on this file — Python only

### Querying Embedded JS Data

Write temporary Node.js scripts:

```javascript
// Promote `const` to `var` for global scope access
const code = fs.readFileSync('index.html', 'utf8');
const jsMatch = code.match(/<script[^>]*>([\s\S]*?)<\/script>/);
const jsCode = jsMatch[1].replace(/^const /gm, 'var ');
eval(jsCode);
// Now query DRUG_REGISTRY, ATC4_CRITERIA, etc.
```

## File Structure

```
/
├── index.html              # THE APP — single-file, all data embedded
├── CLAUDE.md               # This file — Claude Code project memory
├── README.md               # GitHub readme
├── .gitignore              # Temp files, editor artifacts
├── docs/                   # Project documentation
│   ├── app_summary.md
│   ├── endemic_destinations_summary.md
│   ├── pharma_mapping_workflow.md
│   └── sessions/           # Session summaries (chronological)
│       └── *.md
├── data/                   # Source data (reference, not used at runtime)
│   ├── pharma_master_*.csv
│   ├── Blood_donation_medical_Criteria.xlsx
│   ├── Blood_Donation_endemic_Counteries.xlsx
│   ├── Criteria_blood_donation_2023.xlsx
│   └── שאלון_תורם_דם_טבלה.xlsx
└── reference/              # Raw data files (large, .gitignored by default)
    ├── drug_registry_data.txt
    └── contentsVer*.txt
```

## Session Workflow

1. David may upload a prior session summary `.md` — read it first to restore context
2. **Planning sessions** are separate from **implementation sessions** — respect which mode we're in
3. **Content before code** — David reviews drafted content (translations, guide text) before implementation
4. David tests each change in the browser and reports specific symptoms; diagnose and fix incrementally
5. End each session with a markdown summary + any output files

## Key People

- **David Gorelik** — project owner, MDA blood donation recruiter (volunteer), PhD student in Computational Biology. Has pharmacology training. Codes in R, shell, some Python. Reviews all content decisions.
- **Yishai Schneider** — pharmacist who built the Israeli drug registry JS file and drug name mapping

## What's In Progress

- Wizard translation: Screens 2–12 (inline Hebrew → `t()` calls + all 4 language blocks)
- ~53 remaining condition-dependent drug entries
- Arabic translation: `DATA_DESTINATIONS`, HELP tooltips, ~600 `DATA_GUIDE` medical strings
- Montenegro addition to Europe region in country guide
- Hemoglobin deferral logic: graduated periods (3/6/12 months) — needs medical authority consultation
- Japanese translation (planned as appreciation gesture)

## What NOT to Do

- Do NOT add frameworks, bundlers, or package managers
- Do NOT split into multiple files (the single-file design is intentional)
- Do NOT make external network calls from the app
- Do NOT store or transmit user data
- Do NOT make eligibility decisions — only present information
- Do NOT load the full HTML into context — use Python replacement scripts
- Do NOT use `grep`, `sed`, `awk`, or `echo` for file editing — Python only
