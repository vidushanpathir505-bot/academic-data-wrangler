# 🚲 Sales Data Analysis

A pandas-based exploratory data analysis (EDA) project examining ~112,000 bike and accessory sales transactions to uncover revenue drivers, profitability patterns, and customer behavior trends.

## 📌 Overview

This project walks through a full data analysis workflow — from raw data cleaning to business-focused insights — using a real-world sales dataset covering **2011–2016** across six countries. The goal was to answer practical business questions: *which products drive revenue, which are most profitable, and who is buying?*

## 🗂️ Dataset

- **113,036** raw transaction records, **18** columns
- Fields include `Date`, `Customer_Age`, `Age_Group`, `Customer_Gender`, `Country`, `State`, `Product_Category`, `Sub_Category`, `Product`, `Order_Quantity`, `Unit_Cost`, `Unit_Price`, `Cost`, `Revenue`, `Profit`
- 3 product categories (**Bikes, Accessories, Clothing**) across 17 sub-categories and 130 unique products

## 🧹 Data Cleaning

- Removed **1,000 exact duplicate rows** (0.88% of data)
- Converted `Date` from string to `datetime64` and verified zero parsing failures
- Verified `Profit = Revenue - Cost` held true for every row (no calculation errors)
- Checked all numerical columns for impossible values (negatives, zero, outliers) and all categorical columns for inconsistent labels
- Final cleaned dataset: **112,036 rows**

## ⚙️ Feature Engineering

- `Profit_margin` — profit as a percentage of revenue, per transaction
- `Day_of_week` — extracted from `Date` for weekday-level analysis

## 📊 Analysis Performed

Using `groupby()`, `agg()`, and `sort_values()`:

- Revenue and quantity sold by product
- Revenue, quantity, and profit by category and sub-category
- Profitability analysis — total profit vs. average profit margin by product
- Time-based analysis — revenue by year, month, and day of week
- Customer analysis — revenue by age group, gender, and country

## 📈 Visualizations

| Chart | Type |
|---|---|
| Revenue by Product Category | Bar chart |
| Profit by Product Category | Bar chart |
| Monthly Revenue Trend (2011–2016) | Line chart |
| Top 10 Countries by Revenue | Bar chart |
| Top 10 Products by Profit Margin | Horizontal bar chart |

## 💡 Key Insights

1. **Bikes dominate revenue, not volume.** Bikes generated 72.4% of revenue ($61.4M) from just 2.7% of units sold, while Accessories sold 78% of all units for only 17.7% of revenue — a low-volume/high-value vs. high-volume/low-value split that should shape inventory and marketing strategy differently per category.

2. **Accessories are the most profit-efficient category.** Accessories convert revenue to profit at a 58.6% margin, nearly double Bikes (33.2%) and Clothing (33.9%) — despite generating far less total revenue. Bike sales still produce the most total profit dollars purely on scale.

3. **Revenue leaders and profit leaders aren't the same products.** `Road-150 Red, 62` tops revenue ($3.81M), but `Mountain-200 Black, 38` generates more total profit ($1.30M) on less revenue. The `Sport-100 Helmet` line posts ~58–59% margins despite modest revenue — margin and scale are separate stories worth tracking independently.

4. **Revenue grew steadily through 2015, then dipped in 2016.** From $8.95M (2011) to a peak of $19.9M (2015), followed by an 11.6% drop to $17.6M (2016) — worth confirming whether 2016 reflects a genuine decline or an incomplete year of data before treating it as a warning sign.

5. **December and June are peak months; July/August are the slow season.** Peak months outperform the July/August low by roughly 37%, a seasonal pattern relevant for inventory timing and promotional planning.

6. **Adults 35–64 are the core customer base.** This segment drives 50.7% of revenue, while Seniors (64+) contribute just 0.4% — a segment that's either a small addressable market or an under-reached one.

7. **The business is geographically concentrated.** The US and Australia together account for 58% of total revenue, while gender split is close to even (50.8% male / 49.2% female) — geography, not gender, is the more meaningful driver of variation here.

## 🛠️ Tools Used

- Python
- pandas
- matplotlib
- Jupyter Notebook

## 📁 Project Structure

```
sales-analysis/
├── data/
│   └── sales_data.csv
├── sales_analysis.ipynb
└── README.md
```

## 🚀 How to Run

```bash
git clone https://github.com/vidushan-ds/sales-analysis.git
cd sales-analysis
pip install pandas matplotlib jupyter
jupyter notebook sales_analysis.ipynb
```

## 👤 Author

**Vidushan Pathirana**