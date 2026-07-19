# Olist Business Intelligence Dashboard
Power BI project analyzing the Olist e-commerce dataset with executive, operations, and customer insights, supported by a star schema data model.

---

## Executive View
![Executive Dashboard](https://github.com/AdamLumbley/olist-business-intelligence-dashboard/blob/main/olist-executive-dashboard.png)

---

## Operations Overview
![Operations Dashboard](https://github.com/AdamLumbley/olist-business-intelligence-dashboard/blob/main/olist-operations-overview.png)

---

## Customer Insights
![Customer Insights](https://github.com/AdamLumbley/olist-business-intelligence-dashboard/blob/main/olist-customer-insights.png)

---

## Overview
This project analyzes Olist e-commerce operations using a structured Power BI data model. The goal was to practice the full BI workflow — designing a data model, cleaning multi-source data, and building KPIs that answer real business questions about revenue, delivery performance, and customer satisfaction.

- Built in Power BI
- Star schema data model
- ETL performed in Power Query

---

## Business Questions
1. What drives revenue across regions and product categories?
2. How do delivery times impact customer satisfaction?
3. Which segments contribute most to profitability and volume?
4. What patterns exist in customer review behavior?
5. How efficient are operational processes at scale?

---

## Data Model (Star Schema)
![Data Model](https://github.com/AdamLumbley/olist-business-intelligence-dashboard/blob/main/olist-star-schema.png)

The model follows a star schema design centered around the Orders fact table. Dimension tables include customers, sellers, products, payments, and geolocation. A dedicated date dimension enables time intelligence calculations, and a controlled snowflake extension supports hierarchical geographic analysis.

1. Designed a 9-table star schema with a controlled snowflake extension for hierarchical analysis.
2. Built and integrated a dedicated date dimension table to enable time-based analysis (trends, seasonality).
3. Established 1:many relationships with single-direction filtering from dimension tables into the fact table for consistent filtering behavior.

---

## ETL & Data Preparation
1. Developed ETL pipelines in Power Query to transform raw CSV datasets into an analytical model.
2. Performed data integrity correction across 60K records using an outer left join in Power Query to reconcile mismatched records across tables.
3. Standardized and cleaned multi-source datasets prior to modeling.

---

## KPI Layer (DAX Measures)
I designed which KPIs the business questions above required, then used AI (Claude/Gemini) to help write the DAX syntax to implement them. I'm self-taught and still building fluency with DAX beyond core aggregation functions (SUM, COUNTROWS, DIVIDE) — using AI here is part of how I'm learning the language, not a replacement for understanding what each measure needs to calculate and why.

| KPI Category | Measure | Purpose |
| :--- | :--- | :--- |
| **Financials** | `Total Realized Revenue` | Aggregates payments specifically for 'Delivered' orders. |
| **Growth** | `MoM Realized Rev Change %` | Calculates month-over-month revenue growth. |
| **Logistics** | `Avg Delivery Days` | Calculates the duration from order placement to customer delivery. |
| **Efficiency** | `Delayed Orders %` | Identifies the ratio of orders exceeding the estimated delivery date. |
| **Quality** | `1-Star Review Rate` | Tracks negative sentiment trends against total review volume. |

### Sample: Delayed Orders %
```dax
Delayed Orders % =
VAR TotalDelivered = CALCULATE(COUNTROWS(Orders), Orders[Order Status] = "delivered")
VAR TotalDelayed = CALCULATE(
    COUNTROWS(Orders),
    Orders[Order Status] = "delivered" &&
    Orders[Order Delivered Customer Date] > Orders[Estimated Delivery Date]
)
RETURN
DIVIDE(TotalDelayed, TotalDelivered, 0)
```

---

## Tech Stack
Power BI · Power Query (ETL) · DAX (AI-assisted) · Data Modeling (Star Schema)

---

## Key Insights
1. Average dispatch time is 3.21 days, while average total delivery time is 12.50 days — indicating most delay happens during courier transit rather than internal order processing.
2. Customer review scores improved from 3.54 (2016) to 4.09 (2017) and then stabilized through 2018, alongside a drop in average delivery time from ~55 days in early 2016 to ~12.5 days later in the dataset.
3. Taken together, the dashboards show operational performance improving over the observed period, driven largely by faster delivery cycles and better customer satisfaction metrics.
