# Predicting House Prices with Linear Regression

**Track:** Data Analytics — Level 2, Task 1
**Internship:** Oasis Infobyte SIP
**Repository:** [github.com/rneeraja080803/OIBSIP](https://github.com/rneeraja080803/OIBSIP)

## Objective
Build and evaluate a linear regression model that predicts house prices based on features such as area, number of rooms, and other property attributes. Develop end-to-end skills from data cleaning through to model interpretation.

## Dataset
**Housing Prices Dataset** (Kaggle, by M Yasser H) — 545 property records, 13 columns, no missing values. Features include area, bedrooms, bathrooms, stories, parking, and binary amenity flags (mainroad, guestroom, basement, hotwaterheating, airconditioning, prefarea) plus furnishing status.

## Tech Stack
Python, pandas, scikit-learn (LinearRegression, Ridge), matplotlib, seaborn, Jupyter Notebook

## Methodology
1. **EDA** — null check, descriptive statistics, price distribution histogram
2. **Feature selection discussion** — reasoning through which features plausibly predict price
3. **Encoding** — binary yes/no columns mapped to 1/0; `furnishingstatus` one-hot encoded (drop_first=True)
4. **Correlation heatmap** — identifying features most correlated with price
5. **Train/test split** (80/20)
6. **Linear Regression** model training
7. **Evaluation** — MSE, RMSE, R² score
8. **Actual vs. predicted** scatter plot
9. **Residual plot** — checking for random distribution of errors
10. **Coefficient analysis** — which features drive price up/down
11. **Bonus** — Ridge regression comparison

## Results

| Metric | Linear Regression | Ridge Regression |
|---|---|---|
| RMSE | ₹1,324,506.96 | ₹1,325,320.44 |
| R² Score | 0.6529 | 0.6525 |

## Key Findings
- `area`, `bathrooms`, and `airconditioning` show the strongest positive correlation with price.
- `bedrooms` correlates more weakly than expected — `area` captures living space more directly than room count.
- Ridge regression performs almost identically to plain Linear Regression here, since the feature set is small (13 features) with no severe multicollinearity — regularisation matters more on larger, messier feature sets.

## How to Run
```bash
pip install pandas scikit-learn matplotlib seaborn jupyter
jupyter notebook House_Price_Prediction.ipynb
```
