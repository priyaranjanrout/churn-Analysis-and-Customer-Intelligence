# Churn Analysis & Customer Intelligence

An end-to-end churn analytics pipeline for an OTT subscription platform (Netflix/Hotstar/Prime-style), 
built to identify high-risk subscribers, quantify revenue impact, and recommend data-backed retention actions.

## 📌 Business Challenge

In the hyper-competitive OTT landscape, retention is the only way to survive. This project simulates 
a Data Analyst role tasked with identifying high-risk subscribers using a multi-dimensional dataset 
covering customer demographics, subscription details, and support escalations.

## 🛠️ Tech Stack

- **Python**: `pandas`, `numpy`, `matplotlib`, `seaborn`
- **Database**: SQLite (`sqlite3`) for relational data storage and querying
- **Techniques**: SQL–Python integration, data cleaning, feature engineering, EDA, behavioral visualization

## 🗄️ Database Schema

Three relational tables under the `customer_churn` database:

| Table | Key Columns |
|---|---|
| `db_customer` | customerid, name, country, state, gender, dob, interests, pincode |
| `db_subscription` | customerid, subscription_start_date, subscription_type, renewal_date, plan_type, contract_type, cancellation_date, cancellation_reason, monthly_charges, cltv, churn_score |
| `db_support` | customerid, complaint_date, escalations, csat_score, comment |

## 🔄 Project Workflow

1. **Relational Data Extraction** — Connect Python to SQL databases and pull multi-table datasets
2. **Data Cleaning** — Fix data types, rename/select columns, handle missing/null values, QC checks
3. **Feature Engineering** — Calculate tenure, churn rates, customer aging, and other derived metrics
4. **Exploratory Data Analysis** — Aggregation, group-by, pivot tables to uncover churn patterns
5. **Data Visualization** — Behavioral trends via matplotlib/seaborn
6. **Executive Reporting** — Translate findings into actionable, business-facing insights

## 📊 Key KPIs Calculated

| KPI | Formula |
|---|---|
| Churn Rate | churned customers / total customers |
| Retention Rate | 1 − churn rate |
| ARPU | SUM(monthly_charges) / active customers |
| Avg. Customer Tenure | AVG(cancellation_date or now − subscription_start_date) |
| Revenue at Risk | SUM(monthly_charges) WHERE churn_score > 70 |
| Escalation Rate | escalations / complaints × 100 |
| Escalation → Churn Correlation | churn rate WHERE escalations ≥ 1 vs. 0 |

Plus churn broken down by plan type, state/region, and contract type.

## 💡 Key Insights

- **Churn Rate: 28.6%** | Retention Rate: 71.4%
- Monthly-contract subscribers churned at **55.6%** — nearly **7x** the annual-contract churn rate of **8.3%**
- Karnataka showed the highest regional churn concentration; most churn activity occurred in Sep 2024
- Most churn came from the Basic plan tier — limited overall revenue impact
- **Revenue loss due to churn: ~$74/mo | CLTV lost: ~$2,047** (≈18% revenue loss)
- Average customer tenure: 1,451 days | ARPU: ~$18.8

## ✅ Recommended Actions

- Investigate the Karnataka churn spike — pricing changes, complaints, or service issues
- Review whether Basic plan pricing changed around September
- Analyze competitor moves for customers who switched away
- Prioritize outreach (email/SMS/calls) to High/Medium churn-risk customers based on CLTV

## 📈 Business Impact Summary

Engineered an end-to-end churn analytics pipeline for an OTT subscription dataset (20+ KPIs), identifying 
a 28.6% overall churn rate and surfacing that monthly-contract subscribers churned at 55.6% — 6.7x the 
8.3% annual-contract rate — directly attributing ~$74/mo in MRR leakage and ~$2,047 in CLTV erosion to 
at-risk customers, enabling a targeted contract-migration retention strategy.

## 🔗 Applicability

While built on OTT/streaming data, this framework generalizes to any subscription or repeat-purchase 
business model — **E-commerce, SaaS, Fintech, Adtech, Telecom, and Banking**.

## 📂 Repo Structure

├── churnAnalysis.ipynb       # Main analysis notebook
├── customer_churn_data_raw.xlsx   # (optional) raw source data
├── README.md
└── requirements.txt

## 🚀 How to Run

```bash
pip install -r requirements.txt
jupyter notebook churnAnalysis.ipynb
```

---

author-Santosh kumar patra
