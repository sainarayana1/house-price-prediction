# House Price Prediction

Regression model that predicts house prices from property features (area, rooms, amenities, furnishing status) and identifies which features influence price the most. Built as a Week 1 internship project.

## Problem Statement

Real estate buyers and sellers often rely on guesswork or outdated comparisons to estimate a property's fair value. This project builds a regression model that predicts house prices based on property features, then identifies which features most strongly influence price.

## Dataset

[Housing Prices Dataset](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset) (Kaggle, by yasserh) — 545 properties, 13 columns.

| Column | Description |
|---|---|
| `price` | Sale price in INR (target variable) |
| `area` | Plot area in sq. ft. |
| `bedrooms`, `bathrooms`, `stories`, `parking` | Counts |
| `mainroad`, `guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `prefarea` | Yes/No amenity or location flags |
| `furnishingstatus` | furnished / semi-furnished / unfurnished |

## Approach

1. **Data Loading & Exploration** — loaded the CSV, checked shape, identified target vs. features, checked for missing values.
2. **Data Cleaning** — verified no missing values or duplicates; converted yes/no columns to 0/1; one-hot encoded `furnishingstatus`.
3. **Model Building** — 80/20 train-test split; trained Linear Regression and Random Forest Regressor; evaluated with MAE, RMSE, R².
4. **Visualization** — price distribution histogram, correlation heatmap, actual-vs-predicted scatter plot.
5. **Insights** — identified top price drivers and wrote up findings.

## Results

| Model | MAE (INR) | RMSE (INR) | R² Score |
|---|---|---|---|
| Linear Regression | 9,70,043 | 13,24,507 | 0.653 |
| Random Forest | 10,14,947 | 13,99,769 | 0.612 |

Linear Regression performed marginally better than Random Forest on this dataset — a reminder that more complex models don't automatically win, especially on a dataset of this size (545 rows) where price is driven largely by a few strongly linear relationships.

## Key Insights

- **Area** is by far the strongest price driver, followed by **bathrooms**, **air conditioning**, and **stories**.
- Bedroom count matters less than typically assumed — bathrooms and air conditioning have a stronger relationship with price.
- The model explains ~65% of price variation (R² = 0.653), with predictions typically within ₹9.7 lakh of the actual price — good for ballpark estimates, not precise individual valuations.
- **Recommendation:** real estate listings should be priced and marketed around livable area and bathroom count, with air conditioning and preferred-area location highlighted as value-adding features.

## Repository Structure

```
.
├── analysis.ipynb       # Full notebook: all 5 tasks, executed with outputs
├── Housing.csv          # Dataset
├── report.docx          # Detailed project report
├── summary.docx         # 1-page summary of findings
└── charts/
    ├── chart1_price_distribution.png
    ├── chart2_correlation_heatmap.png
    └── chart3_actual_vs_predicted.png
```

## Tools & Libraries

Python 3 · Jupyter Notebook · Pandas · Scikit-learn · Matplotlib · Seaborn

## How to Run

```bash
pip install jupyter pandas numpy matplotlib seaborn scikit-learn
jupyter notebook analysis.ipynb
```

Run all cells (Kernel → Restart & Run All) to reproduce the results above.
