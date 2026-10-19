# Pandemic Waves and State-Level Outcomes: COVID-19 in the U.S. (2020–2023)

Individual final project for BST 260 (Introduction to Data Science), Harvard T.H. Chan School of Public Health, Fall 2024. All analysis is in R and Quarto.

**Read the report:** [docs/BST260_final_report.pdf](docs/BST260_final_report.pdf) · [Supplementary figures](docs/Supplementary.pdf)

## Questions

1. What were the main waves of the pandemic, and how did cases, hospitalisations and deaths differ between them?
2. How did COVID-19 death rates vary across states within each wave?
3. How did severity (case-fatality and hospitalisation-to-death ratios) change over time, and how does it relate to vaccination coverage?

## Data

All data are public. CDC data are pulled from the Socrata APIs at run time; the Census 2023 vintage file is included in `data/raw/`.

| Source | Content | Access |
|---|---|---|
| CDC | Weekly new cases by state | [`pwn4-m3yp`](https://data.cdc.gov/resource/pwn4-m3yp.json) |
| CDC | Weekly COVID-19 hospitalisations by state | [`39z2-9zu6`](https://data.cdc.gov/resource/39z2-9zu6.json) |
| CDC | Weekly provisional COVID-19 deaths by state | [`r8kw-7aab`](https://data.cdc.gov/resource/r8kw-7aab.json) |
| CDC | Vaccination coverage (primary series, boosters) | [`rh2h-3yt2`](https://data.cdc.gov/resource/rh2h-3yt2.json) |
| U.S. Census Bureau | State population 2020–2021 | Census Population Estimates API (key required) |
| U.S. Census Bureau | State population 2020–2023 | `data/raw/NST-EST2023-ALLDATA.csv` |

Sources were merged by state and MMWR week/year, and counts were converted to rates per 100,000 population.

## Methods

- Segmented the pandemic into five waves from national weekly case, hospitalisation and death rates.
- Compared state death rates within each wave (heatmap).
- Tracked the case-fatality ratio (CFR) and hospitalisation-to-death ratio (HDR) by wave, with 7-week rolling averages to smooth week-to-week noise.
- Plotted state vaccination coverage against death rates for each wave.

## Key findings

| Wave | Period | Pattern |
|---|---|---|
| 1 | Jan–Sep 2020 | Initial outbreak; highest case-fatality ratio |
| 2 | Oct 2020–Jun 2021 | Fall/winter surge and Alpha; high hospitalisation |
| 3 | Jul–Nov 2021 | Delta resurgence; highest hospitalisation rates |
| 4 | Dec 2021–Apr 2022 | Omicron BA.1; largest case spike, lower severity |
| 5 | May 2022–May 2023 | Omicron subvariants; smaller peaks, lowest severity |

- Death rates varied widely by state and wave: the Northeast (e.g., New Jersey, Connecticut) was hit hardest in Wave 1, while Southern and Midwestern states had higher death rates in Waves 2–4.
- CFR declined across waves, from its peak in Wave 1 to its lowest in Wave 5.
- States with higher vaccination coverage had lower death rates in every wave.

**Limitations.** These are state-level (ecological) associations without adjustment for age structure, testing intensity, or healthcare capacity, so they describe patterns rather than causal effects of vaccination. Case counts depend on testing, which changed substantially over the study period.

## Repository structure

```
├── code/
│   ├── final-project.qmd       # data download, wrangling, and figures
│   ├── covid-19-analysis.qmd   # written report (renders to PDF)
│   ├── BST260-ref.bib          # references
│   └── images/                 # figures used in the report
├── data/raw/
│   └── NST-EST2023-ALLDATA.csv # Census state population estimates, 2020–2023
└── docs/                       # rendered report, supplementary figures, analysis PDF
```

## Reproducing the analysis

1. Install R (≥ 4.0) and [Quarto](https://quarto.org/).
2. Install the packages:
   ```r
   install.packages(c("tidyverse", "janitor", "httr2", "zoo", "RColorBrewer"))
   ```
3. Get a free Census API key at <https://api.census.gov/data/key_signup.html> and add it to `~/.Renviron`:
   ```
   CENSUS_API_KEY=your_key_here
   ```
4. From the repository root, render the analysis and then the report:
   ```bash
   quarto render code/final-project.qmd
   quarto render code/covid-19-analysis.qmd
   ```

The CDC endpoints return the latest published data, so re-running may give slightly different counts if the CDC has revised its archives.
