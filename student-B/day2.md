# Day 2 — Today's Task (Clean the messy data)

Yesterday you loaded and explored the data. **Today you clean it** so it is ready for analysis. Still no model.

## What to do
1. Load `data/B_customer_churn.csv` into pandas (as yesterday).
2. **NULLs:** find them with `df.isna().sum()`. Decide per column — drop, fill, or keep — and write *why*. (e.g. `monthly_spend` and `monthly_usage_gb` have some NULLs.)
3. **Messy text:** `plan_type` has mixed upper/lower case and stray spaces. Clean it:
   ```python
   df["plan_type"] = df["plan_type"].str.strip().str.lower()
   ```
4. **Duplicate rows:** `df.duplicated().sum()`, then `df = df.drop_duplicates()`.
5. **Outliers:** check `tenure_months` (some are negative — impossible) and `monthly_spend` (some are far too large); decide what to do.
6. **Document every decision** in markdown cells (what you changed and why).

⚠️ **Do NOT drop the churned customers** (`is_churned == 1`) — those are exactly what you will predict later.

## Read today (~1 hour)
- Kaggle **"Pandas"** course: https://www.kaggle.com/learn/pandas
- (Finish ISLP Ch.2 if you did not finish it yesterday.)

## Deliver
A cleaned dataset (save it, e.g. `data/clean.csv`) + a notebook that **explains each cleaning decision**.

## ✅ End of Day 2
- [ ] Found & handled NULLs (documented)
- [ ] Cleaned the `plan_type` text (consistent values)
- [ ] Removed duplicate rows
- [ ] Checked outliers in `tenure_months` and `monthly_spend`
- [ ] Kept the churned customers
- [ ] Documented every decision
- [ ] Did the Kaggle "Pandas" course
