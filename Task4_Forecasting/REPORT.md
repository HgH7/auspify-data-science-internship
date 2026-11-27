# Task 4: Trend Prediction Analysis - Report

**Objective.** Analyze how many catalog titles were released each year and forecast the next few years with simple, honestly tested models.

**Method.** Counted titles per release year (2000-2020; partial 2021 excluded), then compared five models - naive "same as last year", 3-year average, linear trend, exponential trend, and Holt - on a time-ordered holdout (train 2000-2016, test 2017-2020), and refit the best ones on all complete years to forecast 2021-2025.

**Key findings.**

- Release-year counts grow slowly until 2014 (352 titles), jump to a peak of 1,144 in 2018, then fall to 1,029 in 2019 and 953 in 2020. Movies drive the decline while TV shows keep rising.
- The naive model wins the holdout: MAE 138 titles (12.9% MAPE), ahead of Holt (204), exponential trend (241), 3-year average (436) and linear trend (454). A simple model wins because the series turns after 2018.
- Forecasts for 2021-2025 disagree by hundreds of titles per year: naive holds flat at 953, the 3-year average at 1,042, and the linear trend climbs from 977 to 1,199. The honest reading is roughly 950-1,200 catalog titles per release year, with wide uncertainty.

**Limitations.** The data ends 25 September 2021, so 2021 is partial. This is a catalog sample, not a measure of production or demand: recent titles have had less time to be added, which may explain part of the post-2018 drop. The holdout has only 4 points around a turning point, and the analysis does not predict Netflix commissioning or viewer demand.
