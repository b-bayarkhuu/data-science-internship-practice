# Day 2 — Today's Task (Clean the messy data)

Yesterday you loaded and explored the data. **Today you clean it** so it is ready for analysis. Still no model.

## What to do
1. Load `data/A_message_delivery.csv` into pandas (as yesterday).
2. **NULLs:** find them with `df.isna().sum()`. Decide per column — drop, fill, or keep — and write *why*. (e.g. `network_provider` and `recipient_id` have some NULLs.)
3. **Duplicate rows:** `df.duplicated().sum()`, then `df = df.drop_duplicates()`.
4. **Timezones:** `sent_at` has some messy / mixed time-zone text. Parse with `pd.to_datetime(df["sent_at"], errors="coerce")` and decide how to handle the bad ones.
5. **Outliers:** check `message_parts` and `cost` for impossible / extreme values; decide what to do.
6. **Document every decision** in markdown cells (what you changed and why).

⚠️ **Do NOT drop the failed messages** (`delivery_status != "delivered"`) — those are exactly what you will predict later.

## Read today (~1 hour)
- Kaggle **"Pandas"** course: https://www.kaggle.com/learn/pandas
- (Finish ISLP Ch.2 if you did not finish it yesterday.)

## Deliver
A cleaned dataset (save it, e.g. `data/clean.csv`) + a notebook that **explains each cleaning decision**.

## ✅ End of Day 2
- [ ] Found & handled NULLs (documented)
- [ ] Removed duplicate rows
- [ ] Parsed `sent_at` and handled the bad timezones
- [ ] Checked outliers in `message_parts` and `cost`
- [ ] Kept the failed messages
- [ ] Documented every decision
- [ ] Did the Kaggle "Pandas" course
