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

## Getting Started

### Prerequisites
- **R (≥ 4.1)**
- Suggested packages:
  ```r
  install.packages(c("tidyverse", "readxl", "ggplot2", "broom"))
  # Optional (for alternative flows / plot arrangements):
  # install.packages(c("diffusion", "ggpubr"))
  ```

### Reproducing the Report
From the repository root in RStudio (or R console):
```r
# Ensure working directory is the repo root
rmarkdown::render("report/report_source.Rmd", output_format = "pdf_document")
# If your PDF viewer shows missing/blank images, also render HTML:
rmarkdown::render("report/report_source.Rmd", output_format = "html_document")
```

Outputs will appear in `report/` as `report.pdf` and `report_source.html`.

---

## What the Code Does (High Level)

1. **Historical Data (Q3):** Loads `data/Hair-Dryer.xlsx` (U.S. retail unit sales, 2010–2018) and visualizes the series (in **millions** of units).  
2. **Bass Model (Q4):** Defines the closed‑form Bass functions and fits two specifications to handle the **saturated category**:
   - **Free‑M fit** (diagnostic): often yields very large \( M \) and \( q \to 0 \) on tail data.
   - **Fixed‑M fit** (primary): sets \( M \approx 130 \) (≈ U.S. households in **millions**) to obtain interpretable \( p, q \) from the late diffusion tail.
3. **Forecast (Q5):** Projects adoption for the **Dreame Pocket** as a premium **sub‑segment** using the tail \( p, q \) and a **base market potential \( M = 6{,}000{,}000 \)** U.S. households; horizon is **20 years**.
4. **Scope (Q6):** **United States** — data series, household counts, and launch/pricing context are U.S.-based.
5. **Adopters by Period (Q7):** Produces **year‑by‑year** new and cumulative adopters and **exports** the table to `data/dataset1.csv`. Includes a **Fermi** sizing with sensitivity (\( M \in \{4,6,8\}\) million).

---

## Key Modeling Choices

- **Why fixed \( M \) for the tail fit?** In saturated markets, free‑M Bass fits tend to inflate \( M \) and send \( q \to 0 \), matching shape but losing interpretability. Fixing \( M \approx \) U.S. households (in millions) yields **stable, interpretable** \( p, q \) that we carry to the sub‑segment forecast.
- **Why \( M = 6 \) million for Dreame?** Using U.S. household counts and premium willingness‑to‑pay benchmarks, the **addressable, compact/travel premium** sub‑segment is conservatively sized around **5–8 million** households. We set **\( M = 6 \) million** as the base case and run sensitivity.

---

## Data & References

- `data/Hair-Dryer.xlsx`: U.S. retail unit sales of hair dryers (2010–2018), in millions.  
- All citations and supporting sources are compiled in **`sources/Sources.pdf`** (APA style).  
- The report body avoids hyperlinks, per assignment rules; see **Sources.pdf** for full references.

> If you need to update data or rerun the analysis with a different time span, replace `data/Hair-Dryer.xlsx` and knit again.
