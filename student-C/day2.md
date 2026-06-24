# Day 2 — Today's Task (Clean the messy data)

Yesterday you loaded the data and built a daily/hourly series. **Today you clean it** so it is ready to forecast. Still no model.

## What to do
1. Load `data/C_call_volume.csv` into pandas (as yesterday).
2. **Timezones:** `start_time` has some messy / mixed time-zone text. Parse with
   `pd.to_datetime(df["start_time"], errors="coerce")`. Some rows become `NaT` (bad dates) — count them and decide: drop them, or fix them.
3. **Duplicate rows:** `df.duplicated().sum()`, then `df = df.drop_duplicates()`.
4. **Outliers:** check `duration_sec` (some are negative — impossible); decide what to do.
5. **Normal empties (do NOT "fix"):** `connect_time` / `end_time` are empty when `call_result` is not `answered` (no-answer / busy / failed). That is correct, not a data error.
6. **Document every decision** in markdown cells (what you changed and why).

After cleaning, rebuild your **daily and hourly event-count series** from the clean `start_time`.

## Read today (~1 hour)
- Kaggle **"Pandas"** course: https://www.kaggle.com/learn/pandas
- (Finish ISLP Ch.2 if you did not finish it yesterday.)

## Deliver
A cleaned dataset + a clean daily/hourly series, in a notebook that **explains each cleaning decision**.

## ✅ End of Day 2
- [ ] Parsed `start_time` and handled the `NaT` / bad timezones
- [ ] Removed duplicate rows
- [ ] Checked outliers in `duration_sec`
- [ ] Understood that empty `connect_time`/`end_time` for non-answered calls is normal
- [ ] Rebuilt the clean daily/hourly series
- [ ] Documented every decision
- [ ] Did the Kaggle "Pandas" course
