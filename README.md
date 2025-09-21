🎯 Fitbit Wellness Analysis — Labmentrix Task 1

✨ Clean, reproducible analysis of Fitbit daily activity, sleep, weight, and heart-rate data with a 3-layer pipeline:
🐍 Python EDA, 🐘 PostgreSQL data cleaning/metrics, and 📊 Power BI dashboard built from clean CSV exports.

📦 What’s Inside

🔄 End-to-end pipeline: raw CSVs → Python normalization/QC → SQL typed tables/views → Power BI visuals

📈 Seven+ publication-ready plots saved from the notebook for reuse in slides and reports

⚡ One-click dashboard with KPIs for steps, sleep, calories, and 10k-steps adherence

🗂 Repository Layout 🧭

📁 data_raw — Original CSVs used for the analysis
📓 notebook — Main Jupyter notebook for parsing, merges, QC, KPIs, and plots
📊 files/fitness_result — Generated CSVs from Python/SQL; subfolder plots/ contains PNG charts
📤 exports — HTML/PDF exports of the notebook for sharing
🛠 sql — PostgreSQL script for loading, cleaning, deduping, indexing, and analysis views
📌 powerbi — .pbix for the final dashboard (screenshot included)

🚀 Quick Start 🛠️

🖥 Requirements: Python 3.x with pandas, numpy, matplotlib, seaborn; PostgreSQL 14+; Power BI Desktop

📂 Data: Place the four CSVs below in data_raw/ with exact filenames

▶️ Run Python EDA: Open notebook/Labmentrix_Task1_Fitbit_EDA.ipynb and “Run All” to produce clean merges and plots

🐘 Run SQL cleaning: Execute sql/fitness_sql_analysis.sql in PostgreSQL to create typed, deduped daily activity and sleep tables/views

📊 Build dashboard: Point Power BI to the cleaned CSVs or to database views to refresh visuals

📑 Datasets 🔗

dailyActivity_merged.csv — Download

sleepDay_merged.csv — Download

weightLogInfo_merged.csv — Download

heartrate_seconds_merged.csv — Download

🔬 Notebook Processing ⚙️

🆔 ID normalization: Cast Id to string across all tables for safe joins

🕒 Datetime parsing: Explicit formats for ActivityDate, SleepDay, Weight Date, and HR timestamps with 12-h primary and 24-h fallback

🗑 De-duplication: First occurrence per Id+date for daily and sleep tables

❤️ HR features: Daily AvgHR, MaxHR, MinHR, HRCount from second-level readings

🔗 Merge + features: Join daily + sleep + HR on Id+date; cast numerics; derive weekday

🛡 Quality checks: Flag zero-steps but above-median-calories as likely non-wear and exclude from aggregates

🐘 SQL Layer (PostgreSQL)

📥 Raw → typed: Load raw tables; trim, NULL-normalize, and cast to proper types

📅 Date parsing: Handle MM/DD/YYYY and ISO forms; create DATE-typed activitydate/sleepdate

🗑 Deduping: Keep best row per Id+date via row_number()

⚡ Indexing: id/date indexes for fast BI queries; convenience view v_user_daily_summary

🔍 Useful queries: overall averages, per-user steps, steps–calories correlation, weekday patterns, sleep joins

📊 KPIs 📈

👣 Average daily steps and % of days ≥ 10,000

💤 Average sleep minutes and sedentary minutes

🔥 Average daily calories and HR (if present)

📅 Best and worst weekday by average steps

📈 Power BI Dashboard

🃏 Cards: Avg Steps, Avg Sleep (hrs), Avg Calories, % Days ≥10k steps

🔘 Visuals: Calories vs Steps scatter, Avg Sleep by Weekday, Steps over Time, steps–sleep table with slicers

🔗 Data sources: Cleaned CSVs or PostgreSQL views for live refresh

🖼 Visuals Auto-Saved by Notebook

📊 steps_over_time.png — Steps trend
📊 weekday_bars.png — Avg steps & sleep by weekday
📊 calories_vs_steps.png — Scatter + trend
😴 sleep_distribution.png — Sleep minutes distribution
❤️ avg_hr_over_time.png — HR trend
📊 segments_compare.png — Step-bucket comparisons
📊 sedentary_vs_steps.png — Sedentary vs steps scatter

✅ Repro Checklist

✔️ files/fitness_result/ contains generated CSVs

✔️ files/fitness_result/plots/ contains PNG charts

✔️ exports/Labmentrix_Task1_Report.html opens with charts

✔️ Power BI opens and calculates cards/plots

📤 How to Export

📓 Notebook → File → Export to HTML/PDF into exports/

🐘 SQL → psql \copy SELECTs to CSV for BI; commit sql/fitness_sql_analysis.sql

📊 Power BI → File → Export → PDF for slide-ready pages

📝 .gitignore 🧹

.ipynb_checkpoints/

__pycache__/

.DS_Store

env/ or venv/

.pbix.lock.json (if Power BI creates locks)

⚖️ License 📄

MIT License; educational use; Fitbit sample datasets for demonstration

🙌 Credits 🙏

Built by Yashvi Verma ❤️
🐍 Python • 🐘 PostgreSQL • 📊 Power BI
