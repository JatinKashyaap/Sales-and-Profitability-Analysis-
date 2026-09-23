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

### PS-1: Which customers are driving growth in the 2021 ?

<img width="1465" height="1996" alt="customer-performance-report-page1" src="https://github.com/user-attachments/assets/fe81beab-f5d7-4c73-ae73-4b53bbe101da" />
<img width="1313" height="1252" alt="customer-performance-report-page2" src="https://github.com/user-attachments/assets/445e8a20-2bff-4e43-8cda-7fc0a3602940" />

- **Amazon** is the single largest account by a wide margin — **$82.1M** in FY2021, more than 4x the next largest customer
- **AtliQ Exclusive** ($61.1M) and **Atliq e Store** ($53.0M) — AtliQ's own retail/e‑commerce channels — together outsell every third‑party reseller except Amazon
- Every one of the 67 customer accounts grew year-over-year; the smallest jumps (Currys, Australia's Argos/Sainsbury's, Bangladesh's Pakistan-adjacent accounts) still grew 240%+

### PS-2: Are divisions performing evenly?

<p align="center">
  <img src="images/division-level-report.png" alt="Division level revenue report" width="600">
</p>

- **P&A**: $105.2M → $338.4M (**+221.5%**) — the largest division and the fastest-growing in absolute dollars
- **PC**: $40.1M → $165.8M (**+313.7%**) — smallest base, but the *highest* percentage growth of the three
- **N&S**: $51.4M → $94.7M (**+84.4%**) — consistently the slowest-growing division

### PS-3: Is every market hitting its FY2021 target?

<p align="center">
  <img src="images/market-performance-vs-target.png" alt="Market performance vs target by country, FY2021" width="650">
</p>

- **No.** All 23 markets finished **below target**, for an overall variance of **-9.2%**
- **India** ($161.3M) is both the largest market and the closest to target (**-5.9%**) — the best-run market at scale
- **Poland** posted the worst miss at **-18.1%**, followed by Canada (-14.5%) and Spain (-14.1%)
- The **USA**, the second-largest market ($87.8M), still missed target by **-11.7%**

### PS-4: How did the top 5 markets contribute overall?

<p align="center">
  <img src="images/top-5-countries-net-sales.png" alt="Top 5 countries by net sales, FY2021" width="500">
</p>

- India, USA, South Korea, Canada, and the UK together generated **$367.2M** — **61.3% of total FY2021 Net Sales** from just 5 of 23 markets
- This concentration means performance in these five markets alone will make or break any global target going forward

### PS-5: How are the products launched in 2021 performing?

<p align="center">
  <img src="images/new-products-2021-report.png" alt="New products launched in 2021 and their revenue" width="600">
</p>

- The 16 products launched in 2021 generated **$176.2M** in their first year — roughly **29% of total FY2021 Net Sales**
- **AQ Qwerty** ($22.0M), **AQ Trigger** ($20.7M), and **AQ Gen Y** ($19.5M) are the standout launches

### PS-6: Which existing products are growing fastest?

<p align="center">
  <img src="images/top-10-products-by-growth.png" alt="Top 10 products by percentage increase in net sales" width="650">
</p>

- **AQ Mx NB** grew **5,623.5%** (from ~$0.04M to $1.4M) and **AQ Smash 2** grew **2,489.5%** ($0.4M → $11.2M) — both off a very small FY2020 base, so the dollar growth (not just the %) is the more useful number here
- These 10 products together grew **708%**, from $6.4M to $52.0M combined

### PS-7: Which products sell in volume vs. sell for value?

<p align="center">
  <img src="images/top-bottom-5-products-by-quantity.png" alt="Top and bottom 5 products by quantity sold" width="600">
</p>

- The top 5 products by **quantity** (the "AQ Master"/"AQ Gamers" wired & wireless accessory lines) moved **19.0M units** combined — high-volume, lower-ticket items
- The bottom 5 by quantity moved only **~0.17M units** combined, yet this list includes **AQ Smash 2** — the same product that posted a 2,489% *revenue* increase in PS-6. It's a low-volume, high-value product, not an underperformer, and shouldn't be read as one from quantity alone

### PS-8: Is the revenue growth profitable?

<p align="center">
  <img src="images/gross-margin-by-market-2021.png" alt="Gross Margin percent by market, FY2021" width="650">
</p>

- Gross Margin % varies sharply by market: **New Zealand (48.2%)**, **Japan (46.5%)**, and the **UK (45.1%)** are the most profitable markets, while **Germany (26.2%)**, **Norway (29.5%)**, and **Austria (30.1%)** are the least
- **India — the single largest market by revenue — sits below the global average margin** (32.0% vs. 36.4% overall), meaning the market contributing the most dollars is also one of the least profitable per dollar
- Combined with the FY2019–FY2021 margin trend in the EDA section, this points to margin management, not just revenue growth, as the priority for FY2022

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
