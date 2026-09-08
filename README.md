# Netflix Content Strategy & Growth: A Data-Driven Analysis

CDAV Capstone Project — Michael Ngugi (Admission No. 222579), July 2026 Cohort

## Problem Statement

How has Netflix's content genre mix evolved over time, and which genres represent Netflix's
most active growth areas — and how reliable are these conclusions given gaps in the
underlying content metadata?

## Dataset

- **Source:** [Netflix Movies and TV Shows Dataset](https://github.com/rfordatascience/tidytuesday/tree/main/data/2021/2021-04-20), originally compiled by Shivam Bansal, distributed via the TidyTuesday project
- **Size:** 7,787 titles × 12 columns
- **Coverage:** Titles added to Netflix between 2008 and 2021

## Methodology

1. **Data Cleaning** — dropped rows missing `date_added`/`rating` (~0.1% loss); filled missing `director`, `cast`, and `country` with `"Unknown"` to preserve genre/release data
2. **Data Preparation** — exploded multi-value `listed_in` (genre) and `country` columns; split `duration` into `duration_minutes` (Movies) and `duration_seasons` (TV Shows); derived `year_added` from `date_added` as the time dimension for growth analysis
3. **Exploratory Data Analysis** — genre frequency, yearly title additions, content type split, top content-producing countries, movie duration trends
4. **Growth Analysis** — compared genre-level title counts between an early period (2016–17) and a recent period (2019–20) to identify fastest-growing genres
5. **Hypothesis Testing** — two chi-square tests of independence:
   - Genre distribution × time period (significant, χ²(9, N=7,627) = 178.05, p < .001, Cramér's V = .146)
   - Content type (Movie/TV Show) × time period (not significant, χ²(1, N=5,824) = 0.03, p = .859)
6. **Data Quality Assessment** — checked whether missing `country` data is randomly distributed across time periods and genres, to evaluate the reliability of the growth conclusions

## Key Findings

- Netflix's genre mix has shifted significantly but modestly over time
- **Romantic Movies (+348%)**, **Comedies (+265%)**, and **Children & Family Movies (+229%)** are the fastest-growing genres; **Documentaries (+12%)** lag well behind
- This growth is **not** driven by a shift in content format — the Movie/TV Show split remained stable (~33% TV Shows) across both periods
- Missing `country` metadata is stable across time periods (not biasing the core finding) but concentrated in specific genres (International TV Shows, TV Dramas, Children & Family Movies), warranting caution on any country-specific claims for those genres

## Repository Contents

| File | Description |
|---|---|
| `Netflix_nb.ipynb` | Full analysis notebook — cleaning, EDA, hypothesis testing, findings |
| `Netflix_Capstone.pptx` | Presentation slide deck |
| `netflix_titles.csv` | Source dataset |
| `README.md` | This file |

## Tools Used

Python, Pandas, NumPy, Matplotlib, SciPy (`scipy.stats`) — Jupyter Notebook (Python 3.13.7)

## References

- Netflix Movies and TV Shows Dataset — Bansal / TidyTuesday (2021)
- McHugh, M. L. (2013). The Chi-square test of independence. *Biochemia Medica*, 23(2), 143–149.
- Netflix, Inc. (2020). *Notice of 2020 Annual Meeting of Stockholders and Proxy Statement* (Form DEF 14A). U.S. Securities and Exchange Commission.
- Cosmas Gitonga, Statistics I coursework — hypothesis testing and APA reporting conventions

## Author

Michael Ngugi — CDAV (Certificate in Data Analytics and Visualization), July 2026 Cohort
