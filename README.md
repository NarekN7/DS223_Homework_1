# Homework on Bass Model — Dreame Pocket High‑Speed Hair Dryer (U.S. Scope)

This repository contains a complete Bass diffusion analysis for the **Dreame Pocket High‑Speed Hair Dryer** (selected from TIME’s Best Inventions 2024). The project answers all seven required questions (innovation choice, analogue, historical data, parameter estimation, forecast, scope, adopters by period with Fermi logic) and includes the R Markdown source, compiled outputs, data, and references.

> **Note about outputs:** Some figures were reported as **not rendering correctly** in certain PDF viewers (image corruption). To ensure reviewers can see every plot, I included **both** the PDF and an **HTML** export of the report. If a chart is missing or blank in the PDF, please open the HTML version.

---

## Repository Structure

```
.
├─ data/
│  ├─ Hair-Dryer.xlsx         # U.S. retail unit sales of hair dryers (2010–2018), in millions
│  └─ dataset1.csv            # Generated forecast table (Year, New Adopters, Cumulative Adopters)
├─ report/
│  ├─ report_source.Rmd       # Main R Markdown analysis
│  ├─ report.pdf              # Compiled PDF (some viewers show corrupted images; see HTML below)
│  └─ report_source.html      # Compiled HTML (fallback if PDF images are not visible)
├─ sources/
│  └─ Sources.pdf             # APA-style reference list supporting the analysis
├─ script1.R                  # (optional) Estimation helpers
├─ script2.R                  # (optional) Forecasting & plotting helpers
├─ helper_functions.R         # (optional) Shared utilities
└─ README.md
```

> The entire analysis can be reproduced by knitting `report/report_source.Rmd`.

---