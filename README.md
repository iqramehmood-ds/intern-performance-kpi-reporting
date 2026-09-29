# Intern Performance Evaluation & Monthly Reporting System

Internship Task 6  designing and automating a KPI system to track intern performance and generate monthly reports for supervisors.

## Objective

The task was to design KPIs for evaluating intern performance, automate the calculations, and produce monthly reports. The internship platform didn't provide a dataset (same as the earlier tasks), so I built a synthetic dataset 25 interns, 5 departments, 4 months of activity, 307 task records  to design and test the pipeline on. The pipeline provides a reusable starting point for real task-tracking data, provided the date fields and task status assumptions are aligned.

## KPIs

- **Task Timeliness**  on-time completion rate (% of tasks submitted by the deadline) and average delay in days across all tasks, with on-time tasks counted as zero delay
- **Project Quality**  average mentor-rated quality score (out of 10)
- **Mentor Feedback**  average mentor-rated feedback score (out of 5), covering communication, initiative, and responsiveness separately from quality
- **Composite Score**  a 0–100 project-defined indicator combining quality (40%), on-time rate (30%), and mentor feedback (30%). Used to summarize monthly results and group scores into Needs Support, On Track, or Strong Performer bands

## Tools

Python (pandas, NumPy, openpyxl)

## Project structure

```
generate_data.py                    synthetic dataset generator
intern_tasks.csv                    raw task level data
kpi_pipeline.py                     extraction + KPI computation + Excel report builder
monthly_kpi_summary.csv             computed KPIs, one row per intern per month
monthly_performance_report.xlsx     supervisor-facing report (monthly sheets + overall summary)
```

## How it works

1. `generate_data.py` creates the synthetic task dataset (skip this step with real data).
2. `kpi_pipeline.py` reads the task records, derives on time flags and delay days, groups tasks by intern and assignment month, computes the KPIs above, and writes both a CSV and a formatted Excel workbook (monthly sheets plus an overall summary).

## How to run

```
python generate_data.py
python kpi_pipeline.py
```

Run both from the project directory. Required libraries: `pandas`, `numpy`, `openpyxl`.

## Sample result

Across the four month simulation, 85 of 100 intern-month records fell into the Strong Performer band, 14 into On Track, and 1 into Needs Support. An intern month represents one intern's results for one month. These categories reflect the project's chosen score thresholds, not real world evaluations.

## Limitations

Mentor scoring is subjective and not normalized across mentors. The 40/30/30 composite weighting is a starting judgment call, not tuned against real outcome data. The dataset here is synthetic. The pipeline provides a reusable starting point for real task tracking data, provided the date fields and task status assumptions are aligned.
