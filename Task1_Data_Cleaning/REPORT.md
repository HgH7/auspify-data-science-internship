# Task 1: Data Cleaning and Preprocessing - Report

**Objective.** Turn the raw Netflix titles file into a clean, analysis-ready dataset that the later tasks can rely on.

**Method.** Loaded the raw data (8,807 rows), checked for duplicates and for missing values hidden as placeholder text, fixed inconsistent formats, and transformed the date, duration, genre and rating columns into usable types.

**Key findings.**

- 3 records were exact duplicates under a different `show_id` (same title, country and date added); removed.
- `director` and `country` hid missing values as the text `'Not Given'`; converted to proper missing values and filled with `'Unknown'` so no rows were lost.
- `date_added` was stored as text in mixed formats; converted to datetime and derived year, month, month name and weekday columns.
- `duration` mixed minutes (movies) and seasons (TV shows) in one column; split into numeric minutes and numeric seasons.
- A few titles had been date-mangled by Excel before the file was received; they are flagged and left unchanged rather than guessed.

**Result.** `netflix_clean.csv` with 8,787 rows and 20 columns, one row per title, used as the input for Tasks 2, 3 and 4.

**Limitations.** A single country label is kept per title, and placeholder dates that could not be recovered are flagged rather than corrected.
