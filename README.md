<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:8e0e00,50:c31432,100:240047&height=180&section=header&text=Telecom%20Churn%20Analysis&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=38" alt="Telecom Churn Analysis"/>
</div>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=500&size=20&pause=1000&color=FF6B6B&center=true&vCenter=true&width=640&lines=Who%27s+leaving%3F+Who%27s+next%3F+How+do+we+keep+them%3F;7%2C000+customers+%E2%80%A2+31.5%25+churn+%E2%80%A2+%E2%82%B91.6L%2Fmo+at+risk;EDA+%E2%86%92+prediction+model+%E2%86%92+retention+plan" alt="typing"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn"/>
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="pandas"/>
  <img src="https://img.shields.io/badge/seaborn-4C72B0?style=for-the-badge" alt="seaborn"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter"/>
  <img src="https://img.shields.io/badge/seed_42-deterministic-FF6B6B?style=for-the-badge" alt="deterministic"/>
</p>

> **31.5% of customers are churning**, and over a third of monthly revenue walks out the door with them. This project finds out *who* leaves, *why*, and *which 712 customers* a retention campaign should call first.

---

## 📊 The headline numbers

| Metric | Value |
|---|---|
| Customers analyzed | 7,000 |
| Overall churn rate | **31.5%** |
| Monthly revenue at risk | **₹1,62,148** (34.8% of revenue) |
| Avg tenure — churned vs retained | 14.6 vs 29.9 months |
| Model test accuracy | 74.9% |

![churn overview](visuals/01_churn_overview.png)

## 🔑 Finding #1 — the contract is the lever

Month-to-month customers churn at **46.1%**. Two-year contracts: **6.8%**. Contract type is the strongest coefficient in the model — nothing else comes close.

![churn by contract](visuals/02_churn_by_contract.png)

## ⏳ Finding #2 — the first year is the danger zone

Customers in months 0–12 churn at **~56%**. Survive past year four and it drops to **~9%**. Retention isn't a general problem — it's an onboarding problem.

![churn by tenure cohort](visuals/03_churn_by_tenure_cohort.png)

## 🎯 Finding #3 — the 712 worth calling first

Stack the risk factors — month-to-month **+** fiber optic **+** no tech support **+** tenure ≤ 12 months — and you get **712 customers (10.2% of the base) churning at 68%**, with **₹62,098/month** of revenue at risk. That's not a segment, that's a call list.

![top churn drivers](visuals/09_top_churn_drivers.png)

## 🤖 The model

Logistic regression on engineered tenure/cohort features. Not the fanciest algorithm — deliberately: in churn, *explainability beats accuracy*, because the retention team needs to know **why** someone is flagged.

![confusion matrix](visuals/08_confusion_matrix.png)

---

## ⚙️ How it works

```mermaid
flowchart LR
    A["📊 7,000 customers<br/>21 features"] --> B["🔍 EDA<br/>churn by segment"]
    B --> C["🤖 Model<br/>logistic regression"]
    C --> D["🎯 Risk segments<br/>712 high-risk"]
    D --> E["💰 Retention plan<br/>₹62K/mo at risk"]
    style E fill:#8e0e00,stroke:#FF6B6B,stroke-width:2px,color:#fff
```

## 📂 What's inside

```
├── generate_data.py              # synthetic customer base, seed 42
├── analysis.py                   # EDA → model → segments → charts
├── build_notebook.py             # builds the notebook from the pipeline
├── Customer_Churn_Analysis.ipynb # narrated case-study notebook (34 cells)
├── findings.md                   # stakeholder summary
├── data/
│   └── telecom_churn.csv         # 7,000 customers × 21 columns
└── visuals/                      # 9 charts (shown above)
```

## ▶️ Run it

```bash
pip install -r requirements.txt
python3 generate_data.py    # build the dataset
python3 analysis.py         # full analysis + 9 charts
```

Or open the notebook — same analysis, narrated step by step. Deterministic: rebuild from scratch, every number reproduces exactly.

---

## 🔭 Where I'd take it next

- **Uplift modeling** — predict *who responds to retention offers*, not just who churns. Calling everyone wastes money; calling the persuadable saves it.
- **Survival analysis** — model *time-to-churn* (Cox PH) instead of binary churn, so campaigns fire *before* risk peaks.
- **Offer ROI simulator** — price discount vs. saved lifetime value per segment; find the retention spend that pays for itself.

---

*Synthetic customer base (seed 42) with realistic churn behavior — short tenure, month-to-month contracts, and fiber-without-support all raise risk, mirroring real telecom patterns. Pipeline works identically on live data.*

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:8e0e00,50:c31432,100:240047&height=110&section=footer" alt="footer"/>
</div>
