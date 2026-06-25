# Day 2 — Today's Task (Clean the messy data)

Yesterday you loaded the data and built a daily/hourly series. **Today you clean it** so it is ready to forecast. Still no model.

## What to do
1. Load `data/C_call_volume.csv` into pandas (as yesterday).
2. **Timezones:** `start_time` has mixed time-zone text — most rows have none, but some end in `+08:00` / `Z` / ` UTC`. Parse it so **every** good row is kept:
   ```python
   df["start_time"] = pd.to_datetime(df["start_time"], errors="coerce", utc=True, format="mixed")
   print("NaT (bad dates):", df["start_time"].isna().sum())
   ```
   ⚠️ **Always print the `NaT` count and check it is small.** Without `format="mixed"`, pandas guesses one format from the first row and silently turns every row that doesn't match into `NaT` — that can quietly drop most of your data. Once the count is small, decide what to do with those few real bad rows (drop or fix).
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
