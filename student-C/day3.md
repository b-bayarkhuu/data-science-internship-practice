# Day 3 — Today's Task (Explore the time series — EDA)

Yesterday you cleaned the data and rebuilt a clean daily/hourly count. **Today you explore that series** to find its patterns — before building anything. Still no model.

## What to do
1. Start from your **clean daily and hourly** event-count series from Day 2.
2. **Daily plot + trend:** plot the daily count over time. Is there an overall **trend** (slowly rising or falling)?
3. **Weekly seasonality:** compare weekdays vs weekends.
   ```python
   daily.groupby(daily.index.dayofweek).mean()   # 0 = Mon ... 6 = Sun
   ```
   Are weekends lower than weekdays?
4. **Daily seasonality (busy hours):** average the hourly count by hour of day and find the peak.
   ```python
   hourly.groupby(hourly.index.hour).mean().plot(kind="bar")   # which hours are busiest?
   ```
5. **Write down the 3 patterns** you find: is there a trend? what is the weekly shape? which are the busy hours?
6. **Document** each chart in markdown (1–2 lines).

> These three patterns — **trend + weekly seasonality + daily seasonality** — are exactly what your forecast will have to capture later. Today is about *seeing* them clearly.

## Read today (~1 hour)
- **FPP3 (Python) Ch.1–2** — forecasting concepts + time-series graphics (seeing trend / seasonality): https://otexts.com/fpppy/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## Deliver
A short EDA notebook: the daily plot, the weekday-vs-weekend comparison, the busy-hour chart, and your 3 patterns written in plain words.

## ✅ End of Day 3
- [ ] Plotted the daily series and described the trend
- [ ] Compared weekday vs weekend (weekly seasonality)
- [ ] Found the busy hours (daily seasonality)
- [ ] Wrote down the 3 patterns in plain words
- [ ] Understood that these patterns are what the forecast must capture
- [ ] Read FPP3 Ch.1–2
