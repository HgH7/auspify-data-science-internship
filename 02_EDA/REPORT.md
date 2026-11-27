# Part 2: Exploratory Data Analysis - Report

**Objective.** Understand the shape of the Netflix catalog: content mix, geography, ratings, growth over time, and typical durations.

**Method.** Aggregations and charts over the cleaned dataset (8,787 titles), with every chart saved as a PNG in `charts/`.

**Key findings.**

- **Catalog mix:** 6,124 movies (69.7%) against 2,663 TV shows (30.3%); films dominate.
- **Geography:** the United States (3,240), India (1,056) and the United Kingdom (638) lead. Each title keeps only one country label and 287 titles are "Unknown", so co-productions are under-counted.
- **Ratings:** TV-MA is the largest rating (3,205 titles), followed by TV-14 (2,155); the catalog targets adults and older teens.
- **Growth:** yearly additions grew from 24 in 2014 to a peak of 2,014 in 2019, then eased to 1,879 in 2020. The 1,498 for 2021 covers only up to 25 September, so it is a partial year and not comparable.
- **Durations:** the median movie runs 98 minutes; 1,790 of 2,663 TV shows have a single season.
- **Data quality:** 14 titles have a negative release-to-addition lag (flagged, not fixed).

**Limitations.** This is a snapshot of one catalog at one point in time, with one country label per title and a partial 2021.
