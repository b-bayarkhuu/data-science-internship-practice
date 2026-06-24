# Day 1 — Today's Task (Message Delivery Prediction)

**Your project:** later in the internship you will build a model that predicts whether a message is **delivered** or **fails**. **Today is only setup + understanding your data.** No model yet.

**Your data file:** `A_message_delivery.csv` — one row per message.
**Target (what you will predict):** `delivery_status` → `delivered`, or a failure (`failed` / `expired` / `rejected`).

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
Put `A_message_delivery.csv` inside `data/`. Make small commits often.

## 3. Load the data (notebook)
```python
import pandas as pd
df = pd.read_csv("data/A_message_delivery.csv")
print(df.shape)         # rows / columns
df.head()
df.info()               # types, NULLs
df.describe(include="all")
```

## 4. Understand the columns
- `message_id`, `campaign_id`, `account_id`, `sender_name`, `recipient_id`
- `network_provider` — which network sent the message
- `sent_at` — time sent · `delivered_at` — time delivered (filled in only when delivered)
- `delivery_status` — **target** · `error_code` · `message_parts` · `cost`

## 5. Target balance
```python
df["delivery_status"].value_counts(dropna=False)
print((df["delivery_status"] != "delivered").mean() * 100, "% failed")
```
Most messages are delivered → the data is **imbalanced**. Remember this.

## 6. Read today (~1 hour)
- **ISLP** (free, Python) — Ch.1 (Introduction) + Ch.2 (Statistical Learning): https://www.statlearning.com/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## ✅ End of Day 1
- [ ] venv + libraries working
- [ ] Git repo + first commit
- [ ] Notebook loads the CSV (shape / head / info / describe)
- [ ] Notes on what each column means
- [ ] Computed the % failed
- [ ] Read ISLP Ch.1–2
