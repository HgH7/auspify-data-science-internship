# Auspify Data Science Internship - Final Submission

**Intern:** Hassan Elsayed
**Program:** Auspify Technologies Data Science Internship
**Dataset:** "Netflix Movies and TV Shows" by Shivam Bansal, Kaggle (https://www.kaggle.com/datasets/shivamb/netflix-shows), a snapshot of titles listed on Netflix as of September 2021.

This package contains the 4 completed tasks (of the 6 assigned), the cleaned dataset produced in Task 1 and reused by the other tasks, all charts, and written reports.

## Contents

| Path | What it is |
|---|---|
| `netflix_clean.csv` | Cleaned dataset produced in Task 1 (8,787 rows, 20 columns). Used by Tasks 2-4. |
| `Task1_Data_Cleaning/` | Data cleaning and preprocessing notebook, with saved outputs, plus a short report. |
| `Task2_EDA/` | Exploratory data analysis notebook, 7 charts in `charts/`, plus a short report. |
| `Task3_Recommendations/` | Content-based recommendation notebook, 4 charts in `charts/`, plus a short report. |
| `Task4_Forecasting/` | Release-year trend and forecasting notebook, 5 charts in `charts/`, plus a short report. |
| `Report/` | One written report covering all four tasks (Markdown source and PDF). |

Every notebook was run end to end with no errors, and the outputs and charts shown are the ones saved in the notebooks.

## How to run each notebook

Requirements: Python 3 with Jupyter, pandas, numpy, matplotlib and seaborn.

1. **Task 1** - place the original `Dataset.csv` (from the internship's shared dataset folder) beside `Task1_Data_Cleaning/Task1_Data_Cleaning.ipynb` and run all cells. It writes `netflix_clean.csv`.
2. **Task 2** - run `Task2_EDA/Task2_EDA.ipynb`. It reads `netflix_clean.csv` from its own folder or the parent folder (the top level of this package), and saves charts to `charts/`.
3. **Task 3** - run `Task3_Recommendations/Task3_Recommendations.ipynb` (also needs scikit-learn). Same data location rule as Task 2.
4. **Task 4** - run `Task4_Forecasting/Task4_Forecasting.ipynb`. Same data location rule as Task 2. Uses numpy/pandas/matplotlib only.

## Data notes

- The cleaned data covers titles added to Netflix up to 25 September 2021, so 2021 is a partial year.
- Each title keeps a single country label; co-productions are under-counted and 287 titles are "Unknown".
- 14 titles have a negative release-to-addition lag (flagged in Task 2, left unchanged).

Source code is also published at https://github.com/HgH7/auspify-data-science-internship

## Screenshots

Each task folder has a `screenshots/` folder with images of the executed notebook (code cells and their outputs, page by page). `charts/` holds the exported chart images.
