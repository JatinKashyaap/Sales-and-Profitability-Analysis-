# 🖥️ Sales and Financial Data Analysis  — AtliQ Hardwares

Sales & Finance analytics on three fiscal years (FY2019–FY2021) of transaction data for **AtliQ Hardwares**, a consumer hardware brand selling notebooks, storage, PCs, and accessories through resellers such as Amazon, Flipkart, BestBuy, Croma, and Walmart across 23 countries.

![Excel](https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?logo=microsoftexcel&logoColor=white)
![PivotTables](https://img.shields.io/badge/Analysis-PivotTables%20%7C%20Power%20Pivot-F4A81D)
![Domain](https://img.shields.io/badge/Domain-Consumer%20Goods-D6472B)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Table of Contents

* [Overview](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#overview)
* [Business Problem](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#business-problem)
* [Tools & Technologies](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#tools--technologies)
* [Project Structure](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#project-structure)
* [Exploratory Data Analysis (EDA)](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#exploratory-data-analysis-eda)
* [Problem Statements & Key Findings](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#problem-statements--key-findings)
* [How to Run This Project](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#how-to-run-this-project)
* [Final Recommendations](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#final-recommendations)
* [Author & Contact](https://github.com/JatinKashyaap/Insights-for-Consumer-Goods-Domain#author--contact)

---

## Overview

AtliQ Hardwares sells across three divisions — **P&A** (Peripherals & Accessories), **PC**, and **N&S** (Notebooks & Storage) — through roughly **67 reseller/customer accounts** in **23 countries**. This project consolidates three years of sales and finance data into a set of Excel PivotTable/PivotChart reports that answer a single question leadership kept asking in different forms: *"Where exactly is our growth coming from, and is it healthy?"*

The workbooks sit on top of a small star-schema data model (`fact_sales_monthly`, `fact_sales_monthly_with_cost`, `dim_customer`, `dim_date`, `dim_market`, `dim_product`, `ns_targets_2021`), which is what lets every report below be filtered live by **region**, **market**, **division**, or **customer**.

## Business Problem

Between FY2019 and FY2021, AtliQ Hardwares' Net Sales grew from **$87.5M to $598.9M — almost 7x**. That kind of growth raises questions a single "total revenue" number can't answer:

- Which **customers** and **markets** are actually driving the growth, and which are lagging?
- Did each market hit its **FY2021 sales target**, or is the growth masking widespread target misses?
- How are the **new products launched in 2021** performing?
- Is the revenue growth translating into healthy **profitability**, or is cost growth quietly eating into margins?
- Which products sell in **high volume** vs. **high value** — since these need different pricing, inventory, and marketing treatment?

This project answers each of these with a dedicated report, backed by the underlying Sales and Finance data models.

## Tools & Technologies

- **Microsoft Excel 2021** — PivotTables & PivotCharts, Power Pivot / Data Model, conditional formatting (data bars, colour scales) for at-a-glance reporting
- **Star-schema data model** — `dim_customer`, `dim_date`, `dim_market`, `dim_product` dimension tables joined to `fact_sales_monthly` / `fact_sales_monthly_with_cost`, plus an `ns_targets_2021` table for target-vs-actual comparisons

<img width="1917" height="1172" alt="Diagram Model" src="https://github.com/user-attachments/assets/c4cea6cb-0608-4493-b6ea-c2813b5e7ee2" />

- **Core measures**: Net Sales, Quantity Sold, Total COGS, Gross Margin, Gross Margin %
- **PDF export** — each report is published as a standalone, print-ready PDF for distribution outside Excel
- Report screenshots and the two trend charts in this README were rendered separately from the workbooks' figures for documentation purposes

## Project Structure

```
Insights-for-Consumer-Goods-Domain/
├── Sales_Analytics_Project_File.xlsx      # Customer, Market, Product & Division sales pivots (FY19–FY21)
├── Finance_Analytics_Project_File.xlsx    # P&L by Year / Month / Market, Gross Margin % by sub-zone
├── reports/                                # Standalone PDF exports of each report
│   ├── Customer_Performance_Report_.pdf
│   ├── Division_Level_Report.pdf
│   ├── Market_Performance_Report.pdf
│   ├── New_Products-2021_Report.pdf
│   ├── Top_10_Products_Reports.pdf
│   ├── Top_5_Countries_Net_Sales_Report.pdf
│   └── Top_and_Bottom_Products_by_Quantity.pdf
├── images/                                 # Report screenshots & charts used in this README
└── README.md
```

## Exploratory Data Analysis (EDA)

The underlying data spans **3 fiscal years**, **67 customer accounts**, **23 country markets**, and **3 product divisions**. Before drilling into individual reports, two patterns stood out immediately:

**1. Revenue tripled year-over-year, twice — but margin didn't come along for the ride.**

<p align="center">
  <img src="images/net-sales-vs-gross-margin-trend.png" alt="Net Sales growth vs Gross Margin % erosion, FY2019 to FY2021" width="650">
</p>

Net Sales grew 125% in FY2020 and a further 205% in FY2021, while Gross Margin % slipped from **41.4% → 37.3% → 36.4%** over the same period — a steady erosion rather than a one-off dip, which made profitability a first-class question for this analysis, not an afterthought.

**2. The P&A division, not PC, is the real growth engine.**

<p align="center">
  <img src="images/division-level-report.png" alt="Net Sales by Division, FY2020 vs FY2021" width="650">
</p>

P&A grew from $105.2M to $338.4M (+221.5%) and alone accounts for **56% of FY2021 revenue** — more than PC and N&S combined — which shaped which product lines get the most attention in the findings below.

With those two signals in hand, the detailed EDA moved customer-by-customer, market-by-market, and product-by-product using the reports below.

## Problem Statements & Key Findings

# AtliQ Sales & Finance Analytics — Problem Statements and Key Findings

## Data Sources
- Sales Analytics Project File.xlsx
- Finance Analytics Project File.xlsx

All monetary values are USD unless stated otherwise.

## 1. Top performing customers in 2021
**Problem:** Identify customers with the highest FY2021 net sales and compare FY2021 performance with FY2020.
**Solution:** Rank customers by FY2021 Net Sales and calculate FY2020→FY2021 growth.
**Key finding:** Amazon has the highest FY2021 net sales at $82.1M.
**Image:** `01_customers.png`

## 2. Markets able to meet 2021 targets
**Problem:** Determine which markets meet or exceed FY2021 targets.
**Solution:** Use the workbook's Performance vs Target percentage; >=0% means target met/exceeded.
**Key finding:** No market has a non-negative variance in the supplied report. Japan is closest to target at -4.1%; Poland has the largest shortfall at -18.1%.
**Image:** `02_market_targets.png`

## 3. Top 10 products by percentage increase in net sales
**Problem:** Rank the ten products with the largest FY2020→FY2021 net-sales increase.
**Solution:** `(2021 - 2020) / 2020 × 100`.
**Key finding:** AQ Mx NB has the highest increase at 5623.5%.
**Image:** `03_top_products_growth.png`

## 4. Top divisions by percentage increase in net sales
**Problem:** Compare division-level FY2020→FY2021 net-sales growth.
**Solution:** Apply the same percentage-growth formula to each division.
**Key finding:** PC has the highest reported increase at 313.7%.
**Image:** `04_divisions.png`

## 5. Top 5 and bottom 5 products by quantity sold
**Problem:** Identify the five highest-quantity and five lowest-quantity products.
**Solution:** Rank the quantity field descending and ascending.
**Key finding:** Highest = AQ Master wired x1 Ms, 4,151,008 units. Lowest in the bottom-five report = AQ HOME Allin1 Gen 2, 8,854 units.
**Image:** `05_quantity_extremes.png`

## 6. New products sold in 2021
**Problem:** Identify products with no FY2020 sales and FY2021 sales.
**Solution:** Select blank FY2020 rows with FY2021 sales.
**Key finding:** 16 new products are listed, generating $176.2M; the largest contributor is AQ Qwerty at $22.0M.
**Image:** `06_new_products.png`

## 7. Top 5 countries by net sales in 2021
**Problem:** Rank countries by FY2021 net sales.
**Solution:** Sort FY2021 country sales descending.
**Key finding:** India is highest among the five at $161.3M; the five-country total is $367.2M.
**Image:** `07_top_countries.png`

## 8. Overall P&L for all fiscal years
**Problem:** Analyze Net Sales, Total COGS, Gross Margin and Gross Margin % for FY2019–FY2021.
**Solution:** Use the annual P&L report.
**Key finding:** FY2021 Net Sales = $598.9M; Gross Margin = $218.2M; Gross Margin % = 36.43%.
**Image:** `08_pl_year.png`

## 9. Overall P&L for all fiscal months and quarters
**Problem:** Analyze monthly and quarterly P&L across fiscal years.
**Solution:** Q1=Sep–Nov, Q2=Dec–Feb, Q3=Mar–May, Q4=Jun–Aug.
**Key finding:** FY2021 peak monthly Net Sales occur in Dec, at $78.1M.
**Image:** `09_pl_months_quarters.png`

## 10. Overall P&L for markets for FY2021
**Problem:** Compare market-level Net Sales, Total COGS, Gross Margin and Gross Margin %.
**Solution:** Rank markets by Net Sales and review profitability metrics.
**Key finding:** India is the largest FY2021 market at $161.3M in net sales.
**Image:** `10_pl_markets_2021.png`

## 11. Gross Margin % by Subzone based on quarters for all fiscal years
**Problem:** Compare GM% across Q1–Q4 for each subzone across FY2019–FY2021.
**Solution:** Use the workbook's GM% by Subzone pivot tables.
**Key finding:** FY2021 overall GM% is 36.43%; the image provides quarter-by-quarter subzone GM% and the overall annual trend.
**Image:** `11_gm_subzone.png`

## Calculation Notes
1. Percentage increase = `(2021 - 2020) / 2020 × 100`.
2. The workbook's `21 vs 20` field is a ratio; 5.41 means FY2021 is 5.41× FY2020, equivalent to a 441% increase.
3. Market target variance is taken directly from the workbook's `%` field.
4. Fiscal quarters follow the workbook calendar: Q1 Sep–Nov, Q2 Dec–Feb, Q3 Mar–May, Q4 Jun–Aug.
5. New products are products with no FY2020 sales and FY2021 sales in the supplied report.


## How to Run This Project

1. **Clone or download** this repository.
2. **Open the workbooks** in Excel 2016 or later (Power Pivot / Data Model support required): `Sales_Analytics_Project_File.xlsx` and `Finance_Analytics_Project_File.xlsx`.
3. If the workbooks are connected to a live data source, refresh the model via **Data → Refresh All** before analysing; otherwise the pivot tables already hold the cached FY2019–FY2021 figures used throughout this README.
4. Use the **region / market / division / customer** filter cells at the top of each report tab to slice the view — every PivotTable in these workbooks responds to the same filters.
5. For a quick look without opening Excel, browse the pre-exported pages in **`/reports`** — these are the PDFs the screenshots above were taken from.

## Final Recommendations

1. **Protect margin while scaling.** Gross Margin % fell from 41.4% to 36.4% even as revenue grew ~6.8x. Prioritise cost renegotiation or pricing review in the lowest-margin markets first: Germany (26.2%), Norway (29.5%), Austria/Italy (~30%).
2. **Treat India as a volume-margin trade-off, not just a growth story.** It's the top revenue market but sits below average margin (32.0%) — worth testing premium SKUs or bundle pricing there rather than pure volume expansion.
3. **Reset FY2022 targets using India's performance as the benchmark.** Every market missed its FY2021 target, but India's -5.9% miss was far closer than Poland's -18.1% or Canada's -14.5% — the target-setting model likely needs market-specific recalibration, not a single global growth assumption.
4. **Keep investing in the FY2021 launches that are already working** — AQ Qwerty, AQ Trigger, and AQ Gen Y contributed disproportionately to the $176.2M in new-product revenue.
5. **Don't mistake low quantity for low performance.** AQ Smash 2 sells in small volumes but grew revenue nearly 25x — treat it as a high-value, low-volume line rather than folding it into the same strategy as high-volume accessories.
6. **Sanity-check the highest % growth products against their base.** AQ Mx NB and the AQ LION series show four-digit percentage growth off a very small FY2020 base — confirm this reflects durable demand before scaling supply or marketing spend around those numbers.

## Author & Contact

**Jatin Kashyap**
GitHub: [@JatinKashyaap](https://github.com/JatinKashyaap)

Feel free to open an issue on this repository for questions or suggestions about the analysis.
