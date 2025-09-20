Title
Fitbit Wellness Analysis — Labmentrix Task 1

Overview
A clean, reproducible exploratory analysis of Fitbit daily activity, sleep, weight, and heart‑rate data. The notebook normalizes IDs, parses dates explicitly, de‑duplicates, aggregates heart‑rate to daily features, merges tables, applies quality checks, computes KPIs, and generates publication‑ready plots.

Repository layout

data_raw: Original CSVs used to run the analysis.

notebook: Main Jupyter notebook.

files/fitness_result: Auto‑generated outputs (CSVs) and plots (PNGs).

exports: Notebook exports (HTML/PDF).

README, .gitignore, LICENSE: Documentation and hygiene.

Quick start

Requirements: Python 3.x; pip install pandas numpy matplotlib seaborn

Data: Place the four CSVs inside data_raw/ with the exact filenames below.

Run: Open notebook/Labmentrix_Task1_Fitbit_EDA.ipynb and “Run All”.

Outputs: Generated to files/fitness_result/ and files/fitness_result/plots/.

Export: From the notebook menu, export to HTML/PDF into exports/.

Datasets
Replace the placeholders with the source links actually used:

dailyActivity_merged.csv — link: <ADD_LINK_HERE>

sleepDay_merged.csv — link: <ADD_LINK_HERE>

weightLogInfo_merged.csv — link: <ADD_LINK_HERE>

heartrate_seconds_merged.csv — link: <ADD_LINK_HERE>

Note on large heart‑rate file
If heartrate_seconds_merged.csv is too large for standard uploads, consider Git LFS or keep it local and rely on the link above. The notebook expects it at data_raw/heartrate_seconds_merged.csv; adjust the path if needed.

Processing steps

ID normalization: Cast all Id columns to string for safe joins.

Datetime parsing: Explicit formats for ActivityDate, SleepDay, weight Date, and HR timestamps with 12‑hour primary and 24‑hour fallback.

De‑duplication: First occurrence per Id+date for daily and sleep.

Heart‑rate features: Daily AvgHR, MaxHR, MinHR, HRCount aggregated from second‑level readings.

Merge and features: Combine daily + sleep + HR on Id+date; numeric casting; weekday feature.

Quality checks: Flag and exclude zero‑step but above‑median‑calorie rows as probable non‑wear from aggregates.

KPIs

Average steps and percent of days ≥ 10,000.

Average sleep minutes and sedentary minutes.

Average daily heart rate (if HR present).

Highest and lowest weekday by average steps.

Visuals (saved to files/fitness_result/plots/)

steps_over_time.png — Steps over time (line).

weekday_bars.png — Avg steps and sleep by weekday (bars).

calories_vs_steps.png — Calories vs steps (scatter + trend).

sleep_distribution.png — Sleep minutes distribution (hist + KDE).

avg_hr_over_time.png — Average daily HR over time (line, if available).

segments_compare.png — Step‑bucket comparisons (grouped bars).

sedentary_vs_steps.png — Sedentary minutes vs steps (scatter + trend).

Reproduce checks

Outputs present: files/fitness_result/*.csv should be > 1 KB; plots folder contains 6–7 PNGs.

Readability: exports/Labmentrix_Task1_Report.html opens cleanly with plots visible.

Paths: If data live elsewhere, update the notebook’s load cell accordingly.

Project structure (suggested)

Labmentrix_Task1_Fitbit_EDA/

data_raw/

dailyActivity_merged.csv

sleepDay_merged.csv

weightLogInfo_merged.csv

heartrate_seconds_merged.csv

notebook/

Labmentrix_Task1_Fitbit_EDA.ipynb

files/

fitness_result/

clean_daily_sleep.csv

agg_by_date.csv

agg_by_weekday.csv

segments_steps.csv

heartrate_daily.csv

plots/

steps_over_time.png

weekday_bars.png

calories_vs_steps.png

sleep_distribution.png

avg_hr_over_time.png

segments_compare.png

sedentary_vs_steps.png

exports/

Labmentrix_Task1_Report.html

Labmentrix_Task1_Report.pdf

README.md

.gitignore

LICENSE

.gitignore (recommended)

.ipynb_checkpoints/

pycache/

.DS_Store

env/

venv/

exports/*.pdf

files/fitness_result/*.csv

files/fitness_result/plots/*.png

License
MIT License. Educational use. Fitbit sample datasets used for demonstration.

Credits
Made by Yashvi Verma ❤️
