# Day 1 — Today's Task (Event Volume Forecasting)

**Your project:** later in the internship you will build a model that **forecasts how many events (calls)** happen per hour / per day. **Today is only setup + understanding your data.** No model yet.

**Your data file:** `C_call_volume.csv` — one row per event (call).
**Target:** there is NO ready column — you **aggregate** the rows into a count of events **per hour / per day**. That count is what you will forecast.

---

## 1. Set up (terminal)
```bash
mkdir my-project && cd my-project
python3 -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install pandas numpy jupyter matplotlib
jupyter notebook
```

## 2. Git repo
```bash
git init
printf "venv/\n.ipynb_checkpoints/\ndata/*.csv\n" > .gitignore
mkdir data notebooks
git add .gitignore && git commit -m "chore: init repo"
```
Put `C_call_volume.csv` inside `data/`. Make small commits often.

## 3. Load the data (notebook)
```python
import pandas as pd
df = pd.read_csv("data/C_call_volume.csv")
print(df.shape)
df.head()
df.info()
```

## 4. Understand the columns
- `event_id` · `node_id` · `source_id` · `target_id` · `direction` (inbound/outbound)
- `start_time` — event start (your forecast is built on this)
- `connect_time`, `end_time` — filled in only when `call_result` = `answered`
- `duration_sec`, `billed_seconds` · `call_result` (answered / no_answer / busy / failed) · `cost`

## 5. Build the time series (no ready target)
```python
# Some rows have messy timezones, so errors="coerce" turns bad ones into NaT (clean later)
df["start_time"] = pd.to_datetime(df["start_time"], errors="coerce")
print("NaT (bad dates):", df["start_time"].isna().sum())

valid = df.dropna(subset=["start_time"])
daily = valid.set_index("start_time").resample("1D").size()
daily.plot(title="Events per day")    # look for a weekly pattern and a trend
```

## 6. Read today (~1 hour)
- **ISLP** (free, Python) — Ch.2 (Statistical Learning): https://www.statlearning.com/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## ✅ End of Day 1
- [ ] venv + libraries working
- [ ] Git repo + first commit
- [ ] Notebook loads the CSV (shape / head / info)
- [ ] Notes on what each column means
- [ ] Aggregated an hourly/daily series + plotted the daily chart
- [ ] Read ISLP Ch.2
