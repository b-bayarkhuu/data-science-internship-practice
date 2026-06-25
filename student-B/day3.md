# Day 3 — Today's Task (Explore the data — EDA)

Yesterday you cleaned the data. **Today you explore it** to understand *what makes a customer churn* — before building anything. Still no model.

## What to do
1. Load your **cleaned** data from Day 2 (not the raw CSV).
2. **Target balance again:** plot `is_churned` and write the **churn %** clearly. Every model you build later must beat "always predict stay", so keep this number in front of you.
3. **Distributions:** plot histograms of `tenure_months`, `monthly_spend`, `monthly_usage_gb`, and `complaints_count`.
4. **Churn rate by group — the core of today.** Compare the churn rate across groups:
   ```python
   df.groupby("complaints_count")["is_churned"].mean()         # do more complaints mean more churn?
   df.groupby("plan_type")["is_churned"].mean()                # does the plan matter?
   # for numeric columns, bucket first, then group:
   df["tenure_bucket"] = pd.cut(df["tenure_months"], bins=[0, 6, 12, 24, 48, 72])
   df.groupby("tenure_bucket")["is_churned"].mean()            # do newer customers churn more?
   ```
5. **Write 3 ideas** about what makes a customer churn, and **test each one with a plot**.
6. **Document** what you found in markdown (1–2 lines per chart).

⚠️ Think about **leakage**: do not use any column that is only known *after* a customer has already left. (More on this on Day 4.)

## Read today (~1 hour)
- **ISLP Ch.3** (Linear Regression — how predictors relate to an outcome): https://www.statlearning.com/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## Deliver
A short EDA notebook: the churn %, a few clear charts, and your 3 tested ideas — each with a one-line finding.

## ✅ End of Day 3
- [ ] Plotted the target balance and wrote the churn %
- [ ] Plotted distributions of the main columns
- [ ] Compared churn rate by `complaints_count` / `plan_type` / tenure buckets
- [ ] Wrote 3 ideas and tested each with a plot
- [ ] Understood why **accuracy alone** will mislead on imbalanced data
- [ ] Read ISLP Ch.3
