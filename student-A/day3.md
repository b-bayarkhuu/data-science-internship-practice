# Day 3 — Today's Task (Explore the data — EDA)

Yesterday you cleaned the data. **Today you explore it** to understand *what makes a message fail* — before building anything. Still no model.

## What to do
1. Load your **cleaned** data from Day 2 (not the raw CSV).
2. **Target balance again:** plot `delivery_status` counts and write the **failure %** clearly. Every model you build later must beat "always predict delivered", so keep this number in front of you.
3. **Distributions:** plot histograms of `message_parts`, `cost`, and the hour of day (from `sent_at`):
   ```python
   df["hour"] = df["sent_at"].dt.hour
   ```
4. **Failure rate by group — the core of today.** First make a 0/1 flag, then compare the failure rate across groups:
   ```python
   df["is_failed"] = (df["delivery_status"] != "delivered").astype(int)
   df.groupby("network_provider")["is_failed"].mean().sort_values()   # which provider fails most?
   df.groupby("hour")["is_failed"].mean()                              # are nights worse?
   df.groupby("message_parts")["is_failed"].mean()                     # do longer messages fail more?
   ```
5. **Write 3 ideas** about what makes a message fail, and **test each one with a plot**.
6. **Document** what you found in markdown (1–2 lines per chart).

⚠️ **Do NOT use `delivered_at`.** It is filled in only *after* a message is delivered, so it already "knows the answer". (You will learn the name for this on Day 4: **data leakage**.)

## Read today (~1 hour)
- **ISLP Ch.3** (Linear Regression — how predictors relate to an outcome): https://www.statlearning.com/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## Deliver
A short EDA notebook: the failure %, a few clear charts, and your 3 tested ideas — each with a one-line finding.

## ✅ End of Day 3
- [ ] Plotted the target balance and wrote the failure %
- [ ] Plotted distributions of the main columns
- [ ] Compared failure rate by `network_provider` / hour / `message_parts`
- [ ] Wrote 3 ideas and tested each with a plot
- [ ] Understood why **accuracy alone** will mislead on imbalanced data
- [ ] Read ISLP Ch.3
