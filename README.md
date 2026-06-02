# 🩸 Blood Donation Eligibility App

**כלי עזר למתרימי דם ולתורמים — An eligibility guide for blood donation recruiters and donors**

A fully offline, single-file web app that helps [Magen David Adom (MDA)](https://www.mdais.org/) blood donation recruiters and donors navigate eligibility criteria, drug lookups, country-based deferral rules, and the donation process.

> **⚠️ Disclaimer:** This is NOT an official MDA tool. It is a volunteer-built resource. All eligibility decisions are made by on-site MDA medical staff.

## 🌐 Use It Now

**[Open the app →](https://zbidav.github.io/blood-donation-app/)**
_(activates after enabling GitHub Pages: Settings → Pages → Deploy from branch `main` / root)_

Or download `index.html` and open it directly in any browser — no internet required.

## Features

- **Medical criteria search** — Look up conditions, procedures, and medications against MDA blood donation guidelines
- **Drug lookup** — Search 4,936+ drugs from the Israeli Ministry of Health registry, with per-ingredient eligibility criteria and condition-dependent display
- **Country deferral guide** — Endemic country lookup with malaria/disease deferral periods, plus tourist destination risk mapping for 13 countries
- **Donor pre-screening wizard** — 12-screen advisory questionnaire that collects information without blocking; produces colored flags for recruiter review
- **4 languages** — Hebrew (עברית), English, Russian (Русский), Arabic (عربي)
- **Dark mode** — Toggle for comfortable use in any lighting
- **100% offline** — No server, no internet, no data transmitted. Works from `file://` or GitHub Pages. Privacy guaranteed.

## Why This Exists

MDA's publicly available eligibility information has gaps, and recruiters in the field often need quick answers. Non-Hebrew-speaking donors rely on Google Translate, which produces unreliable medical translations. This app fills those gaps with curated, multilingual content — built by a recruiter, for recruiters and donors.

## Technical Details

- Single HTML file (~2.1MB), all CSS/JS/data embedded inline
- Vanilla JavaScript — no frameworks, no build step, no dependencies
- RTL-first layout (Hebrew default)
- File-size is large because of embedded drug registry data (4,936 drugs) and multilingual content

## Data Sources

- MDA blood donation medical criteria
- Israeli Ministry of Health drug registry (scraped and curated)
- WHO endemic country data for malaria and tropical diseases
- MDA donor questionnaire

## Contributing

This is a personal volunteer project. If you're an MDA volunteer, medical professional, or translator and want to help, feel free to open an issue or reach out.

## License

This project is provided as-is for informational and volunteer use. Medical data is sourced from MDA and Israeli Ministry of Health public materials. The app makes no medical decisions and should not be used as a substitute for professional medical judgment.
