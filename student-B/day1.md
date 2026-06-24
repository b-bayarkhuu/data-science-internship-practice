# Day 1 — Today's Task (Customer Churn Prediction)

**Your project:** later in the internship you will build a model that predicts which **customers are likely to leave** (churn). **Today is only setup + understanding your data.** No model yet.

**Your data file:** `B_customer_churn.csv` — one row per customer.
**Target (what you will predict):** `is_churned` → `1` (left) or `0` (stayed).

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
Put `B_customer_churn.csv` inside `data/`. Make small commits often.

## 3. Load the data (notebook)
```python
import pandas as pd
df = pd.read_csv("data/B_customer_churn.csv")
print(df.shape)
df.head()
df.info()
df.describe(include="all")
```

## 4. Understand the columns
- `customer_id` · `plan_type` (⚠ messy text: mixed upper/lower case)
- `tenure_months` — months as a customer · `monthly_spend`
- `monthly_usage_gb` · `call_minutes` · `message_count`
- `days_since_last_payment` · `complaints_count`
- `is_churned` — **target**

```python
df["plan_type"].value_counts(dropna=False)        # you will see messy text
```

## 5. Target balance
```python
df["is_churned"].value_counts(normalize=True) * 100
```
Most customers stay → the data is **imbalanced**. Remember this.

## 6. Read today (~1 hour)
- **ISLP** (free, Python) — Ch.1 (Introduction) + Ch.2 (Statistical Learning): https://www.statlearning.com/
- Reading log (3 lines): what I read / one thing I learned / one thing still unclear.

## ✅ End of Day 1
- [ ] venv + libraries working
- [ ] Git repo + first commit
- [ ] Notebook loads the CSV (shape / head / info / describe)
- [ ] Notes on what each column means
- [ ] Computed the % churned
- [ ] Read ISLP Ch.1–2
