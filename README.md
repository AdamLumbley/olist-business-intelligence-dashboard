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

## Data Model (Star Schema)
![Data Model](https://github.com/AdamLumbley/olist-business-intelligence-dashboard/blob/main/olist-star-schema.png)

## The model follows a star schema design centered around the Orders fact table.
Dimension tables include: customers, sellers, products, payments, and geolocation. 
A dedicated date dimesion enables time intelligence calculations. 
A controlled snowflake extension supports hiearchiacal geographic analysis.
---

## Overview
This project analyzes Olist e-commerce operations using a structured Power BI data model. The goal is to evaluate revenue performance, delivery efficiency, and customer satisfaction through a star-schema-based analytical layer.

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

## Data Model & Architecture

1. Designed a 9-table star schema data model with a controlled snowflake extension for hierarchical analysis.
2. Built and integrated a dedicated date dimension table enabling time-based analysis (trends, seasonality).
3. Established referential integrity across fact and dimension tables for consistent filtering behavior.

## ETL & Data Preparation

1. Developed ETL pipelines in Power Query to transform raw CSV datasets into an analytical model.
2. Performed data integrity correction across 60K records using SQL-style join (OUTER LEFT JOIN) reconciliation logic.
3. Standardized and cleaned multi-source datasets prior to modeling.

## KPI Layer (DAX Measures)

1. Revenue (Delivered Orders Only)
2. Delivery Delay Rate
3. Average Delivery Time
4. 1-Star Review Rate

## Tech Stack

Power BI
Power Query (ETL)
DAX
SQL (data exploration / transformation)
Data modeling (Star Schema)


## Key Insights

1. Average dispatch time is 3.21 days, while average total delivery time is 12.50 days, indicating that the majority of delay occurs during courier transit rather than internal order processing.
2. Customer review scores improved from 3.54 (2016) to 4.09 (2017) and then stabilized through 2018. This improvement aligns with a significant reduction in delivery times during the same period, from approximately 55 days in early 2016 to ~12.5 days on average later in the dataset.
3. The combined dashboards indicate overall improvement in operational performance across the observed time period, particularly driven by faster delivery cycles and improved customer satisfaction metrics.
