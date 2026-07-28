# EDA on Retail Sales Data

**Track:** Data Analytics — Level 1, Task 1
**Internship:** Oasis Infobyte SIP
**Repository:** [github.com/rneeraja080803/OIBSIP](https://github.com/rneeraja080803/OIBSIP)

📄 For full task documentation, see [DOCUMENTATION.md](./DOCUMENTATION.md) in this folder.

## Objective
Perform a thorough Exploratory Data Analysis on a retail sales dataset to uncover patterns, customer behaviour trends, and actionable business insights.

## Dataset
**Sample Superstore Dataset** (Kaggle) — 9,994 orders across 2014–2017, covering order/ship dates, customer segment, region, product category/sub-category, sales, quantity, discount, and profit.

> **⚠️ Note on the "Customer Demographics" checklist item:** This dataset does not contain individual customer age or gender fields (it is transaction/order-level data, not user-profile data). Rather than fabricate synthetic demographic fields onto real transaction records, I substituted the closest genuine demographic-style breakdowns available in the dataset — **Customer Segment** (Consumer / Corporate / Home Office) and **Region** — and documented this substitution explicitly in the notebook (Section 4). This follows the task's self-sourcing guideline, which permits any suitable retail/e-commerce sales dataset; the Superstore dataset is the most widely used dataset of this type precisely because it's transaction-level rather than customer-profile-level.

## Tech Stack
Python, pandas, matplotlib, seaborn, Jupyter Notebook

## What's Inside
`EDA Retail Sales.ipynb` covers:
1. Initial inspection (shape, dtypes, nulls, duplicates)
2. Descriptive statistics (mean, median, mode, std)
3. Time series analysis — monthly and quarterly sales trends
4. Customer segment / regional breakdown (substituting for age/gender, which this dataset does not contain)
5. Product analysis — top 10 best-selling products, revenue by category
6. Correlation heatmap (Sales, Quantity, Discount, Profit)
7. Additional insight — profitability by sub-category + discount-vs-profit scatter plot
8. Written observations after every chart
9. Conclusion — 3 actionable business recommendations

## Key Findings
- Sales are heavily right-skewed; a small number of large orders drive the average up.
- Q4 is consistently the strongest sales quarter every year — clear seasonality.
- Discount is negatively correlated with profit; orders discounted above ~30% tend to be unprofitable.
- **Tables** and **Bookcases** sub-categories are net loss-making despite healthy category-level revenue — this only surfaces at the sub-category level.

## How to Run
```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook EDA Retail Sales.ipynb
```

## Note on Data
`Order Date` / `Ship Date` in the raw CSV use mixed date formats (e.g. `11-08-2016` and `4/15/2017`), so parsing uses `pd.to_datetime(..., format='mixed', dayfirst=True)` rather than a single fixed format.
