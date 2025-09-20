Fitbit Wellness Analysis — Labmentrix Task 1 ✨

Clean, reproducible exploratory analysis of Fitbit daily activity, sleep, weight, and heart‑rate data. The notebook normalizes IDs, parses dates explicitly, de‑duplicates rows, aggregates HR to daily metrics, merges sources, applies quality checks, computes KPIs, and produces publication‑ready visuals. 📊

Highlights 🚀

-End‑to‑end pipeline: parsing, joins, QC, KPIs, and visuals in one notebook.
-Seven focused plots for insights and presentations.
-Auto‑saved CSVs and PNGs for reuse and reporting.

Repository layout 🧭

-data_raw — Original CSVs used for the analysis.
-notebook — Main Jupyter notebook.
-files/fitness_result — Generated CSVs and plots (PNGs) from the notebook.
-exports — HTML/PDF exports of the notebook.
-README, .gitignore, LICENSE — Documentation and hygiene.

text
Labmentrix_Task1_Fitbit_EDA/
├─ data_raw/
├─ notebook/
├─ files/fitness_result/
│  └─ plots/
├─ exports/
└─ README.md

Quick start 🛠️

-Requirements: Python 3.x; install: pandas, numpy, matplotlib, seaborn.
-Data: Place all four CSVs in data_raw/ with the exact filenames listed below.
-Run: Open notebook/Labmentrix_Task1_Fitbit_EDA.ipynb and “Run All.”
-Outputs: CSVs in files/fitness_result/ and PNGs in files/fitness_result/plots/.
-Export: Use File → Export to create HTML/PDF in exports/.

Datasets 🔗

-dailyActivity_merged.csv — source: <https://drive.google.com/file/d/1DwhJNPjIlJ94F8fjK_SMSXGSzumX8Gww/view?usp=drive_link>
-sleepDay_merged.csv — source: <https://drive.google.com/file/d/1qS1MQBvC47rmrX1yHpB5LkDOjehGpdgP/view?usp=drive_link>
-weightLogInfo_merged.csv — source: <https://drive.google.com/file/d/1x0k5c9tgRviMjqTluhoUPhkO_p3wjDkK/view?usp=drive_link>
-heartrate_seconds_merged.csv — source: <https://drive.google.com/file/d/1yAn5emRYfDFSO5yFu6lvvKtS5GYG17Uu/view?usp=drive_link>

Processing steps ⚙️
-ID normalization: Cast Id to string across all tables to ensure safe joins.
-Datetime parsing: Explicit formats for ActivityDate, SleepDay, Weight Date, and HR timestamps (12‑hour primary, 24‑hour fallback).
-De‑duplication: First per Id+date for daily and sleep tables.
-HR features: Daily AvgHR, MaxHR, MinHR, HRCount from second‑level readings.
-Merge and features: Join daily + sleep + HR by Id+date; numeric casting; weekday feature.
-Quality checks: Zero‑step but above‑median‑calorie rows flagged as probable non‑wear and excluded from aggregates.


KPIs 📈
-Average steps and share of days ≥ 10,000.
-Average sleep minutes and sedentary minutes.
-Average daily heart rate (if HR present).
-Highest and lowest weekday by average steps.

Visuals (auto‑saved) 🖼️

-steps_over_time.png — Steps over time (line).
-weekday_bars.png — Avg steps and sleep by weekday (bars).
-calories_vs_steps.png — Calories vs steps (scatter + trend).
-sleep_distribution.png — Sleep minutes distribution (hist + KDE).
-avg_hr_over_time.png — Average daily HR over time (line, if available).
-segments_compare.png — Step‑bucket comparisons (grouped bars).
-sedentary_vs_steps.png — Sedentary minutes vs steps (scatter + trend).

All plots are saved to files/fitness_result/plots/.

Reproduce checks ✅
-files/fitness_result/ contains generated CSVs (>1 KB typical).
-files/fitness_result/plots/ contains 6–7 PNGs after running plot cells.
-exports/Labmentrix_Task1_Report.html opens with charts visible.
-If data are in a different location, update the load paths in the notebook.

.gitignore (recommended) 🧹

- .ipynb_checkpoints/
- pycache/
- .DS_Store
- env/ or venv/

License 📄
MIT License. Educational use. Fitbit sample datasets used for demonstration.

Credits 🙏
Made by Yashvi Verma ❤️
