# 📊 Plant Co. Performance Report 2024 – Power BI Dashboard

This Power BI project provides a high-level overview of **Plant Co.'s** sales performance in 2024. It highlights key performance indicators (KPIs), tracks sales trends, and allows stakeholders to explore profitability, customer segments, and underperforming regions interactively.

---

## 🖼️ Dashboard Preview

![Sales Performance Dashboard](./image.png)

---

## 🔍 Key Insights

- 📈 **Year-to-Date (YTD) Sales** and **Previous Year (PYTD)** tracking
- 🔁 **YTD vs PYTD Difference** visualized through bar and line charts
- 🌍 **Bottom 10 Countries by Sales Decline**
- 🧱 **Profitability Analysis** by **GP% (Gross Profit Percentage)**
- 🎯 **Product Type Segmentation** (Indoor, Outdoor, Landscape)

---

## 💡 Core DAX Measures

Here are the key DAX measures powering the dashboard:

```DAX
-- Total Sales YTD
Sales YTD = 
CALCULATE(
    SUM('Sales'[Amount]),
    DATESYTD('Date'[Date])
)

-- Total Sales PYTD (Previous Year-To-Date)
Sales PYTD = 
CALCULATE(
    [Sales YTD],
    SAMEPERIODLASTYEAR('Date'[Date])
)

-- YTD vs PYTD Difference
Sales YTD vs PYTD = 
[Sales YTD] - [Sales PYTD]

-- Gross Profit Percentage (GP%)
GP% = 
DIVIDE(
    SUM('Sales'[Gross Profit]),
    SUM('Sales'[Amount])
) * 100
