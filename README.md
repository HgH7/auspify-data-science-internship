# Netflix Catalog Analysis

A four-part data project on Netflix's catalog: clean the raw data, explore it, build a content-based recommender, and forecast titles per release year.

**Author:** Hassan Elsayed
**Dataset:** "Netflix Movies and TV Shows" by Shivam Bansal, Kaggle (https://www.kaggle.com/datasets/shivamb/netflix-shows), a snapshot of titles listed on Netflix as of September 2021. The copy used here has 8,790 rows and 10 columns and is expected to be saved as `Dataset.csv`.

## What it does

1. **Data cleaning**: removes duplicates, converts placeholder missing values, fixes date, duration, genre and rating columns. Output: `netflix_clean.csv` (8,787 rows, 20 columns).
2. **Exploratory analysis**: content mix, countries, ratings, growth over time, durations, with 7 charts.
3. **Recommendations**: TF-IDF and cosine similarity over genres, director, country, rating and year. Returns the 10 most similar titles for any title; 84.3% of top-10 results share the query title's primary genre, against 9.3% for random picks.
4. **Forecasting**: compares five simple models on a 2017-2020 holdout and forecasts 2021-2025 titles per release year.

## Contents

| Path | What it is |
|---|---|
| `netflix_clean.csv` | Cleaned dataset produced in part 1, used by parts 2-4. |
| `01_Data_Cleaning/` | Cleaning notebook with saved outputs, short report, screenshots. |
| `02_EDA/` | EDA notebook, 7 charts in `charts/`, short report, screenshots. |
| `03_Recommendations/` | Recommender notebook, 4 charts in `charts/`, short report, screenshots. |
| `04_Forecasting/` | Forecasting notebook, 5 charts in `charts/`, short report, screenshots. |
| `Report/` | Full written report (Markdown and PDF). |

## How to run

Requirements: Python 3 with Jupyter, pandas, numpy, matplotlib and seaborn (part 3 also needs scikit-learn).

1. Part 1: put `Dataset.csv` beside `01_Data_Cleaning/01_Data_Cleaning.ipynb` and run all cells. It writes `netflix_clean.csv`.
2. Part 2: run `02_EDA/02_EDA.ipynb`. It reads `netflix_clean.csv` from its own folder or the repo root and saves charts to `charts/`.
3. Part 3: run `03_Recommendations/03_Recommendations.ipynb`. Same data location rule.
4. Part 4: run `04_Forecasting/04_Forecasting.ipynb`. Same data location rule. Uses numpy, pandas and matplotlib only.

## Data notes

- The data covers titles added to Netflix up to 25 September 2021, so 2021 is a partial year.
- Each title keeps a single country label; co-productions are under-counted and 287 titles are "Unknown".
- 14 titles have a negative release-to-addition lag (flagged in part 2, left unchanged).
