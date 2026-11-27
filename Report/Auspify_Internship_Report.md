# Netflix Catalog Analysis - Final Internship Report

**Intern:** Hassan Elsayed
**Program:** Auspify Technologies Data Science Internship
**Dataset:** "Netflix Movies and TV Shows" by Shivam Bansal, Kaggle (https://www.kaggle.com/datasets/shivamb/netflix-shows), a snapshot of titles listed on Netflix as of September 2021.

This report covers the four completed tasks: data cleaning, exploratory data analysis, a content-based recommendation system, and release-year trend forecasting. All analysis uses the cleaned dataset produced in Task 1 (8,787 titles, 20 columns, one row per title).

## Task 1: Data Cleaning and Preprocessing

**Objective.** Turn the raw Netflix titles file into a clean, analysis-ready dataset.

**Method.** Loaded the raw data (8,807 rows), checked for duplicates and for missing values hidden as placeholder text, fixed inconsistent formats, and transformed date, duration, genre and rating columns into usable types.

**Key findings.**

- 3 records were exact duplicates under a different `show_id`; removed.
- `director` and `country` hid missing values as the text `'Not Given'`; converted to proper missing values and filled with `'Unknown'` so no rows were lost.
- `date_added` was text in mixed formats; converted to datetime, with year, month, month name and weekday derived.
- `duration` mixed minutes and seasons in one column; split into numeric minutes (movies) and numeric seasons (TV shows).
- A few titles had been date-mangled by Excel before the file was received; flagged and left unchanged rather than guessed.

**Result.** `netflix_clean.csv`, 8,787 rows and 20 columns, reused by Tasks 2, 3 and 4.

**Limitations.** One country label is kept per title, and unrecoverable placeholder dates are flagged rather than corrected.

## Task 2: Exploratory Data Analysis

**Objective.** Understand the shape of the catalog: content mix, geography, ratings, growth over time, and typical durations.

**Method.** Aggregations and charts over the cleaned dataset; each chart saved as a PNG (7 charts in the task folder).

**Key findings.**

- **Catalog mix:** 6,124 movies (69.7%) against 2,663 TV shows (30.3%); films dominate.
- **Geography:** the United States (3,240), India (1,056) and the United Kingdom (638) lead. Each title keeps only one country label and 287 titles are "Unknown", so co-productions are under-counted.
- **Ratings:** TV-MA is the largest rating (3,205 titles), followed by TV-14 (2,155); the catalog targets adults and older teens.
- **Growth:** yearly additions grew from 24 in 2014 to a peak of 2,014 in 2019, then eased to 1,879 in 2020. The 1,498 for 2021 covers only up to 25 September, so it is a partial year and not comparable with full years.
- **Durations:** the median movie runs 98 minutes; 1,790 of 2,663 TV shows have a single season.
- **Data quality:** 14 titles have a negative release-to-addition lag (flagged, not fixed).

**Limitations.** A snapshot of one catalog at one point in time, with one country label per title and a partial 2021.

## Task 3: Content-Based Recommendation System

**Objective.** Given any title, return the 10 most similar titles in the catalog.

**Method.** TF-IDF over a combined text "soup" of genres, director, type, country, rating and release year; cosine similarity between all 8,787 titles; the 10 nearest titles returned per query. Evaluated against random picks on 300 sampled titles.

**Key findings.**

- 84.3% of top-10 recommendations share the query title's primary genre, against 9.3% for random picks; 98.3% share at least one genre, against 23.8% random. The model beats chance by a wide margin.
- Demo: "Dick Johnson Is Dead" returns other recent documentaries (similarity 0.27-0.33); "The Crown" returns British drama series such as "The English Game", "Dracula" and "Black Mirror" (similarity up to 0.98).

**Limitations.** Content features only, with no viewing data, so it finds similar titles rather than personalized picks. The description and cast columns were dropped in Task 1, so plot and actors are not used. The genre-based evaluation is partly circular because genre is one of the features: it shows the model finds similar content, not that people would enjoy it. Merging description and cast back in is the natural next improvement.

## Task 4: Trend Prediction Analysis

**Objective.** Analyze how many catalog titles were released each year and forecast the next few years with simple, honestly tested models.

**Method.** Counted titles per release year (2000-2020; the partial 2021 excluded from training and testing). Compared five models - naive "same as last year", 3-year average, linear trend, exponential trend, and Holt - on a time-ordered holdout (train 2000-2016, test 2017-2020), then refit on all complete years to forecast 2021-2025.

**Key findings.**

- Release-year counts grow slowly until 2014 (352 titles), jump to a peak of 1,144 in 2018, then fall to 1,029 in 2019 and 953 in 2020. Movies drive the decline while TV show counts keep rising, so the catalog is tilting from films toward series.
- The naive model wins the holdout: MAE 138 titles (12.9% MAPE), ahead of Holt (204), the exponential trend (241), the 3-year average (436) and the linear trend (454). A simple model wins because the series turns after 2018; trend-following models overshoot the peak or undershoot from lower training years.
- Forecasts for 2021-2025 disagree by hundreds of titles per year: naive holds flat at 953, the 3-year average at 1,042, and the linear trend climbs from 977 to 1,199. The honest reading is roughly 950-1,200 catalog titles per release year, with wide uncertainty.

**Limitations.** The data ends 25 September 2021, so 2021 is partial. This is a catalog sample, not a measure of production or demand: recent titles have had less time to be added, which may explain part of the post-2018 drop. The holdout has only 4 points around a turning point, and the analysis does not predict Netflix commissioning, budgets or viewer demand.

## Overall notes

- All four notebooks run end to end without errors; the outputs and charts in the notebooks are the ones saved in this package.
- The cleaned data covers titles added to Netflix up to 25 September 2021.
- Source code: https://github.com/HgH7/auspify-data-science-internship
