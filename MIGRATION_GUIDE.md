# Migration Guide: Moving to Claude Code + GitHub

## Overview

This guide explains how to set up the blood donation app project in a GitHub repo with Claude Code. After this, your workflow becomes: edit with Claude Code → commit → push → site updates automatically.

---

## Step 1: Create the GitHub Repo

1. Go to https://github.com/new
2. Repository name: `blood-donation-app` (or whatever you prefer)
3. **Public** (required for free GitHub Pages)
4. Do NOT initialize with README (we have our own)
5. Click "Create repository"

---

## Step 2: Set Up GitHub Pages

After the first push (Step 4):

1. Go to repo → Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: `main`, folder: `/ (root)`
4. Save
5. Your site will be at: `https://yourusername.github.io/blood-donation-app/`

---

## Step 3: Create Local Folder Structure

```bash
mkdir blood-donation-app
cd blood-donation-app
git init
```

### Copy these files into the folder:

#### Root (required)
| File | Source | Notes |
|------|--------|-------|
| `index.html` | Your latest `blood_donation_criteria_v0_4_3.html` | **Rename to index.html** — GitHub Pages serves this automatically |
| `CLAUDE.md` | From this migration package | Claude Code project memory |
| `README.md` | From this migration package | Edit the GitHub Pages URL after setup |
| `.gitignore` | From this migration package | |

#### `docs/` (project documentation)
| File | Source | Notes |
|------|--------|-------|
| `docs/app_summary.md` | `blood_donation_app_summary.md` | App architecture overview |
| `docs/endemic_destinations_summary.md` | `endemic_destinations_summary.md` | Tourist destination risk data |
| `docs/pharma_mapping_workflow.md` | `pharma_mapping_workflow.md` | Drug family mapping process |

#### `docs/sessions/` (session history)
| File | Notes |
|------|-------|
| `session_summary_2026-03-28.md` | Translation session |
| `session_summary_2026-03-28_b.md` | Continuation |
| `session_summary_2026-03-28_russian_t_content.md` | Russian translation content |
| `session_summary_2026-03-28_translation.md` | Translation infrastructure |
| `session_summary_2026-03-29_full.md` | Arabic + dark mode |
| `session_summary_2026-03-29_pharma_mapping.md` | Pharma mapping start |
| `session_summary_2026-03-30_pharma_mapping.md` | Pharma decks 14-18 |
| `session_summary_2026-03-30_pharma_decks_19_20.md` | HTN + diuretics |
| `session_summary_2026-03-30_pharma_decks_21_23.md` | Cardiac block |

#### `data/` (reference data — not used at runtime)
| File | Notes |
|------|-------|
| `pharma_master_Ingredients.csv` | 1,040 ingredients |
| `pharma_master_Conditions.csv` | 349 conditions |
| `pharma_master_MDA_Links.csv` | 249 MDA links |
| `pharma_master_Cross_References.csv` | Cross-deck references |
| `pharma_master_Statistics.csv` | Mapping statistics |
| `Blood_donation_medical_Criteria.xlsx` | MDA medical criteria source |
| `Blood_Donation_endemic_Counteries.xlsx` | Endemic country data source |
| `Criteria_blood_donation_2023.xlsx` | 2023 criteria update |
| `שאלון_תורם_דם_טבלה.xlsx` | Donor questionnaire structure |

#### `reference/` (large files — .gitignored by default)
| File | Size | Notes |
|------|------|-------|
| `drug_registry_data.txt` | 800KB | Raw registry data (already embedded in app) |
| `contentsVer1_js.txt` | 28KB | Historical JS content versions |
| `contentsVer3_js.txt` | 36KB | |
| `contentsVer4_js.txt` | 64KB | |
| `contentsVer5_js.txt` | 112KB | |

#### Files to keep locally but NOT in the repo
| File | Reason |
|------|--------|
| `david_blood_donation_context.md` | Personal info — now covered by CLAUDE.md |
| `קורס_מתרימי_דם_מקוצר.docx` | MDA course materials — possibly proprietary |
| `כמה_טבלאות.docx` | MDA internal tables |
| `סיכום_למבחן_נהלים.docx` | MDA exam summary |
| `קורס_שאיבת_דם_ורידי.docx` | MDA phlebotomy course |
| `השתלמות_בנק_הדם_יולי_25.docx` | Blood bank training |
| `רשימת_מיקוד_פרמקולוגיה_תשעז_אריאל.pdf` | University course materials |

---

## Step 4: First Push

```bash
cd blood-donation-app
git add .
git commit -m "Initial commit: blood donation eligibility app v0.4.3"
git branch -M main
git remote add origin https://github.com/yourusername/blood-donation-app.git
git push -u origin main
```

---

## Step 5: Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Requires Node.js 18+. Then:

```bash
cd blood-donation-app
claude
```

Claude Code will automatically read `CLAUDE.md` on startup and know how to work with the project.

---

## Typical Workflow After Setup

```
you:    claude "add Montenegro to the Europe region in the country guide"
claude: [reads CLAUDE.md, writes Python script, edits index.html, validates]
you:    [test in browser]
you:    git add -A && git commit -m "add Montenegro to Europe region" && git push
        → site updates in ~60 seconds
```

Or let Claude Code handle the git part too:

```
you:    claude "commit and push the Montenegro change"
claude: git add -A && git commit -m "add Montenegro to Europe region" && git push
```

---

## Notes

- **The `reference/` folder is .gitignored** — if you want those files in the repo too, remove the `reference/` line from `.gitignore`
- **GitHub Pages free tier** works for public repos. If you need private, you'd need GitHub Pro ($4/mo) or use a different host
- **The app filename must be `index.html`** for GitHub Pages to serve it at the root URL. If you keep the versioned name, you'd need to link to `/blood-donation-app/blood_donation_criteria_v0_4_3.html` which is clunky
- **Session summaries in git** means you have version history for project decisions, which is nice for continuity
