# Customer Segmentation Analysis

**Track:** Data Analytics — Level 1, Task 2
**Internship:** Oasis Infobyte SIP
**Repository:** [github.com/rneeraja080803/OIBSIP](https://github.com/rneeraja080803/OIBSIP)

## Objective
Apply clustering algorithms to segment an e-commerce company's customer base into distinct groups based on purchasing behaviour, enabling targeted marketing strategies.

## Dataset
**Online Retail Dataset** (UCI Machine Learning Repository, via Kaggle) — 541,909 transaction line items from a UK-based online retailer, December 2010–December 2011.

> 📥 **Note:** The raw CSV (~46MB) is not included in this repo due to GitHub's file size limits for web uploads. Download it here before running the notebook:
> - **Kaggle:** [Customer Segmentation Dataset by M Yasser H](https://www.kaggle.com/datasets/yasserh/customer-segmentation-dataset) → download `Online Retail.csv`
> - **UCI (original source):** [archive.ics.uci.edu/dataset/352/online+retail](https://archive.ics.uci.edu/dataset/352/online+retail)
>
> Once downloaded, place `Online_Retail.csv` in this same folder before running the notebook — the code expects it at that path.

## Tech Stack
Python, pandas, scikit-learn (KMeans, StandardScaler), matplotlib, seaborn, Jupyter Notebook

## Methodology
1. **Data cleaning** — dropped rows with missing `CustomerID`, removed cancelled orders (InvoiceNo starting with 'C'), removed negative quantity/price rows (397,884 clean rows, 4,338 unique customers remain)
2. **RFM feature engineering** — Recency (days since last purchase), Frequency (distinct invoice count), Monetary (total spend) per customer
3. **Standardisation** — `StandardScaler` applied before clustering, since RFM features are on very different scales
4. **K-Means + Elbow Method** — tested K=1 to 10, selected **K=4** based on the elbow point
5. **Cluster visualisation** — scatter plots (log-scaled, due to one extreme outlier cluster) across Recency/Monetary and Frequency/Monetary
6. **Cluster profiling** — mean RFM values per cluster, customer counts, and per-segment marketing recommendations

## Key Finding
Clustering surfaced a **non-obvious insight**: a tiny cluster of just **13 customers** shows extreme frequency (~82 orders) and spend (~£127K average) — these behave like wholesale/B2B accounts, not typical retail shoppers. This required using a log scale on the visualisations, since this cluster would otherwise be invisible against the other ~4,300 customers.

## Cluster Summary

| Cluster | Label | Avg Recency | Avg Frequency | Avg Monetary | Count |
|---|---|---|---|---|---|
| 2 | VIP / Wholesale Champions | 7.4 days | 82.5 orders | £127,338 | 13 |
| 3 | Loyal High-Value Customers | 15.5 days | 22.3 orders | £12,709 | 204 |
| 0 | Regular / Active Customers | 43.7 days | 3.7 orders | £1,359 | 3,054 |
| 1 | At-Risk / Lapsed Customers | 248.1 days | 1.6 orders | £481 | 1,067 |

## How to Run
```bash
# 1. Download Online_Retail.csv from the Kaggle/UCI links above and place it in this folder

# 2. Install dependencies
pip install pandas scikit-learn matplotlib seaborn jupyter

# 3. Run the notebook
jupyter notebook Customer Segmentation.ipynb
```

## Note on Data
Dates are parsed with `pd.to_datetime(..., format='%d-%m-%Y %H:%M')`. Cluster visualizations use a log scale on the Monetary axis due to the extreme outlier cluster (Cluster 2) that would otherwise compress all other clusters into an unreadable clump.
