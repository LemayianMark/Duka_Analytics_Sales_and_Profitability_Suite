# Duka_Analytics_Sales_and_Profitability_Suite
Power BI suite analyzing Ksh 6.68M in retail revenue across six Kenyan store locations, with margin diagnostics, customer segmentation, and YoY performance tracking.


# Duka Analytics: Retail Sales, Profitability & Customer Insights Dashboard

## Problem

Duka Analytics — a multi-category retailer operating across six Kenyan towns — had sales data scattered across categories, stores, and payment channels with no unified view of performance. Leadership could see revenue was flowing in, but had no clear read on **which categories were actually profitable**, **which stores were underperforming**, or **who their most valuable customers were**.

## The goal:

Build a Power BI reporting suite that moves beyond raw revenue tracking — surfacing margin health by category and location, quantifying customer value by segment (Retail vs. Wholesale), and giving leadership a page-by-page narrative from "how are we doing" down to "what to do about it."

## Approach

1. **Data modeling** — Built a star-schema model with a central Sales fact table connected to Product, Store, Customer, and a dedicated Date dimension marked for time intelligence.
2. **Power BI — DAX measure layer** — Built out Total Sales, Total Gross Profit, Gross Margin %, YoY Growth %, Average Order Value, and ranking measures (RANKX-based) to drive Top/Bottom performer views.
3. **Dashboard — a 4-page story** — Structured to walk a reader from the big picture down to actionable detail, rather than one crowded page.

---

## 📌 Executive Summary

Duka Analytics processes **Ksh 6.68M** in total revenue across **832 orders** from **40 distinct customers**, spanning five product categories and six store locations. This suite tracks sales performance, profitability by category and location, and customer value to support both regional and category-level decision-making.

![Executive Summary](Dashboard_Images/Customer_Insights)

---

## 💡 Key Business Findings

* **Margin Leader vs. Laggard**: **Electronics** delivers the strongest gross margin performance, while **Stationery** trails as the lowest-margin category — a **~1.5 percentage point** spread worth closing.
* **Overall Profitability**: The business runs a blended **Gross Margin of 22.82%** on **Ksh 1.52M** in gross profit.
* **Revenue Concentration**: **Electronics** anchors the business at **Ksh 3.4M (≈51% share)** of total revenue, more than 5x the next-largest category (Groceries, Ksh 2.1M).
* **Customer Mix**: **Wholesale** customers drive **57.95% (Ksh 1.96M)** of revenue vs. **42.05% (Ksh 1.43M)** from Retail — despite Wholesale being a smaller customer count, it's the heavier revenue engine.
* **Regional Margin Spread**: Gross margin by store ranges from **23.89% in Nairobi** down to **22.42% in Nakuru**, pointing to store-level cost or pricing inconsistencies worth investigating.
* **Payment Channel**: **M-Pesa** dominates transaction volume at **62.7% (Ksh 2.13M)** of revenue, ahead of Cash (23.99%) and Card (13.32%).

---

## 🎯 Strategic Recommendations

| Objective | Target Group / Segment | Tactical Action Plan | Projected Impact |
| :--- | :--- | :--- | :--- |
| **1. Close the Margin Gap** | Stationery category | Audit supplier pricing and shrinkage on low-margin SKUs (e.g. Notebook A4, School Exercise Books); renegotiate cost price or reposition as basket-fillers rather than margin drivers. | Lifts blended margin toward the Electronics benchmark (23%+). |
| **2. Regional Margin Standardization** | Nakuru & Machakos stores | Review local pricing and discounting practices against Nairobi's higher-margin baseline. | Recovers margin points across the two lowest-performing stores. |
| **3. Wholesale Growth** | Wholesale customer segment | Expand account-based outreach given Wholesale's outsized revenue share relative to Retail. | Compounds revenue growth from an already high-yield segment. |
| **4. Channel Optimization** | M-Pesa & Card users | Streamline M-Pesa checkout further given its dominant share; test incentives to grow Card adoption for larger basket sizes. | Improves conversion and basket value across payment channels. |

---

## 🛠️ Dashboard Architecture

| Dashboard Page | Purpose & Core Insights |
| :--- | :--- |
| **1. Executive Summary** | Total Revenue, Gross Profit, Gross Margin %, and Revenue Growth YoY %, with a monthly trend vs. prior year/target, and revenue by payment method and store location. |
| **2. Sales Performance** | Average Order Value, Quantity Sold, and category-level revenue trend, plus a top-10 product ranking table and a payment method × store location matrix. |
| **3. Profitability Summary** | Gross Profit and Margin % by category, revenue-to-profit waterfall, a revenue/margin/quantity bubble chart, and monthly margin trend. |
| **4. Customer Insights** | Distinct Customers, Total Orders, and Transactions per Customer, with revenue share by customer type (Wholesale vs. Retail), sales by day of week, and basket spend by location. |

---

## 🧮 Advanced DAX Features

The report uses time-intelligence and ranking measures to power YoY comparisons and Top/Bottom performer views:

```dax
Sales PY = 
CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))

YoY Sales Growth % = 
DIVIDE([Total Sales] - [Sales PY], [Sales PY])

Overall Gross Margin % = 
DIVIDE([Total Gross Profit], [Total Sales])

Margin Rank = 
RANKX(ALL('Product'[ProductName]), [Overall Gross Margin %], , DESC)
```

---

## 📸 Dashboard Gallery

### Page 1: Executive Summary
![Executive_Summary](Dashboard_Images/Executive_Summary.png)

### Page 2: Sales Performance
![Sales_Performance](Dashboard_Images/Sales_Performance.png)

### Page 3: Profitability Summary
![Profitability_Summary](DashboardImages/Profitability_Summary.png)

### Page 4: Customer Insights
![Customer_Insights](Dashboard_Images/Customer_Insights.png)

---

## 🛠️ Tech Stack & Skills

* **Power BI Desktop**: Data Modeling, Dashboard UX Design, Custom Visual Layouts, Conditional Formatting.
* **DAX (Data Analysis Expressions)**: Time Intelligence (SAMEPERIODLASTYEAR), Ranking (RANKX), Margin & Growth Measures.
* **Data Architecture**: Star Schema (Sales fact table with Product, Store, Customer, and Date dimensions).

---

## 📐 Data Model (Star Schema)

The report runs on a Star Schema with a central `Sales` fact table connected to `Product`, `Store`, `Customer`, and `Date` dimension tables. The `Date` table is marked as the official date table to support time-intelligence functions (YoY growth, prior-period comparisons).

